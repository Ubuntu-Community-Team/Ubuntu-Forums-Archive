---
title: "vodafone huawei 4511"
date: 2011-08-02
forum: Networking &amp; Wireless
---

### Post by chumblefish on 2011-08-02
Hi

Anyone know how a newb can get a vodafone huawei 4511 dongle working on ubuntu?

I've spent several hours reading stuff, most of which is way above my head.

I plug it in, set it up in "edit connections". Nothing happens.

It shows up in disk utility twice, as a usb vodaphone storage (huawei) and cd drive (vodafone cd rom)

I switched from puppy to ubuntu because I read that you could just plug dongles into ubuntu and they would be recognized. (Spent many many hours trying to get it working in puppy.)

Help much appreciated.

---

### Post by pdc on 2011-08-03
which version of ubuntu are you using?

which country are you in?

I suspect you have an old version of ubuntu; as it sounds as though your device is not switching; (they are all seen as virtual CD devices first, and then switched to being seen as modems.......................)

if you can open a terminal type

> lsusb

and copy and paste back what you get

---

### Post by chumblefish on 2011-08-03
Hi PDC
 
Thanks for replying.
 
I'm using the latest version of ubuntu, 11.04, 32 bit on a usb stick.
 
I'm using a computer to access the internet in a public library at the moment (in the UK) so can't do the lsusb thing right now. I'll post the results later this evening or tomorrow.

---

### Post by pdc on 2011-08-03
> I'm using a computer to access the internet in a public library at the moment (in the UK) so can't do the lsusb thing right now. 

well ......... you probably could; 

tell us if you are using UNITY .......... icons at the left going down the left-hand edge;

looks like this modem is recent; 

where did you get the 4511 number from ...........

[https://patchwork.kernel.org/patch/1012172/](https://patchwork.kernel.org/patch/1012172/)

the above patch is to switch the device without using usb_modeswitch; I enclose it for information only; 

if you tell us your lsusb data

---

### Post by pdc on 2011-08-03
phew;

to get this working now; will require a little effort it would seem;

(in a few months, not so.................)

you need 

1) usb_modeswitch installed

2) make a special file to tell it about your modem

so you need to see if you are up to it all;

1) go to synaptic (Package Manager) and see if usb_modeswitch is installed ..if not....... go here

[http://packages.debian.org/squeeze/usb-modeswitch](http://packages.debian.org/squeeze/usb-modeswitch)

and choose the i386 package at the BOTTOM of the page; install

2) SPECIAL FILE

go here

[http://henleyregatta.blogspot.com/](http://henleyregatta.blogspot.com/)

if all too hard, ............return modem or find helpful local Linux User Group who can help you .......................

---

### Post by chumblefish on 2011-08-04
Thanks again. I will follow your instructions when I am home again with my laptop. In the meantime, here is the lsusb result. I got it while in lubuntu (I just tried to see if the dongle worked in lubuntu) - I guess the info will be the same as if I had got it in ubuntu. I got the 4511 number from the label on the dongle. For the link to the patch, I downloaded the mbox and patch files. I will try to open them/run them in ubuntu this evening and see what happens. As for the link 2), I already went there and gave up at the

"Create the file  [FONT=&quot]/etc/usb_modeswitch.d/12d1:14b7" [/FONT]

part, as I didn't know how to creste a file. I will read the page again if the patch doesn't work and see if I can work it out.

ubuntu@ubuntu:~$ lsusb
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 12d1:14b7 Huawei Technologies Co., Ltd. 
Bus 002 Device 002: ID 03f0:5a07 Hewlett-Packard 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 0c45:63fa Microdia 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
ubuntu@ubuntu:~$

---

### Post by JFDee on 2011-08-05
No need to start from zero.

Andrew Bird (who also contributed the kernel patch) has provided this device and several others to the usb_modeswitch "data base".

See
[https://github.com/digidietze/usb-modeswitch-data/blob/master/usb_modeswitch.d/12d1:14b7](https://github.com/digidietze/usb-modeswitch-data/blob/master/usb_modeswitch.d/12d1:14b7)

You can go ahead and do stuff yourself (and learn a thing or two on the way) - or you can wait until tonight when I'm going to release a new program and data package version of usb_modeswitch containing a row of new configurations including your modem.

****

---

### Post by JFDee on 2011-08-05
A note about the kernel patch mentioned above:

There might be a misconception about what this patch will be doing. It will **not** change the mode from install mode to modem mode; it will just add the ID of the modem mode to the serial driver. That means that usb_modeswitch does not have to load and bind the driver after switching, because the driver will know the device and act without any external trigger.

So you will still need to mode-switch the device. If the kernel patch is **not** installed, usb_modeswitch will notice that no driver is taking care of the modem after switching and will spring into action. The result is basically the same as with the kernel patch.

****

---

### Post by pdc on 2011-08-08
this is tremendous; many thanks

---

