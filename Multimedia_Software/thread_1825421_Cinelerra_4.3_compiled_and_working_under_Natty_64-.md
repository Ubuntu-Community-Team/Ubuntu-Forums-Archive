---
title: "Cinelerra 4.3 compiled and working under Natty 64-bit!"
date: 2011-08-15
forum: Multimedia Software
---

### Post by yodermk on 2011-08-15
I know Cinelerra is a bear to get working, so I thought I'd report that I did it.  4.2 did not work because it requires Video4Linux 1, which was removed in a recent kernel.  4.3 came out on the 5th of this month, so I thought I'd give it a try.

I only had to install two new packages -- the other requirements were already installed from previous attempts.  I installed libxv-dev to get the compile to finish.  After the compile, the 'bin/cinelerra' binary mysteriously did not exist, even though I saw no errors in the make.  Looking at the makefile, I saw it use the command 'make -C cinelerra'.  I tried that manually, and saw a complaint about libbz2.  So I installed libbz2-dev, tried it again, and it worked!  The author(s) really need to do a better job of getting their configure scripts to correctly identify all dependencies.

With all the dependencies, a simple configure and make does the trick.

I wish I had an apt-get command with a list of necessary packages that I could paste into this message for anyone to copy/paste, but I had tried several times before so all the deps except the two above were already installed.  Compiling a list would require reinstalling my OS and working it out from scratch, something I'm not inclined to do at the moment.  I've seen package lists before in these forums, but they are pretty old and probably need editing for recent versions.

If anyone else wants to give it a go, maybe we can compile another package list in this thread.

---

### Post by BicyclerBoy on 2011-08-15
You can get the dependencies & required actions from:

apt-get -s build-dep cinelerra

The -s option makes this a dummy simulation run..no sudo needed..

Info about v4linux1 removal..
[http://www.kernellabs.com/blog/?cat=66](http://www.kernellabs.com/blog/?cat=66)

---

### Post by handy on 2011-08-15
Following is the PKGBUILD for the Arch 64bit install (which installs without problems for me), it may be of use re. identifying the dependencies:

```
pkgname=cinelerra-heroine
pkgver=4.3
pkgrel=1
pkgdesc="Cinelerra from the HeroineWarrior.com (64-bit)"
arch=('x86_64')
url="http://www.heroinewarrior.com/cinelerra.php"
license=('GPL')
depends=('libpng' 'freeglut' 'libxv' 'termcap' 'libva')
makedepends=('yasm' 'nasm' 'libtool')
conflicts=('cinelerra-cv')
source=(https://sourceforge.net/projects/heroines/files/cinelerra-$pkgver-src.tar.bz2
	quicktime.patch)
md5sums=('42def96800668fa4a029bd1a982a4648'
	 'c555059768637c1456b71a36748ed81b')
sha256sums=('8f0fa7b8b33356f984e40d55bb362ac87651328c30741b30d1fec864e32dba4c'
	    'bd8c849582ccf8608951e4755983b9c56bcbd73e1ea8a09a922a5ed21419c255')

build() {
  cd "$srcdir/cinelerra-$pkgver"

  #make quicktime/ compile
  patch -Np1 -i "$srcdir/quicktime.patch"

  ./configure
  make
}

package() {
  cd "${srcdir}/cinelerra-$pkgver"

  #makes repackaging work
  [ ! -e "bin/cinelerra" ] && \
  	make -C cinelerra && \
	make -C plugins

  make install

  #install puts it in bin/
  rm -rf "$pkgdir/usr/lib/cinelerra/"
  mkdir -p "$pkgdir/usr/lib/cinelerra/"
  mv bin/* "$pkgdir/usr/lib/cinelerra/"

  #no longer do it in .install
  mkdir -p "$pkgdir/usr/bin/"
  ln -s /usr/lib/cinelerra/cinelerra "$pkgdir/usr/bin/cinelerra"
}

```

---

### Post by cyberboycoolen on 2011-09-14
Can't get this to work... Always compile error. Can anyone make a deb for 64 bit natty? Or is the cinelerra-cv version going to up their version to match 4.3?

---

