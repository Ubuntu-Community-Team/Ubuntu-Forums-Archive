---
title: "No Direct Draw on Intel Mobile GM965/GL960"
date: 2008-01-05
forum: Multimedia &amp; Video
---

### Post by birdywa on 2008-01-05
hello, I have a Thinkpad R61i with an Intel Mobile GM965/GL960 according to lspci. glxinfo returns direct draw: no. This is a problem because it is making starcraft run horribly slow in wine and screensavers run slow too. Basically it cripples anything 3d. The screen and graphics window says that I am using VESA for the driver, which was the default on a fresh install. When i tried to chose the propper driver, though, it crippled X11, so I had to revert it back. Has anybody else had problems with this card?

---

### Post by birdywa on 2008-01-06
bump

---

### Post by nashgurl on 2008-01-17
I'm having problems!!!
I can't get it to go higher that 800x600.

This is really fustrating.. and I can't find a fix.

I'm REALLY new to the whole linux/ubuntu thing... so I don't know how to install a driver or to make it work. 

I need help!!!!!!!!!!

---

### Post by lukus on 2008-01-30
hi nashgurl, im pretty new to this too, and I have the same graphics card.  It is a problem with ubuntu thinking that the graphics card has a TV-out on it...and it doesnt.  For a temporary fix, open terminal and enter

xrandr --output TV --off

I managed a permanent fix by doing this...

wget [http://ppa.launchpad.net/kyle/ubuntu/pool/main/x/xserver-xorg-video-intel/xserver-xorg-video-intel_2.1.1-0ubuntu10_amd64.deb](http://ppa.launchpad.net/kyle/ubuntu/pool/main/x/xserver-xorg-video-intel/xserver-xorg-video-intel_2.1.1-0ubuntu10_amd64.deb)

sudo dpkg -i xserver-xorg-video-intel_2.1.1-0ubuntu10_amd64.deb

then:

dpkg-reconfigure xserver-xorg

If you want to use an external monitor, use this:

xrandr --output VGA --auto

hope that helps...

---

