---
title: "Problem with 3Com OfficeConnect Wireless LAN USB adapter"
date: 2010-09-06
forum: Networking &amp; Wireless
---

### Post by gbl08ma on 2010-09-06
Hi
I have a 3Com 3CRSHEW696 USB WLAN adapter, which worked well (out  of the box) with Ubuntu since I started using it (8.04 version). But now  it seems the last version supporting it is 9.10, since I just installed  10.04 (I know I'm a bit late for the party :)) and I can't manage to get Ubuntu recognizing it.

I simply plug in the card, and instead of having the wireless networks listed on the network applet, it simply doesn't even show the section of "Wireless Networks". Tried to re-insert the card and reboot with no avail.

I've read somewhere in this forum that between 9.10 and 10.04 releases, the  wireless drivers have been changed. If this is correct, how can I  install the old ones, or install other ones supporting this card?

When I do a "ifconfig" on the shell, it only lists the usual interfaces (eth0 and lo), no wlan0 or wifi0 interface.

I have no other wireless cards, and having to use a 3G modem to browse the web is slow and not very cheap :)

Anybody has a solution, or some hint?

Thanks
Gabriel

---

### Post by garyedwardjohnston on 2010-09-06
this is what i'd try

plug in the stick

put in the live ubuntu cd and restart choosing try ubuntu (not install)

if it works on the live disk you know its something with your config...i always like to have all devices plugged into the machine when i install

if it doesnt work try wcid...if that still doesnt work then ndiswrapper

ndis wrapper is a program that uses windows drivers for wireless devices.  you need the windows driver to use with ndiswrapper.  ive had great success with ndis in the past

good luck

---

### Post by gbl08ma on 2010-09-06
Thanks for the reply, I just installed Ubuntu form scratch on a partition I have specifically for installing some Linux when I need/want to. The partition was formatted (it had an old install of Slitaz there) and Ubuntu installed form a Live USB stick.

On the Live USB stick I couldn't connect to the network, too. I'll look into using wcid or ndis, finding the Windows drivers will be easy (hopefully) because I still have the CD that came with the adapter with the drivers, manual and etc.

---

### Post by gbl08ma on 2010-09-13
I installed wcid and it still didn't work (anyways, the wlan0 interface doesn't even exist, so using wcid which is just a front end is no solution).

Then I looked into using ndiswrapper with the drivers that came with the wireless stick CD, which I don't know if they work well with Windows, since on Windows it works out of the box (I plug the adapter in, and  Windows automatically recognizes it like what happened with previous versions of Ubuntu). However, the first time I did a modprobe on Ubuntu to enable the loaded drivers, the whole OS stopped responding after some seconds (the mouse pointer didn't even move!), and I had to hardware reset.

The second, third, etc. times I did modprobe, it didn't hang but still no wlan0 interface shown.

Any ideas? I'm tired of using 3G PPP connection when I get wifi for free :)

---

### Post by gbl08ma on 2010-12-18
bump

I still have this problem, no matter what I do.

It has gone a lot of time since I posted this and now I run Ubuntu 10.10 (not 10.04). However, my wireless card keeps not being recognized in Ubuntu (the menu of the network manager doesn't even show the Wireless Networks section).

I tried loading rWindows drivers through ndiswrapper, and although it does detect when the hardware is present or not, for the network manager it's like there is no hardware. There's no wlan interface (wlan0, wlan1, etc. nor wifi0, wifi1 etc.) either.

Not having Wireless connection is a big pain for me, because although my internet doesn't come by wifi no more, I have a lot of devices connected through my wireless network (including my TV, which has DLNA for media sharing) and it just irritates me that our Windows 7 laptop sends files to the TV (and the TV browses the files of the PC) flawlessly while I can't even connect to my home network on my Ubuntu desktop (which BTW has a much bigger media collection).

**Please post anything you think that could help.** I have shell experience and I can compile drivers if needed, as well as install/remove packages and do advanced configurations.

Solving this connection problem would be a really great Christmas gift for me ;)

EDIT: As I think I already said, this adapter worked well in Ubuntu until version 9.04 (included) - no need to use ndiswrapper, just plug&play. After that, Ubuntu must have changed its wireless drivers which is why my adapter isn't recognized anymore. I don't want to use ndiswrapper more, it simply doesn't work (I have already done troubleshooting according to the stickied forum post), and I guess it would work by installing the old (9.04) drivers. However, I don't know what drivers these are, nor where I can find out what they are...

---

### Post by montclair on 2011-01-06
> **gbl08ma said:**
> bump

I still have this problem, no matter what I do.

It has gone a lot of time since I posted this and now I run Ubuntu 10.10 (not 10.04). However, my wireless card keeps not being recognized in Ubuntu (the menu of the network manager doesn't even show the Wireless Networks section).

I tried loading rWindows drivers through ndiswrapper, and although it does detect when the hardware is present or not, for the network manager it's like there is no hardware. There's no wlan interface (wlan0, wlan1, etc. nor wifi0, wifi1 etc.) either.

Not having Wireless connection is a big pain for me, because although my internet doesn't come by wifi no more, I have a lot of devices connected through my wireless network (including my TV, which has DLNA for media sharing) and it just irritates me that our Windows 7 laptop sends files to the TV (and the TV browses the files of the PC) flawlessly while I can't even connect to my home network on my Ubuntu desktop (which BTW has a much bigger media collection).

**Please post anything you think that could help.** I have shell experience and I can compile drivers if needed, as well as install/remove packages and do advanced configurations.

Solving this connection problem would be a really great Christmas gift for me ;)

EDIT: As I think I already said, this adapter worked well in Ubuntu until version 9.04 (included) - no need to use ndiswrapper, just plug&play. After that, Ubuntu must have changed its wireless drivers which is why my adapter isn't recognized anymore. I don't want to use ndiswrapper more, it simply doesn't work (I have already done troubleshooting according to the stickied forum post), and I guess it would work by installing the old (9.04) drivers. However, I don't know what drivers these are, nor where I can find out what they are...

I got the exactly same problem. I have a 3COM 3CRUSB20075 and I am sitting on Debian 5.0. 
I have done everything it says on here [http://wiki.debian.org/NdisWrapper](http://wiki.debian.org/NdisWrapper) but i don't either have a wlan0 anywhere. 

iwconfig says
> lo        no wireless extensions.

eth0      no wireless extensions.

irda0     no wireless extensions.


Help?

---

### Post by gbl08ma on 2011-02-13
IIRC, from what I can remember from using other, more simpler Linux distros, like Puppy Linux, which display the device chipset instead of its brand name and model on their network utilities, these adapters I have (I have two and I can get access to more, so it's a waste to not have them working on Ubuntu) are **using an Atmel chip**.

They don't need, however, firmware to be uploaded/written on them for their use. The problem is, all the packages I can find for Ubuntu or Debian are all about firmware, or for adapters that require a firmware; furthermore this seems to be for adapters that don't connect through USB but directly to the motherboard (PCI).

I also searched for the source code for the Linux drivers to see if I could compile them myself, but I can find nothing.

Any ideas?
Does anybody know of another adapter that also **stopped working from 9.04 to 9.10**?

It's just that I've been with this problem for more than one year... I wouldn't mind buying a new antenna (if I was sure if came with source code or Ubuntu supported it out-of-the box), but having two of these antennas laying around...

PS: even more annoying is that now, after I played around with ndiswrapper, Ubuntu just hangs when (or some time after) I plug the adapter in. X server stops responding - the mouse pointer doesn't move nor the keyboard does work, and I can't get to the terminal interface.

---

