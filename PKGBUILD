# Maintainer: Janek Thomaschewski <janek@jbbr.net>

pkgname=signal-desktop-bin
pkgver=1.11.0
pkgrel=1
pkgdesc='Private messaging from your desktop'
arch=('x86_64')
url='https://github.com/signalapp/Signal-Desktop'
license=('GPL3')
provides=('signal-desktop')
conflicts=('signal')
options=(!strip)
depends=('gconf' 'gtk2' 'libnotify' 'libxtst' 'nss' 'xdg-utils' 'libxss')

sha512sums=('776f3e75ef304af5da72cc6e67b3cf541183bc461cffa38e575a4f9019a088553983c2ed7b5381de85f68f2228cc3505384337e6cf621019ef0cd3f83b60aeac'
            '7db7ee79a07fb86fec471e63c5189d61e8a2ca8fc2e659ea89ef22516e24e0a3c9f32c93f8ee520f56abc187b9b9304355e8aadb427c4920cda4f663ab1489fa')
source=("https://updates.signal.org/desktop/apt/pool/main/s/signal-desktop/signal-desktop_${pkgver}_amd64.deb"
        'signal-desktop')

package() {
  # extract package data
  tar xf data.tar.xz -C "${pkgdir}"

  # fix permissions in 1.9.0+ (Some directories have now 775; changing them back to 755)
  find "${pkgdir}" -type d -not -perm 755 -exec chmod 755 {} \;

  # install alias in /usr/bin
  mkdir "${pkgdir}/usr/bin"
  install -D -m755 signal-desktop "${pkgdir}/usr/bin/signal-desktop"
}
