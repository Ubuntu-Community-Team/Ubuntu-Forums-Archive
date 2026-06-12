---
title: "ythTV on Ubuntu 7.10 x64"
date: 2008-04-06
forum: Multimedia &amp; Video
---

### Post by prcm311 on 2008-04-06
I've searched for information on how to install MythTV on Ubuntu 7.10 x64 but I didn't find anything very useful on the subject.

I have a fresh install of 7.10 x64 on my machine right now with only a few extra installations such as flash, restricted nvidia drivers, and audio/video codecs.  Nothing that should conflict with the installation of MythTV or MySQL.  However when I installed MythTV and tried to run 'mythtv-setup' I get a MySQL error.  I'm not familiar with MySQL and unsure if it works with x64 (I assume it should).  I do get to the setup screen but once I select the language and verify the database info it exits.  I've attached the terminal output I get.

_General Installations:_

libfreebob0		
libstdc++5		
libfaad2-0		
libavutil1d		
unrar		
transmission		
gstreamer0.10-plugins-bad		
lib32ncurses5		
nspluginwrapper		
python-compizconfig		
gstreamer0.10-plugins-ugly		
libgtk1.2		
jscalibrator		
libglib1.2		
ia32-libs		
odbcinst1debian1		
libquicktime1		
transmission-cli		
gstreamer0.10-plugins-bad-multiverse		
libjack0		
ubuntu-restricted-extras		
libmp4v2-0		
transmission-gtk		
java-common		
sun-java6-bin		
libc6-i386		
libavcodec1d		
lib32gcc1		
unixodbc		
libx264-54		
lib32asound2		
sun-java6-jre		
gstreamer0.10-ffmpeg		
gcc-3.3-base		
lm-sensors		
liba52-0.7.4		
cabextract		
compizconfig-settings-manager		
libgsm1		
libdvdread3		
libcdaudio1		
libgtk1.2-common		
libxvidcore4		
libsidplay1		
libsoundtouch1c2		
libmad0		
libid3tag0		
libmjpegtools0c2a		
lib32z1		
gstreamer0.10-plugins-ugly-multiverse		
flashplugin-nonfree		
lib32stdc++6		
libjsw2		
sensors-applet		
msttcorefonts		
xserver-xorg-input-joystick		
libmpcdec3		
liblame0		
libmpeg2-4		
libmms0		
libfaac0		

_MythTV:_

mythtv-database		
pwgen		
libnet-daemon-perl		
libartsc0		
liblzo1		
mythtv		
libmysqlclient15off		
libfame-0.9		
mysql-server		
libdbi-perl		
libpvm3		
mythtv-common		
mythtv-backend		
libdbd-mysql-perl		
gawk		
libpostproc1d		
transcode		
ntp		
libqt3-mt-mysql		
mysql-client		
libmyth-0.20		
libplrpc-perl		
libxvmc1		
mythtv-frontend		
libqt3-mt		
libaudio2		
mysql-common		
mysql-server-5.0		
mythtv-transcode-utils		
mysql-client-5.0

_My question:_

Is there a way to install MythTV and MySQL on an x64 system and if so what are the patches or dependencies I'm missing.

---

### Post by wolfen69 on 2008-04-06
```
 sudo apt-get install mysql-common mysql-client-5.0 

```then try installing myth tv.

---

### Post by prcm311 on 2008-04-06
I have those packages installed already... or do you mean I should have installed them first?

---

### Post by prcm311 on 2008-04-06
Alright I was able to figure it out.

It helps to install MySQL first and set that up then install MythTV.

This issue was caused by a simple password mistake.  I had to provide MythTV with the root password to MySQL.

---

