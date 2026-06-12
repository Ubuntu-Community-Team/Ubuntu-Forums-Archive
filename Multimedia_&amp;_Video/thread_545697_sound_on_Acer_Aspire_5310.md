---
title: "sound on Acer Aspire 5310"
date: 2007-09-07
forum: Multimedia &amp; Video
---

### Post by leftfieldnz on 2007-09-07
This what i did to get sound going.

lsmod |fgrep snd

card HDA intel chip realtek id 268

[ftp://ftp.alsa-project.org/pub/](ftp://ftp.alsa-project.org/pub/)
download latest driver then lib then util

open a terminal
sudo mkdir src
cd src/
sudo mkdir alsa
 extract the 3 downloaded files to the above folder

cd src/alsa/

cd alsa-driver-1.0.15
sudo ./configure --with-cards=hda-intel
sudo make
sudo make install

Compile and install alsa-lib

cd ../alsa-lib-1.0.15
sudo ./configure
sudo make
sudo make install

Compile and install alsa-utils

cd ../alsa-utils-1.0.15
sudo ./configure
sudo make
sudo make install

Note that you must have the curses library installed to be able to compile alsa-utils. You can install it with this command from a terminal: 
sudo apt-get install libncurses5-dev

sudo kate /etc/modprobe.d/alsa-base

Add the following line to the file, replacing '3stack' with your model (see below for a complete list)

options snd-hda-intel model=acer

alsactl store
alsactl restore

sudo reboot

---

