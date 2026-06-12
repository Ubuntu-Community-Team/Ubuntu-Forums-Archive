---
title: "No sound (gstreamer issue)"
date: 2007-10-20
forum: Multimedia &amp; Video
---

### Post by dest581 on 2007-10-20
I just installed the new release on my fairly new dell laptop, and sound doesn't work at all.  If I double click on the sound icon on the panel, I get the following error:
> No volume control GStreamer plugins and/or devices found

It doesn't seem to notice the built in speakers or the headphone-out jack.

Help with diagnosing/fixing the problem would be appreciated.

---

### Post by grupotux on 2007-10-20
I installed Gutsy yesterday from the Alternate CDROM on and older Toshiba A10-S177 with the same result. The only difference is that I can hear the login drum. Once up, however, there is no sound and the volume control icon shows a red x.  Pressing the right hand mouse button over the icon brings forth the same gstreamer error. Any clues, anyone?  :(

---

### Post by Qu4k3R on 2007-10-21
It's happening the same to me :'(

I am installing with this command:

> 
sudo aptitude install sound~n pulseaudio-esound-compat


This is dangerous because it will remove the following packages:

> 
fast-user-switch-applet
gdm
pulseaudio-esound-compat
ubuntu-desktop


So I'll need to reinstall the «gdm», the «ubuntu-desktop» and the «fast-user-switch-applet» packages.

I'll reply again later if this works..


PS: I got also a bug with wireless..
doing
> 
sudo ifconfig eth1 up


Does not bring the eth1 device.. (wireless)
PM me if you know how to put wireless working ;)

thanks in advance.

**[ EDIT ]**

I recompiled alsa but it stays the same thing..
Help is appreciated.


** [BIG EDIT - AGAIN! ]  **

I went to my sound board hardware site then downloaded the drivers for linux.

It is working fine..

It was only my intel (sound board) drivers..
went to
[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=6&PFid=6&Level=5&Conn=4&DownTypeID=3&GetDown=false#RTL8100B(L)/RTL8100C(L)/RTL8101L/RTL8139C(L)/RTL8139C(L)+/RTL8139D(L)/RTL8100(L)/RTL8130/RTL8139B(L](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=6&PFid=6&Level=5&Conn=4&DownTypeID=3&GetDown=false#RTL8100B(L)/RTL8100C(L)/RTL8101L/RTL8139C(L)/RTL8139C(L)+/RTL8139D(L)/RTL8100(L)/RTL8130/RTL8139B(L))

and
[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=24&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false#High%20Definition%20Audio%20Codecs](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=24&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false#High%20Definition%20Audio%20Codecs)

the site is [http://www.realtek.com.tw/](http://www.realtek.com.tw/)
[---------------------------------------------]
thanks anyway.

---

### Post by twizler on 2007-10-25
,-O 
      O(_)) Ubuntu GUSTY 7.1
       `-O  
H[COLOR="DarkGreen"]OW TO FIX[/COLOR]
 [COLOR="Red"]No volume control GStreamer plugins and/or devices found.[/COLOR]
> 

READ MY POST BELOW USE ALSA SCRIPT~~

---

### Post by grupotux on 2007-10-28
My sound chipset is an earlier ICH4 type. Compiling ALSA from source resolved nothing, however,
to my great surprise, running the «The Battle for Wesnoth» game produces clear sound. Does this
provide a new clue?

I find it disturbing that after four (4) weeks this thread remains inactive.

---

### Post by twizler on 2008-01-04
THIS WORKS EVEN BETTER -- 
Copy and past into a file. call it alsa_1.sh ( i used gedit) 


> open gedit -- copy and past the section below. 
> 
#!/bin/sh
#
#install necessary stuff
apt-get install build-essential ncurses-dev gettext
apt-get install linux-headers-`uname -r`

echo "downloading alsa packages..."
wget [ftp://ftp.alsa-project.org/pub/drive...1.0.15.tar.bz2](ftp://ftp.alsa-project.org/pub/drive...1.0.15.tar.bz2)
wget [ftp://ftp.alsa-project.org/pub/lib/a...1.0.15.tar.bz2](ftp://ftp.alsa-project.org/pub/lib/a...1.0.15.tar.bz2)
wget [ftp://ftp.alsa-project.org/pub/utils...1.0.15.tar.bz2](ftp://ftp.alsa-project.org/pub/utils...1.0.15.tar.bz2)

echo "extracting alsa packages..."
tar -xjf alsa-driver*.tar.bz2
tar -xjf alsa-lib*.tar.bz2
tar -xjf alsa-utils*.tar.bz2
rm alsa*.tar.bz2

echo "setting up alsa for compilation"
mkdir -p /usr/src/alsa
mv alsa-* /usr/src/alsa

#alsa-driver
cd /usr/src/alsa/alsa-driver*
./configure --with-cards=hda-intel
make
make install

#alsa-lib
cd /usr/src/alsa/alsa-lib*
./configure
make
make install

#alsa-utils
cd /usr/src/alsa/alsa-utils*
./configure
make
make install

echo "now reboot and you should be able to hear sound"
echo "&#$#$#   8uy m3 A b33r s0m3day s1nc3 y0u gt it 2 w0rk!"
echo " reboot please"
echo " from command terminal you can type:  sudo reboot"
#end of alsa_1

> 
from terminal type:       sh alsa_1.sh

> Script downloads alsa and configures driver ... takes like 5min best part is you dont do any thing but watch the magic happen. 

---

