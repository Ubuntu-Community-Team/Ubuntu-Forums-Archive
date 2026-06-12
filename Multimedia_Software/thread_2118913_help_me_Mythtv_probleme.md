---
title: "help me Mythtv probleme"
date: 2013-02-22
forum: Multimedia Software
---

### Post by freeman075 on 2013-02-22
hi ever one  i need help with mythtv 
i cant slove dvbs card probleme im sorry for my bad english 
[URL="http://imageshack.us/f/829/screenshottuq.png/"]http://imageshack.us/f/829/screenshottuq.png/
[/URL] <IMG SRC="[imageshack.us/f/829/screenshottuq.png]("http://imageshack.us/f/829/screenshottuq.png/")">

<IMG SRC="[http://]("http://imageshack.us/f/829/screenshottuq.png/")[imageshack.us/f/829/screenshottuq.png]("http://imageshack.us/f/829/screenshottuq.png/")">

[IMG]http://imageshack.us/f/829/screenshottuq.png/[/IMG][IMG]http://imageshack.us/f/829/screenshottuq.png[/IMG]

---

### Post by BicyclerBoy on 2013-02-23
First the tuner card has to be recognised by kernel/driver.
Then (potentially) firmware loaded.

Most tuner cards need a/the firmware package installed.

From a terminal:
dmesg | grep dvb

You can find what the system identifies as the tuner from either:
lspci
lsusb

Can check on LinuxTV.org (v4l-dvb) for state of tuner support.

---

### Post by freeman075 on 2013-02-23
My Card works good in kaffeine 
thats probleme only in mythtv

---

### Post by BicyclerBoy on 2013-02-23
You could have mentioned that...

Looking at your image...it looks like you picked your card as a mpeg encoder capture card (analogue in) & it is not. It is a DVB DTV capture card..
[http://www.mythtv.org/wiki/User_Manual:Setting_up_DVB-S_for_satellite](http://www.mythtv.org/wiki/User_Manual:Setting_up_DVB-S_for_satellite)

MythTV must have complete control of tuners...no sharing with other programs.
To allow another application to use "mythtv" tuner you have to stop the backend service
(sudo service mythtv-backend stop)

The same *could* be true of Kaffeine..
Does kaffeine have a backend service that runs at startup?

It is a good idea to:
Manually stop the backend (as above) before starting mythtv-setup..
Start mythtv-setup from terminal with logging:
mythtv-setup -v general

I never used kaffeine (xine based) because it is/was livetv focused & never supported LATM-AAC/h264 5 years ago or even 1 year ago.

---

