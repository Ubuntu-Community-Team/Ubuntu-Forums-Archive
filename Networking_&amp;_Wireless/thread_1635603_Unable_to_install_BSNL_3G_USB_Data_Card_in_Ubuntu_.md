---
title: "Unable to install BSNL 3G USB Data Card in Ubuntu 10.04"
date: 2010-12-02
forum: Networking &amp; Wireless
---

### Post by rawfool on 2010-12-02
I'm using Ubuntu 10.04 & I recently bought BSNL 3G USB Data Card(3.6 Mbps). When I plugged it into Win Vista, it automatically got installed. But when I tried to open it in Ubuntu, I found a .deb file. When I double clicked on .deb file, it gave me some errors. 
> 
**Broken Dependencies**
Your system has broken dependencies. This system cannot continue until this is fixed. To fix it run 'gksudo synaptic' or 'sudo apt-get install -f' in a terminal window.

When I run 'sudo apt-get install -f' in terminal, it gave
> Unable to fetch some archives, may be run apt-get update or try with --fix-missing?

Please help me with this. Thank you.

---

### Post by dineshs on 2010-12-04
Can you post the results of```
lsusb
```and```
dmesg | grep -e "modem" -e "tty" 
```[This]("http://ubuntuforums.org/showthread.php?t=1466490") guide by alexfish may also help

---

### Post by vivek.pandey on 2010-12-04
> **rawfool said:**
> I'm using Ubuntu 10.04 & I recently bought BSNL 3G USB Data Card(3.6 Mbps). When I plugged it into Win Vista, it automatically got installed. But when I tried to open it in Ubuntu, I found a .deb file. When I double clicked on .deb file, it gave me some errors. 


When I run 'sudo apt-get install -f' in terminal, it gave


Please help me with this. Thank you.

dude i ll suggest better switch to ubuntu 10.10 10.04 doesnt spports certain modems including urs,u need to go for a big procedure to make it work then y not 10,10

---

### Post by rawfool on 2010-12-04
@ ***dineshs***
Thanks for your reply dude. Now the problem got rectified and I figured it out as the problem was with .deb package installer.

> rawfool@ubuntu:~$ lsusb
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 05a9:2640 OmniVision Technologies, Inc. OV2640 Webcam
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

rawfool@ubuntu:~$ dmesg | grep -e "modem" -e "tty"
[    0.000000] console [tty0] enabled
[    0.750111] tty tty26: hash matches


---

### Post by pdc on 2010-12-04
> console [tty0] enabled

so your device is being seen as a storage device; not yet as a modem

(if it were seen as a modem, you would seem ttyUSB0 at least)

suggest download and install usb_modeswitch

[http://packages.debian.org/squeeze/usb-modeswitch](http://packages.debian.org/squeeze/usb-modeswitch)

download the package that matches your system ie i386 or AMD or whatever

install; reboot; insert modem: any joy?

______________-

also: is this of any use?

[http://ubuntuforums.org/showthread.php?t=1637090](http://ubuntuforums.org/showthread.php?t=1637090)

__________________________

and another option !!!!!!!!!!!!

is install sakis3g

here is how to install

[http://wiki.sakis3g.org/wiki/index.php?title=Sakis3G_installation](http://wiki.sakis3g.org/wiki/index.php?title=Sakis3G_installation)

and here is the home page for sakis3g

[http://www.sakis3g.org/](http://www.sakis3g.org/)

and here is a post from a grateful user in India reporting success

[http://forum.sakis3g.org/smf/index.php?topic=114.0](http://forum.sakis3g.org/smf/index.php?topic=114.0)

(sakis3g has usb_modeswitch built-in to its package)

---

### Post by rawfool on 2010-12-05
@ **pdc** - Thanks for your kind reply. I followed what you said. I installed i386 file from [http://packages.debian.org/squeeze/usb-modeswitch](http://packages.debian.org/squeeze/usb-modeswitch).

And also installed the packages as directed in [http://wiki.sakis3g.org/wiki/index.php?title=Sakis3G_installation](http://wiki.sakis3g.org/wiki/index.php?title=Sakis3G_installation).


And after installation the status is:
> rawfool@ubuntu:~$ dmesg | grep -e "modem" -e "tty"
[    0.000000] console [tty0] enabled
[    0.778124] tty tty24: hash matches
[   22.786184] cdc_acm 2-1:2.1: ttyACM0: USB ACM device
[   22.786944] cdc_acm 2-1:2.3: ttyACM1: USB ACM device
[   22.793833] cdc_acm: v0.26:USB Abstract Control Model driver for USB modems and ISDN adapters
[   22.887770] cdc_acm 2-1:2.1: ttyACM0: USB ACM device
[   22.888723] cdc_acm 2-1:2.3: ttyACM1: USB ACM device
[   22.893487] cdc_acm: v0.26:USB Abstract Control Model driver for USB modems and ISDN adapters
[   22.935107] cdc_acm 2-1:2.1: ttyACM0: USB ACM device
[   22.938074] cdc_acm 2-1:2.3: ttyACM1: USB ACM device
[   22.941029] cdc_acm: v0.26:USB Abstract Control Model driver for USB modems and ISDN adapters


Please suggest me modifications if any. Thank you once again for your reply.

---

### Post by pdc on 2010-12-05
as you see 

> ttyACM0

your device is now recognised as a modem

plug your modem in; wait a minute

go to network manager; leftmost icon on teh top right of the tool bar;

there should be a prompt there if you left click: new connection?

if so, configure by country and network

if not, tell us what happens

---

### Post by rawfool on 2010-12-06
@ **pdc** - Dude, I didn't find Network Manager icon at the mentioned place. But I went to **System->Preferences->Network Connections** & on **Mobile Broadband** tab, pressed **Add** button and entered the details like Service Provider, Country, APN. That's all. Is that what you were trying to explain?

I didn't see any difference. Can you guide me further. 

Thanks for your reply.

---

### Post by pdc on 2010-12-06
read #5 above

and this post I quoted there

[http://forum.sakis3g.org/smf/index.php?topic=114.0](http://forum.sakis3g.org/smf/index.php?topic=114.0)

I suggest you google on the topic; there are many of your fellow countrymen who have got this to work; I can't at a distance

---

### Post by creatorsofnation on 2011-11-27
[COLOR="Red"]when i follow the above steps it is showing that my package system is broken.....:(
please guide me in a simple way.....[/COLOR]
[B][COLOR="Navy"]1)which package i need to install?
2)how can i get that package?
3)can i install it from software center?
4)will it be easier if i install ubuntu 11.10?(now am using 10.04)
5)please suggest me the ways how to install other modems like tata photon+, reliance 3g,airtel 3g...etc....[/COLOR][/B]

---

### Post by serz152 on 2011-11-27
It dosent work at all it shows connection established  but firefox wont connect it says to try again What now

---

