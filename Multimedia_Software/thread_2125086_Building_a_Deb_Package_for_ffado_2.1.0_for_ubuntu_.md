---
title: "Building a Deb Package for ffado 2.1.0 for ubuntu 12.10"
date: 2013-03-12
forum: Multimedia Software
---

### Post by sev1985 on 2013-03-12
Hi everyone, 

I just installed Ubuntu 12.10 and needed to compile the latest version of ffado (2.1.0) for my audio interface an M-Audio ProFire 610. 
it compiled and installed fine. But when I try to get the firewire backend for jack, the package manager insists on installing the old version of 
ffado (2.0.99). How do I build a deb package from the new ffado version instead of just installing it directly from source?

---

### Post by schragge on 2013-03-13
There's [ffado 2.1.0 package]("https://launchpad.net/ubuntu/+source/libffado")  for raring (Ubuntu 13.04). I guess backporting it to Ubuntu 12.10 would be easier than packaging from scratch. As your /etc/apt/sources.list probably doesn't point to rarian repositories, you can just download the debian source from the link above. There are three files: *.orig.tar.gz, *.debian.tar.gz, and *.dsc. You need all of them.

First, download and unpack the new ffado debian source (2.1.0). There's also another option: [backportpackage]("http://www.atriso.be/2012/06/backporting-packages-easily/"), but I never used it (you probably also need to install and configure [pbuilder]("http://www.tolaris.com/2009/03/31/backporting-debian-packages-with-pbuilder/") for that to work).
```

mkdir src
cd src
wget https://launchpad.net/ubuntu/+archive/primary/+files/libffado_2.1.0%2Bsvn2240.{orig.tar.gz,debian.tar.gz,dsc}
dpkg-source -x *.dsc

```

Then download and unpack the old ffado debian source (2.0.99) and prepare your build environment. (Before doing it, check that you have source repositories enabled.)
```

cd ~/src
apt-get source libffado
sudo apt-get build-dep libffado
sudo apt-get install build-essential devscripts ubuntu-dev-tools quilt
[COLOR=#FF0000]cat <<EOF >~/.quiltrc-dpkg
d=. ; while [ ! -d $d/debian -a `readlink -e $d` != / ]; do d=$d/..; done
if [ -d $d/debian ] && [ -z $QUILT_PATCHES ]; then
QUILT_PATCHES="debian/patches"
QUILT_PATCH_OPTS="--reject-format=unified"
QUILT_DIFF_ARGS="-p ab --no-timestamps --no-index --color=auto"
QUILT_REFRESH_ARGS="-p ab --no-timestamps --no-index"
QUILT_COLORS="diff_hdr=1;32:diff_add=1;34:diff_rem=1;31:diff_hunk=1;33:diff_ctx=35:diff_cctx=33"
[ -d $d/debian/patches ] || mkdir $d/debian/patches
fi
EOF[/COLOR]
[COLOR=green]export DEBFULLNAME="Your Name"
export DEBEMAIL=sev1985@yourdomain.com
alias dquilt="quilt --quiltrc=${HOME}/.quiltrc-dpkg"[/COLOR]

```Lines marked [COLOR=green]green[/COLOR] can be added to your *~/.bashrc*. Lines marked [COLOR=red]red[/COLOR] must be done only once: the [quilt]("http://manpages.ubuntu.com/manpages/precise/en/man1/quilt.1.html") setup will work for all your future deb packages.

You can try to build the new ffado now
```

cd ~/src/libffado-2.1.0
dch -l~sev
[COLOR=#0000ff]# describe your build, e.g. Backport to quantal [/COLOR]
debuild -i -us -uc -b

```
If there are no errors, a bunch of .deb files will be built. You can install them with
```

sudo debi

```
Otherwise, examine the differences between the old and the new source (unpacked in ~/src/libffado-2.0.99 and ~/src/libffado-2.1.0, respectively).  You're mostly interested in the packaging changes that are kept under *debian* directory in source tree. Follow instructions in the [Debian New Maintainers' Guide]("http://www.debian.org/doc/manuals/maint-guide/") (especially [chapter 9]("http://www.debian.org/doc/manuals/maint-guide/update.en.html")) and [Ubuntu Packaging Guide]("http://developer.ubuntu.com/packaging/html/traditional-packaging.html"). [thread=268687]This thread[/thread], albeit quite old, also may be of some help.

---

