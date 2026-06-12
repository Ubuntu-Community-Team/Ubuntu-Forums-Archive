---
title: "Quod Libet on Edgy Eft"
date: 2006-10-29
forum: Multimedia &amp; Video
---

### Post by whoosh on 2006-10-29
I'm pretty new at this, but is there any way to install Quod Libet on Edgy Eft?  I extract the .tar and then i run sudo make install and I get a bunch of errors.

```

mkdir -p /usr/local/share/man/man1
mkdir -p /usr/local/bin
mkdir -p /usr/local/share/quodlibet
mkdir -p /usr/local/share/quodlibet/browsers
install -m 644 browsers/*.py /usr/local/share/quodlibet/browsers
mkdir -p /usr/local/share/quodlibet/formats
install -m 644 formats/*.py /usr/local/share/quodlibet/formats
mkdir -p /usr/local/share/quodlibet/qltk
install -m 644 qltk/*.py /usr/local/share/quodlibet/qltk
mkdir -p /usr/local/share/quodlibet/parse
install -m 644 parse/*.py /usr/local/share/quodlibet/parse
mkdir -p /usr/local/share/quodlibet/plugins
install -m 644 plugins/*.py /usr/local/share/quodlibet/plugins
mkdir -p /usr/local/share/quodlibet/util
install -m 644 util/*.py /usr/local/share/quodlibet/util
mkdir -p /usr/local/share/quodlibet/library
install -m 644 library/*.py /usr/local/share/quodlibet/library
intltool-merge -d po exfalso.desktop.in exfalso.desktop
make: intltool-merge: Command not found
make: [exfalso.desktop] Error 127 (ignored)
install -m 755 exfalso.py /usr/local/share/quodlibet
install -m 644 exfalso.1 /usr/local/share/man/man1/exfalso.1
install -D -m 644 exfalso.png /usr/local/share/pixmaps/exfalso.png
install -m 644 exfalso.svg exfalso.png /usr/local/share/quodlibet
install -D -m 644 exfalso.desktop /usr/local/share/applications/exfalso.desktop
install: cannot stat `exfalso.desktop': No such file or directory
make: [app-install-exfalso] Error 1 (ignored)
ln -sf ../share/quodlibet/exfalso.py /usr/local/bin/exfalso
intltool-merge -d po quodlibet.desktop.in quodlibet.desktop
make: intltool-merge: Command not found
make: [quodlibet.desktop] Error 127 (ignored)
install -m 755 quodlibet.py /usr/local/share/quodlibet
install -m 644 quodlibet.1 /usr/local/share/man/man1/quodlibet.1
install -D -m 644 quodlibet.png /usr/local/share/pixmaps/quodlibet.png
install -m 644 quodlibet.svg quodlibet.png /usr/local/share/quodlibet
install -D -m 644 quodlibet.desktop /usr/local/share/applications/quodlibet.desktop
install: cannot stat `quodlibet.desktop': No such file or directory
make: [app-install-quodlibet] Error 1 (ignored)
ln -sf ../share/quodlibet/quodlibet.py /usr/local/bin/quodlibet
install -m 644 config.py const.py player.py stock.py widgets.py rhythmbox-*.png /usr/local/share/quodlibet
for E in _trayicon.so _mmkeys.so; do (test -e $E && install -m 755 -D $E /usr/local/lib/quodlibet/$E); done
make: [install] Error 1 (ignored)
cd po && make install-po DESTDIR=
make[1]: Entering directory `/home/kshyu/Desktop/quodlibet-0.23.1/po'
intltool-update --pot --gettext-package=quodlibet
make[1]: intltool-update: Command not found
make[1]: *** [quodlibet.pot] Error 127
make[1]: Leaving directory `/home/kshyu/Desktop/quodlibet-0.23.1/po'
make: [install] Error 2 (ignored)

```

Any suggestions?

---

### Post by whoosh on 2006-10-29
Actually, it installed...

but now I have other problems...

I can't import songs from my mounted windows partition.  This happens with rhythmbox too.  Anyone know how to fix it?

---

### Post by y0ssarian on 2006-11-09
Does it have to do with the mounted partition's permissions? Can you add songs on the same partition as QuodLibet? Are the songs mp3's or m4a's?

Post your windows partition line from /etc/fstab

---

