---
title: "TV Tuners on the cheap..."
date: 2009-12-28
forum: Multimedia Software
---

### Post by aristotlewilde on 2009-12-28
So I am a sucker for hardware "deals".  If I can get something for $20 or so, you better believe I am going to try it.

In the last month, I have picked up two different USB Stick TV Tuners with the longshot chance that one will be supported in Ubuntu.  The way I see it, if they aren't my Windows 7 box can always use another tuner for Media Center.

So I bought an Asus MyCinema U3100mini (US version), and a Mygica HDTV Stick (Hybrid u6012a).  Neither "just worked" on first try in Ubuntu.  

Has anyone got experience with either of these?  The latter shows up in LSUSB as a Syntek Semiconductor device.  

This is not a "must have" setup, but it sure would be cool to watch TV on my Linux PC!

---

### Post by xc3RnbFO8P on 2009-12-28
Read this:
[http://www.mythtv.org/wiki/Asus_My_Cinema_U3100_mini]("http://www.mythtv.org/wiki/Asus_My_Cinema_U3100_mini")

---

### Post by gsmanners on 2009-12-28
The first one has a MythTV page you might be interested in:

[http://www.mythtv.org/wiki/Asus_My_Cinema_U3100_mini](http://www.mythtv.org/wiki/Asus_My_Cinema_U3100_mini)

EDIT: Yay! Simo posted again. :P

---

### Post by aristotlewilde on 2009-12-28
I had seen that.  Having trouble following those instructions,  It seems the files in Step 2 have been moved.

More than likely, I will just get a Linux Friendly card.  This one can go to the missus.

---

### Post by kv2000in on 2009-12-29
Can you post the vendor IDs and the  Product IDs for these two products?

---

### Post by aristotlewilde on 2009-12-30
> **kv2000in said:**
> Can you post the vendor IDs and the  Product IDs for these two products?

Sorry.  Where would these be located?  Is this it below?  This is for the Mygica device.

Bus 001 Device 006: ID 05e1:0400 Syntek Semiconductor Co., Ltd

---

### Post by kv2000in on 2010-01-01
Vendor ID:05e1
Product ID:0400 .

Apparently, there are multiple versions of USB TV tuners floating around in the market, all with same ViD and PiD using different sets of tuners,demodulators and USB bridges.
For example , one version has these chips :-     
*  Philips TDA18271 (tuner & analog demodulator) ?
* Auvitek AU8522 demodulator (A/D)
* Auvitek AU0828 (USB bridge)  

[http://linuxtv.org/wiki/index.php/Sabrent_TV-USBHD](http://linuxtv.org/wiki/index.php/Sabrent_TV-USBHD)
[http://linuxhacksandfixes.blogspot.com/2009/05/sabrent-tv-dgusb.html](http://linuxhacksandfixes.blogspot.com/2009/05/sabrent-tv-dgusb.html)

The other one has :
AU0828A (USB Bridge)
AU8522AA (Demodulator)
MT2131F (Tuner)

[http://www.linuxtv.org/pipermail/linux-dvb/2008-November/030537.html](http://www.linuxtv.org/pipermail/linux-dvb/2008-November/030537.html)
[http://marc.info/?l=linux-dvb&m=122472907625204&w=2](http://marc.info/?l=linux-dvb&m=122472907625204&w=2)

For getting it to work, we will have to find out which set of chips are present on this version (i.e. Mygica ). I know that tuners TDA18271 and MT2131F are supported . 
If you could confirm the chips present on this device, It will be helpful.

Also, If you could post your dmesg output ( user@user$ dmesg ) after attaching the device.
Thanks so much.

---

### Post by gdselzer on 2010-03-25
So I picked up the Asus MyCinema U3100mini mentioned above and I'm not getting any love.

lsusb provides:

```
Bus 001 Device 004: ID 0b05:1747 ASUSTek Computer, Inc.
```

How do I figure out which chipsets this has?  I've been googling the device id but haven't found much.

Can anyone help me with next steps on this?

Thanks

---

### Post by dbbslc on 2010-04-13
I have been trying to get my Mygica stick to work without success.
I modified a current au0828-cards.c driver from the ubuntu linux-source for 2.6.31-20 as described in the [http://linuxhacksandfixes.blogspot.com/2009/05/sabrent-tv-dgusb.html](http://linuxhacksandfixes.blogspot.com/2009/05/sabrent-tv-dgusb.html) page. After modprobing it I only get the kernel messages of 
usb 2-6: new high speed USB device using ehci_hcd and address 9
usb 2-6: configuration #1 chosen from 1 choice

Nothing else. Udev (or whatever should create a device) -- supposedly /dev/video0 per the error message xawtv give do not create the device.
Has anyone else got this working yet and if so what were the steps you took to do it?

BTW - the device ids are: ID 05e1:0480

Thanks.

---

### Post by tdayal on 2010-04-16
I've been quite unsuccessful too. 

Mygica a680b
USB ID: 05e1:0480

I've edited the au0828-cards.c like the tutorial said, but when I make I get:

make[2]: Entering directory `/usr/src/linux-headers-2.6.31-20-generic'
  CC [M]  /home/USERNAME/teledongle-65d8b048c989/v4l/tuner-xc2028.o
/home/tushar/teledongle-65d8b048c989/v4l/tuner-xc2028.c:49: error: 'FIRMWARE_NAME_MAX' undeclared here (not in a function)
make[3]: *** [/home/USERNAME/teledongle-65d8b048c989/v4l/tuner-xc2028.o] Error 1
make[2]: *** [_module_/home/USERNAME/teledongle-65d8b048c989/v4l] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.31-20-generic'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/USERNAME/teledongle-65d8b048c989/v4l'
make: *** [all] Error 2


Any ideas?

---

### Post by Directive 4 on 2010-04-16
my advice, forget mythtv, you'll save yourself a world of hurt.

try TVtime for the software center, prob work straight away,

---

### Post by tdayal on 2010-05-10
*Bump*

Still getting that make error with teledongle...

---

