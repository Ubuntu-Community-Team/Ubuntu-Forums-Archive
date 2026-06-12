---
title: "How to get sound clip on AMSN"
date: 2007-11-09
forum: Multimedia &amp; Video
---

### Post by awalker2561 on 2007-11-09
List of software to get aMsn working.

tls1.4.1 or tls-1.5.0 fix [http://osdn.dl.sourceforge.net/sourceforge/amsn/tls1.4.1-linux-x86.tar.gz](http://osdn.dl.sourceforge.net/sourceforge/amsn/tls1.4.1-linux-x86.tar.gz)

tcl8.4 and tk8.4 from source [http://www.tcl.tk/software/tcltk/downloadnow84.html](http://www.tcl.tk/software/tcltk/downloadnow84.html)

Snack from source [http://www.speech.kth.se/snack/index.html](http://www.speech.kth.se/snack/index.html)

tlswrap and openssl source (unsure)


INSTRUCTIONS:

Extract tls fix and replace in tls1.5 or 1.50 folder in /usr/lib "Might need to rename tls1.5 to tls1.50 as well"

Compile tcl8.4 and tk8.4

Copy tkConfig.sh to /usr/lib/tk8.4 and tclConfig.sh to /usr/lib/tcl8.4

Compile Snack with "./configure --with-tk=/usr/lib/tk8.4 --with-tcl=/usr/lib/tcl8.4 --enable-alsa" option

Copy snack files from /lib/snack2.2 to /usr/lib directory

Run alsaconf before running aMsn (might not be needed)

Go to volume control, open preference and unmute speakers

Start AMSN, go to account-> preferences-> others-> edit audio and video setting

Also will work with Debian Etch.

Depends on

g++
cpp-4.2
gcc-4.2
libc6-dev
libgomp1
libstdc++6.4.2-dev
linux-libc-dev

libx-dev
libxau-dev
libxdmcp-dev
x11proto-core-dev
x11proto-input-dev
x11proto-kb-dev
xtrans-dev

libasound2-dev

---

### Post by K.Mandla on 2007-11-14
Moved to Multimedia and Video.

---

