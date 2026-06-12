---
title: "[SOLVED] playing dvd's on kaffeine"
date: 2008-04-17
forum: Multimedia &amp; Video
---

### Post by nasaJ81 on 2008-04-17
i am brand new to ubuntu. i recently downloaded kaffeine to try and play dvds. Because totem will not.This is the message i get 04:10:48 PM: xine: couldn't find demux for >dvd://<
04:10:48 PM: xine: found input plugin : DVD Navigator
03:53:17 PM: xine: couldn't find demux for >dvd://<
03:53:15 PM: xine: found input plugin : DVD Navigator
03:48:11 PM: xine: couldn't find demux for >dvd://<
03:48:11 PM: xine: found input plugin : DVD Navigator

Can anyone help me with this problem and guide me what to do.
And im not a computer genius so take it easy on me..

---

### Post by xc3RnbFO8P on 2008-04-17
Install in Synaptic Package Manager:

libmad0
libmad0-dev
python-pymad

k3b
k3b-i18n
libk3b2
libk3b2-extracodecs
libk3b2-mp3
libk3b-dev

dvd95
dvdauthor
liba52
liba52 dev
libdvdnav4
mkisofs

In Terminal:
> 
wget -c [http://packages.medibuntu.org/pool/non-free/w/w32codecs/w32codecs_20071007-0medibuntu1_i386.deb](http://packages.medibuntu.org/pool/non-free/w/w32codecs/w32codecs_20071007-0medibuntu1_i386.deb)
> sudo dpkg -i w32codecs_20071007-0medibuntu1_i386.deb
> wget -c [http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.9-2medibuntu4_i386.deb](http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.9-2medibuntu4_i386.deb)
> sudo dpkg -i libdvdcss2_1.2.9-2medibuntu4_i386.deb
> sudo apt-get install libdvdread3 libxine1-ffmpeg totem-xine build-essential debhelper fakeroot
> sudo /usr/share/doc/libdvdread3/install-css.sh
Now you would be able to play and burn Dvds.

---

### Post by nasaJ81 on 2008-04-17
ok i just installed all those..and i finally got the dvd to start playing..and then it stops and i get this message Maybe you don't have enough rights for this, or source doesn't contain data (e.g: no disc in drive). (Error reading NAV packet.)

---

### Post by nasaJ81 on 2008-04-17
im sorry i didnt do everything..hold on

---

### Post by nasaJ81 on 2008-04-17
Ok I Did It All And It Works..thank-you So Much..i Would Of Never Figured All That Out..thank-you Thank-you

---

