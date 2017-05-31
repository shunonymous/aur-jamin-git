# Maintainer: Shun Terabayashi <shunonymous@gmail.com>
pkgname=jamin-git
_version=0.98.9
pkgver=0.98.9.r12.199091a
pkgrel=2
epoch=
pkgdesc="A JACK Audio Connection Kit Audio Mastering Interface"
arch=('i686' 'x86_64')
url="http://jamin.sourceforge.net/en/about.html"
license=('GPLv2')
depends=('jack' 'fftw' 'libxml2' 'gtk3' 'swh-plugins' 'liblo')
makedepends=('git' 'intltool')
provides=('jamin')
conflicts=('jamin' 'jamin-cvs')
options=('!libtool')
install=${pkgname}.install
source=('jamin-git::git+https://git.code.sf.net/p/jamin/code')
md5sums=('SKIP')

pkgver() {
  cd "$pkgname"

  printf "$_version.r%s.%s" "$(git rev-list --count HEAD)" "$(git rev-parse --short HEAD)"
}

build() {
  cd "$pkgname"

  LDFLAGS="-ldl"
  ./autogen.sh --prefix=/usr --libdir=/usr/lib
  make
}

package() {
  cd "$pkgname"

  make DESTDIR="$pkgdir/" install
}

# vim:set ts=2 sw=2 et:
