---
title: "Clear 4G Mobile USB - How can I get this working?"
date: 2010-07-27
forum: Networking &amp; Wireless
---

### Post by Alvina on 2010-07-27
My mom just switched from Comcast to Clear 4G Mobile Internet service and I don't know how to get this working on a Ubuntu 10.04 system.  The Clear installation USB only gives me two options: Windows Users and Mac OS X Users.

I was wondering if the Linux WiMax driver would be instrumental in having Clear work on my Ubuntu 10.04 system.  From this website: [http://www.linuxwimax.org/Home](http://www.linuxwimax.org/Home)

However, if there are no other options, we do have 10 days to back out of the contract.

I would really appreciate it if someone could steer me in the right direction.  I'm a dim light bulb when it comes to these things.

If I didn't provide enough info, just let me know!

(I attached a screenshot of the Clear modem that I have.)

---

### Post by pdc on 2010-07-27
I suggest:

turn on the computer; when booted, plug in this device; wait 30-60secs

left-click on network manager; the left-most of the icons at the TOP RIGHT of the screen; does the network you want to connect to show up there?

If not, open a terminal

type in 

> lsusb

copy and paste the results back here and we can try to help

---

### Post by Alvina on 2010-07-27
> **pdc said:**
> I suggest:

turn on the computer; when booted, plug in this device; wait 30-60secs

left-click on network manager; the left-most of the icons at the TOP RIGHT of the screen; does the network you want to connect to show up there?

If not, open a terminal

type in 



copy and paste the results back here and we can try to help


The attached picture is the USB that they provide us for the installation, so that we can be able to use the Clear modem (the picture attached in my first post).  When I plug in this green USB thingy, a 'CLEAR' icon pops up on my desktop... I open that and two options come up: Mac OS X users & Windows Users... I don't fall under either of those categories.  

My mom wants to keep Clear for their cheap price... Although, they don't support Linux... I would rather boot into Ubuntu 10.04 than Windows 7.  I was wondering if anything would change if I downloaded a Linux WiMax driver.

I typed in that command and this is what it shot out: 

Bus 002 Device 007: ID 0489:e016 Foxconn / Hon Hai 
Bus 002 Device 006: ID 046d:c018 Logitech, Inc. Optical Wheel Mouse
Bus 002 Device 002: ID 8087:0020  
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 006: ID 0bda:0159 Realtek Semiconductor Corp. 
Bus 001 Device 003: ID 0402:9665 ALi Corp. 
Bus 001 Device 002: ID 8087:0020  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

Any ideas?

---

### Post by pdc on 2010-07-28
I don't recognise any of the IDs on the lsusb printout;

the device is being seen as storage for software; it needs to be flipped to be seen as a modem;

1) RIGHT-CLICK on the icon on the desktop for CLEAR; on the drop-down menu, select EJECT; wait

try 

> lsusb

have any of the IDs changed; if so, 

LEFT-CLICK on network manager; top bar; left-most of the right-hand icons ..

2) if no joy above, 

I think you need to join the usb_modeswitch forum

[http://www.draisberghof.de/usb_modeswitch/bb/](http://www.draisberghof.de/usb_modeswitch/bb/)

as I can't see your device listed on the existing hardware;

Josh oversees the programme, and the forum, and he will help you

---

### Post by p110011 on 2010-07-30
Alvina, we've asked for drivers on the Clear.net forum and so far it's a no-go, in the mean time I use a ClearSpot mobile router and USB modem like you're Mom's. Clear also has the newer ClearSpots for rent or sale. I want to get a wifi tablet anyways and the ClearSpot works pretty good.

---

### Post by iyerra on 2010-08-01
I am all set to buy a Linux laptop from [www.zareason.com](www.zareason.com) as soon as figure out the working solution for using Clear 4G USB. 

While almost everyone around me has a wireless Windows laptop, it will be kind of different to explore the world of Ubuntu and help others around me understand how that can be different. 

If I combine Clear and Ubuntu, it sounds like "Ubuntu"ntly "Clear" (or abundantly clear) to me ;)

Please share the finalized details of the working solution so that I can use it setup my Linux laptop. 

Thanks,

Ramu

---

### Post by nutznboltz on 2010-08-24
Has anybody tried the Clear devices with a newer network-manager?

This is the daily build PPA:

[https://launchpad.net/~network-manager/+archive/trunk](https://launchpad.net/~network-manager/+archive/trunk)

---

### Post by mnaines on 2010-08-26
I will be getting my Clear Mobile USB (Series S) later today.  Because I run Ubuntu full-time, I am going to do an experiment to see if I can get Clear's connection manager to work through Wine.  Those who have the device can try it and help me see if it will work.

---

### Post by alexfish on 2010-08-26
> **mnaines said:**
> I will be getting my Clear Mobile USB (Series S) later today.  Because I run Ubuntu full-time, I am going to do an experiment to see if I can get Clear's connection manager to work through Wine.  Those who have the device can try it and help me see if it will work.

hi 

think someone has already tried wine / did not work

also did some delving / BUT DON'T KNOW IF HEADING IN THE RIGHT DIRECTION

all things from searches point to wimax i2400 

check it searching for clear drivers for the device

on an ubuntu 10.04 there are these drivers

i2400.ko
i2400-sdio.ko
i2400-usb.ko

whilst they appear to be drivers in the kernel

the device may not be recognized / check which drivers are loading when the device is connected

according to the information from the wimax site

you may have to modeprobe the driver

if another driver is loaded then you will have to remove the driver first then 

modprobe the driver

IE:

to remove the wrong driver
where in this case the wrong driver was option(a previous post)
CODE:
sudo modprobe -v -r option

load the wimax drivers
IE:
CODE:

modprobe i2400m-usb

you could monitor the log file viewer/ message to see if the device is recognised and if the drivers are loading

Could also check to see if it Comes up in the Network Manager.

If the device is recognised then there are other tools required

For reading , it also gives instruction for command line use

[http://www.linuxwimax.org/WiMAX-Network-Service-1.3.3-mainline-README.txt](http://www.linuxwimax.org/WiMAX-Network-Service-1.3.3-mainline-README.txt)

also on Ubuntu is madwimax which is a user space for phones with samsung wimax chip and also for a samsung netbook (its built in)

Don't know if it helps / Please ignore if it Don't



Some people are resorting to Virtual Box (>= 3.1.4)

can't help much further since I don't have one of these devices
although it would be interesting to know the outcome

regards

alexfish

PS: if your stuck on commands on how to get the device info etc , let me know I may be able to help in that department

---

### Post by vivek.ahuja@hotmail.com on 2011-12-06
Are there drivers for Wimax + Wifi cards provided by Intel 6150 on ubuntu. Even we can access clear network if we have wimax supported network card.?

---

