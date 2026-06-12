---
title: "transkode in Amarok on AMD64"
date: 2006-12-21
forum: Multimedia &amp; Video
---

### Post by Tim Sawyer on 2006-12-21
Hi,

I've got my ipod happily connected to amarok in Edgy.  However, all my music is in flac format, and I need to transcode it to mp3 to transfer it.

The transkode script in Amarok doesn't work on AMD64.  The error it comes out with is:

/home/tjs/.kde/share/apps/amarok/scripts/transkode/transkode: error while loading shared libraries: libtag.so.1: wrong ELF class: ELFCLASS64

Anyone have a fix that doesn't involve recompiling the plugin?

ta,

Tim.

---

### Post by jetpeach on 2007-02-14
i have a related problem, but different enough i started a different thread.  it may be helpful to you though
[http://www.ubuntuforums.org/showthread.php?p=2158476](http://www.ubuntuforums.org/showthread.php?p=2158476)

---

### Post by Tim Sawyer on 2007-02-15
I gave in and installed the x86 version on my AMD X2...it's much simpler to get stuff like Flash player to work!

Tim.

---

### Post by Fatboy Snarky on 2007-07-20
Hi,


I recently installed Feisty and I had no problem compiling the amarok-transkode-plugin.

I obtained the source package from [http://www.kde-apps.org/content/show.php?content=37669](http://www.kde-apps.org/content/show.php?content=37669) (transkode-0.6.tar.bz2 at the time being).

As dependencies, I installed "kdebase-dev" and "libtag1-dev". (Others like "build-essential" etc. were already installed; maybe on other systems, additional packages have to be installed)

The compilation was straight forward: 

tar -xjf transkode-0.6.tar.bz2
cd transkode-0.6
./configure
make
sudo make install


After restarting Amarok, the plugin worked.

HTH,
Ulrich

---

### Post by om1d3 on 2008-01-21
[COLOR="Navy"]You just simply copy **transkode** fom **/usr/bin** to **/home/username/.kde3.5/share/apps/amarok/scripts/transkode**.
Ok, first you install transkode via apt-get (or whatever) for x86-64 and then copy it.
At least that's what made it work for me in Gentoo and since this is the only encounter of the error in Google I thought you want a fix (quick and dirty).
Anyway, have fun.[/COLOR]

---

### Post by dbenc on 2008-06-08
are you having trouble transcoding more than one track at a time? mine wont do it :S i guess its because im using the x86-64 version ...

---

