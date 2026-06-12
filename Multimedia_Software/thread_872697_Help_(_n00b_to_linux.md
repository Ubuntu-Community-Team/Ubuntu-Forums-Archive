---
title: "Help :( n00b to linux"
date: 2008-07-28
forum: Multimedia Software
---

### Post by kw0me on 2008-07-28
Ok i installed tvtime. :)
ive got a toshiba a200 laptop dual booting vista and ubuntu.

My tv device is a usb hybrid tv tuner (by kaiser baas)
My Videocard is an ATI Radeon HD2600 256m (may be mobility unsure)

the driver that comes with tvtime loads fine with my usb tuner
I have the latest driver for my videocard thats working with ubuntu

when i try to run tvtime - scaner i get this output in term.

kw0me@kw0me-laptop:~$ tvtime - scanner
Running tvtime 1.0.2.
Reading configuration from /etc/tvtime/tvtime.xml
Reading configuration from /home/kw0me/.tvtime/tvtime.xml
xvoutput: No XVIDEO port found which supports YUY2 images.

*** tvtime requires hardware YUY2 overlay support from your video card
*** driver.  If you are using an older NVIDIA card (TNT2), then
*** this capability is only available with their binary drivers.
*** For some ATI cards, this feature may be found in the experimental
*** GATOS drivers: [http://gatos.souceforge.net/](http://gatos.souceforge.net/)
*** If unsure, please check with your distribution to see if your
*** X driver supports hardware overlay surfaces.

Can someone please help me work out what i need to do? it kinda looks simple but i need a bit of direction.

p.s im trying to tune into an analog signal.

---

### Post by kw0me on 2008-07-29
a little help? anyone?

---

### Post by kw0me on 2008-07-29
Ok after some poking around i installed the latest driver from ati so tv time opens now.

Now i have to get my usb tuner working. in windoze its reported as a STK7700D and using lsusb it comes up as this 
Bus 007 Device 006: ID 1164:1f08 YUAN High-Tech Development Co., Ltd

any clues anyone? if i can get this working i will never need windoze again! full linux laptop :)

---

### Post by kw0me on 2008-07-30
yeh heaps helpful forum.....

---

### Post by Brandel Valico on 2008-07-30
Your post is under a day old give people time to respond before getting upset at the fact there are no responses. I'll do some research and see if I can help. No guarantee though as I run TV time through an installed video card not a usb model tv tuner card.

---

### Post by Brandel Valico on 2008-07-30
Okay one quick google search suggests that you may need to install a special usb driver

[http://tvtime.sourceforge.net/cards.html](http://tvtime.sourceforge.net/cards.html)

Thats Tv-times support page where it discusses this and shows the USB driver. Try downloading it and installing it. It is a Tar file and will probably need to be made into a .deb file. But hopefully that will allow you to use tvtime via usb.

You could also check into Xawtv

Which can be added simply by going to add/remove in applications and doing a search for Xawtv and installing it through that method. It may work with the usb card system you have.


Now a word of caution I don't have a USB video card as such these are suggestions that MAY help. They also may not.

---

### Post by xxyzyxx on 2009-08-22
There is a project on LinuxTV to make a driver that will fully support the dib0700 hybrid devices (like yours from YUAN 1164:1f08 and other simmilar). This project need support before it can be started, also from the future users as from the vendors of the devices.
Anyone can help to start the project by for example asking vendors to help or even donate the project your self (hardware and other stuff is needed for testing etc). More info can be found for example on this page:
[http://osdir.com/ml/linux-media/2009-07/msg00065.html](http://osdir.com/ml/linux-media/2009-07/msg00065.html)

I my self am an user of YUAN's 1164:1f08, and would like to get this card fully forking. As you know the main problem for new users of linux, is hardware unsupported by it. They often resign from using linux. More and more laptops (asus, compal, acer, IBM etc) have this cards on board, so it would be good to have this fully working, also for good linux reputation.
So anyone who can help in any way, please do.

---

