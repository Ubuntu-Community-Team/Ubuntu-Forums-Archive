---
title: "T-mobile Rocket 2.0 not flipping"
date: 2010-09-21
forum: Networking &amp; Wireless
---

### Post by sgtron on 2010-09-21
I just picked up a 3g modem from T-mobile that I cannot get to work with 10.04

Inserting the device and running lsusb gives 

Bus 002 Device 002: ID 19d2:1201 ONDA Communication S.p.A. 

I installed usb-modeswitch but I don't know how to configure the usb-modeswitch.conf  

I know I need to provide the default vendor and product as what is given above vendor=0x19d2 and product=0x1201 but I don't know what to put for the target vendor and product.  I'm sure vendor is the same 0x19d2, but the product.. I don't know what to put for the target product so the usb storage will flip to usb modem.

Or maybe I'm completely wrong about how I'm going about this.

I've researched this numerous places:

[http://forums.t-mobile.com/t5/Laptop-Stick-Help/FYI-Rocket-USB-Laptop-Stick-Huawei-UMG1831-Works-Under-Ubuntu-10/td-p/377151](http://forums.t-mobile.com/t5/Laptop-Stick-Help/FYI-Rocket-USB-Laptop-Stick-Huawei-UMG1831-Works-Under-Ubuntu-10/td-p/377151)

and

[http://gutsywww.ubuntuforums.org/showthread.php?t=1572572](http://gutsywww.ubuntuforums.org/showthread.php?t=1572572)

and I can see the basic idea of how to proceed, but I think I'm stuck at flipping the device from storage to modem mode.

I've got 14 days to return this thing if I can't get it to work.  I'm willing to mess around for all 14 of them if we can get this to work and help out any other ubuntu users who want to buy this device.

---

### Post by ambush276 on 2010-09-22
same problem... im want to do the exact same thing and i have done exactly what you have done with those guides..

i cant figure it out either

---

### Post by ambush276 on 2010-09-22
ok i got one step further.. tell me if you can work with this..


ok so at the step where you "safely remove.."

just hit "eject" and DO NOT remove the tmobile rocket 2.0 from the usb port.

then run lsusb again.. i got for the product 1203...

and when i went to modem i found the Tmobile Rocket 2.0 there.


on the other hand i could not get it to connect to the internet.... but maybe you can help from there?

---

### Post by sgtron on 2010-09-29
Crap.  Sorry I missed this post.  I took back my modem to t-mobile.. They charged me for the days I "used" it but at least I won't get stuck with tech I can't use.. 

Ok, you're smart.  After I read your post I remembered reading something about that same thing... ejecting will reveal some different data.. smart guy you!  

Here's what I would try if I still had my own modem... I think you need to set up usb_modeswitch.conf with the information you derived from your little experiment.  I think one of those links I posted had some info on that.. 

Let me know if that helps any.. I'm willing to actually do some research if this gets you anywhere.

---

### Post by sgtron on 2010-09-29
Here.  Set it up like in this post:

[http://www.blogcatalog.com/blog/iwrite-2/dbbfb38ae5ef9ccef8540aad7f9edbd6](http://www.blogcatalog.com/blog/iwrite-2/dbbfb38ae5ef9ccef8540aad7f9edbd6)

Then use connection manager to follow through.. see if *that* works.

---

### Post by mgove on 2010-09-29
I got it to work after much poking at it. (I'm connected on it right now.)

For the usb_modeswitch stuff. 
/etc/usb_modeswitch.d/19d2:1201
#begin
DefaultVendor=  0x19d2
DefaultProduct= 0x1201

TargetVendor=   0x19d2
TargetProduct=  0x1203

CheckSuccess=20

MessageContent="5553424392020000000000000000061B000000020000000000000000000000"
#end

In /lib/udev/rules.d/40-usb_modeswitch.rules
add a line:
ATTRS{idVendor}=="19d2", ATTRS{idProduct}=="1201", RUN+="usb_modeswitch '%b/%k'"

That will get the modeswitch to work.

There seems to be an issue with modem-manager vs. the rocket 2.
It harfs when talking to it, the modem errors when given the AT+ZPAS command. 

I found simply removing the /usr/lib/ModemManager/libmm-plugin-zte.so module makes it identify as a standard GSM modem and it starts working. I haven't dug too much into trying to fix the module itself. 

I also started using the latest network manager from
[https://launchpad.net/~network-manager/+archive/trunk](https://launchpad.net/~network-manager/+archive/trunk)

It seems to work a bit better with the GSM modems.  Signal strength and provider are shown.  It still has the zte modem issue though. But the same temporary fix works.

---

### Post by sgtron on 2010-09-29
MGOVE, you rule!  

I guess I should have kept my modem for a few more days.. Anyway, at least we have this documented for everyone who comes after to help them get it to work for themselves.

As for me, I'm thinking of getting a G2 from T-mobile and tethering that so I don't have to pay 2 bills...

---

