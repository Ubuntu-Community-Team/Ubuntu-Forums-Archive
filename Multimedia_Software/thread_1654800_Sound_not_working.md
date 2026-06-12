---
title: "Sound not working"
date: 2010-12-28
forum: Multimedia Software
---

### Post by joshbeebe on 2010-12-28
I've been having problems with my sound. In Windows 7 my sound works fine. I just installed Ubuntu 10.4 and tried to play music through Rhythmbox and it didn't work. I've searched online for answers and every fix I've tried didn't work. All of my audio settings are turned all the way up but nothing. I tried a program that does a system beep and I also got nothing with that. Any ideas on what the problem could be?

---

### Post by joshbeebe on 2010-12-28
I just checked my headphones and they do work. Also, this is a laptop if that is of any help.

---

### Post by lidex on 2010-12-29
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by kiki298 on 2010-12-29
I have a similar problem, but it is reversed for me. My speakers are working, but my headphones will not. The music just keeps playing from the speakers when the headphones are plugged in. I have an Asus, it's model number is U52F-BBL9.

This is my output:

[http://www.alsa-project.org/db/?f=c95cc568ef74bdb60e26b8e98c7b89dabea5e995](http://www.alsa-project.org/db/?f=c95cc568ef74bdb60e26b8e98c7b89dabea5e995)

Thanks for any help!

---

### Post by lidex on 2010-12-29
@kiki298
I see you have selected model=hp-laptop. Try changing that to auto:
```
options snd-hda-intel model=auto
```

Can you post this output please:
```
cat /etc/modprobe.d/alsa-base.conf
```

---

### Post by kiki298 on 2010-12-29
Thank you so much, your suggestion to change to auto worked!

My output for the cat /etc/modprobe.d/alsa-base.conf is:


```
kiki@kiki-U52F:~$ cat /etc/modprobe.d/alsa-base.conf
# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-ioctl32 ; /sbin/modprobe --quiet --use-blacklist snd-seq ; }
#
# Workaround at bug #499695 (reverted in Ubuntu see LP #319505)
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; /sbin/modprobe --quiet --use-blacklist snd-seq-oss ; : ; }
#
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-caiaq index=-2
options snd-usb-ua101 index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2
# Keep snd-usb-audio from beeing loaded as first soundcard
options snd-usb-audio index=-2
options snd-hda-intel index=0 model=toshiba position_fix=1
options snd-hda-intel model=auto
```

Again, thanks so much!

---

### Post by sorabh.v6 on 2011-03-26
sound of mine ubuntu also not working plz somebody help me out......
i ran the above command in terminal and got the following link
[http://www.alsa-project.org/db/?f=fd339006b0e7edf0b1857218edcc4b23a732fc16](http://www.alsa-project.org/db/?f=fd339006b0e7edf0b1857218edcc4b23a732fc16)

---

### Post by lidex on 2011-03-31
> **sorabh.v6 said:**
> sound of mine ubuntu also not working plz somebody help me out......
i ran the above command in terminal and got the following link
[http://www.alsa-project.org/db/?f=fd339006b0e7edf0b1857218edcc4b23a732fc16](http://www.alsa-project.org/db/?f=fd339006b0e7edf0b1857218edcc4b23a732fc16)

Using a Terminal="Applications->Accessories->Terminal"
```
sudo aptitude --purge reinstall linux-sound-base alsa-base alsa-utils linux-image-`uname -r` linux-ubuntu-modules-`uname -r` libasound2
```
**Reboot.**

For a 'command not found' error simply install aptitude:
```
sudo apt-get install aptitude
```

---

### Post by sorabh.v6 on 2011-04-03
dude i did as you mentioned above but nothing happened and it showed this in terminal

sony@sony-laptop:~$ sudo aptitude --purge reinstall linux-sound-base alsa-base alsa-utils linux-image-`uname -r` linux-ubuntu-modules-`uname -r` libasound2
[sudo] password for sony: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Writing extended state information... Done
Couldn't find any package whose name or description matched "linux-ubuntu-modules-2.6.32-30-generic"
Couldn't find any package whose name or description matched "linux-ubuntu-modules-2.6.32-30-generic"
The following packages will be REINSTALLED:
  alsa-base alsa-utils libasound2 linux-image-2.6.32-30-generic 
  linux-sound-base 
The following packages will be REMOVED:
  freepats{pu} libcdaudio1{pu} libcelt0-0{pu} libdc1394-22{pu} 
  libdirac-encoder0{pu} libfftw3-3{pu} libflite1{pu} libgme0{pu} 
  libiptcdata0{pu} libkate1{pu} libmimic0{pu} libmms0{pu} libofa0{pu} 
  libopenspc0{pu} liborc-0.4-0{pu} libsoundtouch1c2{pu} libwildmidi0{pu} 
0 packages upgraded, 0 newly installed, 5 reinstalled, 17 to remove and 1176 not upgraded.
Need to get 0B of archives. After unpacking 51.5MB will be freed.
Do you want to continue? [Y/n/?] y
E: I wasn't able to locate file for the linux-image-2.6.32-30-generic package. This might mean you need to manually fix this package.
Writing extended state information... Done
E: Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavailable)
E: Couldn't lock list directory..are you root?
sony@sony-laptop:~$ sudo apt-get install aptitude
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libwildmidi0 liborc-0.4-0 libflite1 libdc1394-22 libsoundtouch1c2
  libopenspc0 libfftw3-3 libgme0 freepats libkate1 libcdaudio1 libmimic0
  packagekit-backend-apt libcelt0-0 libdirac-encoder0 virtuoso-nepomuk libofa0
  libmms0 libiptcdata0
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  apt apt-transport-https apt-utils gtk2-engines-pixbuf kpackagekit
  libboost-iostreams1.42.0 libdbus-glib-1-2 libdbusmenu-qt2 libdebconf-kde0
  libept1 libgail-common libgail18 libgdk-pixbuf2.0-0 libglib2.0-0 libgtk2.0-0
  libgtk2.0-bin libkdecore5 libkdeui5 libkio5 libkparts4 libkutils4 liblzma2
  libmng1 libncurses5 libncursesw5 libnepomuk4 libpackagekit-glib2-14
  libpackagekit-qt-14 libphonon4 libqt4-assistant libqt4-dbus libqt4-designer
  libqt4-help libqt4-network libqt4-opengl libqt4-qt3support libqt4-script
  libqt4-scripttools libqt4-sql libqt4-sql-mysql libqt4-sql-sqlite libqt4-svg
  libqt4-test libqt4-webkit libqt4-xml libqt4-xmlpatterns
  libqtassistantclient4 libqtcore4 libqtgui4 libqtwebkit4 librsvg2-2
  librsvg2-common libsolid4 libsoprano4 libsqlite3-0 libvte9 libwmf0.2-7
  libwmf0.2-7-gtk packagekit packagekit-backend-apt packagekit-backend-aptcc
  phonon-backend-xine python-apt python-packagekit soprano-daemon synaptic
Suggested packages:
  dpkg-dev apt-doc aptitude-doc-en aptitude-doc debtags hspell libqt4-dev
  qt4-qtconfig librsvg2-bin packagekit-backend-smart python-apt-dbg
  python-apt-doc virtuoso-minimal dwww menu deborphan
Recommended packages:
  gpg libdconf0 kdelibs5-plugins
The following packages will be REMOVED:
  libept0 libpackagekit-glib2-12 libpackagekit-qt-12
The following NEW packages will be installed:
  libboost-iostreams1.42.0 libdebconf-kde0 libept1 libgdk-pixbuf2.0-0
  libkdecore5 libkdeui5 libkio5 libkparts4 libkutils4 liblzma2 libnepomuk4
  libpackagekit-glib2-14 libpackagekit-qt-14 libqtassistantclient4
  libqtwebkit4 libsolid4 packagekit-backend-aptcc
The following packages will be upgraded:
  apt apt-transport-https apt-utils aptitude gtk2-engines-pixbuf kpackagekit
  libdbus-glib-1-2 libdbusmenu-qt2 libgail-common libgail18 libglib2.0-0
  libgtk2.0-0 libgtk2.0-bin libmng1 libncurses5 libncursesw5 libphonon4
  libqt4-assistant libqt4-dbus libqt4-designer libqt4-help libqt4-network
  libqt4-opengl libqt4-qt3support libqt4-script libqt4-scripttools libqt4-sql
  libqt4-sql-mysql libqt4-sql-sqlite libqt4-svg libqt4-test libqt4-webkit
  libqt4-xml libqt4-xmlpatterns libqtcore4 libqtgui4 librsvg2-2
  librsvg2-common libsoprano4 libsqlite3-0 libvte9 libwmf0.2-7 libwmf0.2-7-gtk
  packagekit packagekit-backend-apt phonon-backend-xine python-apt
  python-packagekit soprano-daemon synaptic
50 upgraded, 17 newly installed, 3 to remove and 1138 not upgraded.
E: Could not get lock /var/cache/apt/archives/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the download directory

---

### Post by lidex on 2011-04-03
Two things are obvious: your system is not up to date and you have another package manager open when trying to do that. Make sure update manager and synaptic are closed then do this in a terminal:
```
sudo apt-get update
sudo apt-get upgrade
```
Once that completes, do the alsa re-install.

---

### Post by sorabh.v6 on 2011-04-10
sir but i dont know how to reinstall alsa and what alsa is........cause i m a newbie to linux.And can u suggest me any refrence for learning linux.

---

### Post by lidex on 2011-04-10
> **sorabh.v6 said:**
> sir but i dont know how to reinstall alsa and what alsa is........cause i m a newbie to linux.And can u suggest me any refrence for learning linux.

Look at post #8, just redo what you were previously trying.

---

### Post by sorabh.v6 on 2011-04-11
sound is now perfect, thanks to every one who replied.I want to know more about linux ,so can anyone reffer me any book, by the i am doing my b.tech from it stream.

---

### Post by mindwarpusa on 2011-04-11
I'm having a simillar problem, I switched my htpc from windows xp to ubuntu 10.10 and since i switched my audio no longer works i used the cmd from the second or so reply and these are my results



[http://www.alsa-project.org/db/?f=bb3d7d6dd85bd9ef343ced27a010c560704f487c](http://www.alsa-project.org/db/?f=bb3d7d6dd85bd9ef343ced27a010c560704f487c)

---

### Post by kaip on 2011-04-11
I'm having a similar problem.  Ever since I accidentally hibernated a few months ago, my sound has not worked.

[http://www.alsa-project.org/db/?f=935205897e49875e847fa6ad18d8fe28969a3478](http://www.alsa-project.org/db/?f=935205897e49875e847fa6ad18d8fe28969a3478)

---

