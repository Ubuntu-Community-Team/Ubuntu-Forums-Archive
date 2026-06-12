---
title: "Color Mismatch with .avi-files"
date: 2007-03-25
forum: Multimedia &amp; Video
---

### Post by asdir on 2007-03-25
As can be seen in the image below I have a problem with a color mismatch in videos (In my example the red blur on the clock should be where it says '7:00' for instance). It appears with .avi-files only but not with all of them. The system is a relatively fresh install of Edgy and I have installed codecs via Automatix, including w32codecs. Moreover I installed the nvidia video driver and recently installed compiz according to the unofficial ubuntu guide. (Both of the last mentioned installs fiddled with the xorg.conf which is why I mentioned them.)
The problem appears with Totem as well as VLC. When I start the Xine-gui, i also have a scrambled user interface (the thing you get when you press 'g'). (That may however be due to another problem of course.)
The graphics card is a geforce3.
Anymore specs you need?
Thanks in advance for any help.
[IMG]http://img481.imageshack.us/img481/4968/bildschirmfoto2fy4.png[/IMG]
This image was made via a usual ubuntu screenshot since the screenshot out of Totem showed a clear picture.

---

### Post by njtromp on 2007-04-04
You might try the directions given at [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu) They worked for me.

In short (I'm using 6.06 Dapper)
[LIST=1]
[*]wget -q [http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg](http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg) -O- | sudo apt-key add -
[*]sudo wget [http://medibuntu.sos-sts.com/sources.list.d/dapper.list](http://medibuntu.sos-sts.com/sources.list.d/dapper.list) -O /etc/apt/sources.list.d/medibuntu.list
[*]sudo apt-get update
[*]sudo apt-get install libdvdcss2
[*]sudo apt-get install w32codecs
[*]Logout and login again
[/LIST]

Cheers Nico

---

