# Maintainer: pavbaranov <pavbaranov@gmail.com> 
#for this version based on the original version make for Arch Linux by:
# Maintainer: Felix Yan <felixonmars@archlinux.org>
# Maintainer: Antonio Rojas <arojas@archlinux.org>
# Contributor: Andrea Scarpino <andrea@archlinux.org>

pkgname=kwin
pkgver=5.12.1
pkgrel=1.1
pkgdesc='An easy to use, but flexible, composited Window Manager'
arch=(x86_64)
url='https://www.kde.org/workspaces/plasmadesktop/'
license=(LGPL)
depends=(kscreenlocker xcb-util-cursor plasma-framework kcmutils breeze kinit qt5-sensors)
makedepends=(extra-cmake-modules qt5-tools kdoctools python qt5-virtualkeyboard)
optdepends=('qt5-virtualkeyboard: virtual keyboard support for kwin-wayland')
groups=(plasma)
source=("https://download.kde.org/stable/plasma/$pkgver/$pkgname-$pkgver.tar.xz"{,.sig}
D9848.patch::"https://phabricator.kde.org/file/data/ct7mrqfbvghur3776sfd/PHID-FILE-3kj2g3lmgjhbawdt4xvk/D9848.diff")
sha256sums=('de5513fe9d13c7e17dc32f767699f8c7ce656a3eb3fb1dda22665a0b3dc48d8f'
            'SKIP'
            'bf2a8d0a34e4079f11f83de611f3d547265888532215e6fd229f3cc12f3b97c3')
validpgpkeys=('2D1D5B0588357787DE9EE225EC94D18F7F05997E'  # Jonathan Riddell
              '348C8651206633FD983A8FC4DEACEA00075E1D76'  # KDE Neon
              'D07BD8662C56CB291B316EB2F5675605C74E02CF'  # David Edmundson
              '1FA881591C26B276D7A5518EEAAF29B42A678C20') # Marco Martin <notmart@gmail.com>

prepare() {
  mkdir -p build
  
  cd $pkgname-$pkgver

  msg "Phabricator D9848 ("new blur") patch"
     patch -p1 -i ../D9848.patch
}

build() {
  cd build
  cmake ../$pkgname-$pkgver \
    -DCMAKE_BUILD_TYPE=Release \
    -DCMAKE_INSTALL_PREFIX=/usr \
    -DCMAKE_INSTALL_LIBDIR=lib \
    -DCMAKE_INSTALL_LIBEXECDIR=lib \
    -DBUILD_TESTING=OFF
  make
}

package() {
  cd build
  make DESTDIR="$pkgdir" install
}
