---
title: "TerraTec H7 driver/firmware"
date: 2009-08-04
forum: Mythbuntu
---

### Post by jensk on 2009-08-04
I have bought a new Terratec H7 USB DVB-T/C encoder [http://www.terratec.net/en/products/TerraTec_H7_91101.html]("http://www.terratec.net/en/products/TerraTec_H7_91101.html")
A really nice device with build in CI slot for CAM.

I can get the pc to recognize the USB device - lsusb shows 0ccd:10a3 TerraTec device.
I do not get any further.
I have tried lsmod to se if any DVB modules gets loaded but none are. 
/var/log/messsages shows no sign of any DVB or /dev/video- devices except the ones belonging to the allready installed PVR-500 card.

Does anybody know which driver and firmware this devices uses? I have written to TerraTec to get this information but haven't had any answer yet.

My current version is Mythbuntu 8.10 kernel version 2.6.27.14.

If upgrading to Mythbuntu version 9.04 with kernel version 2.6.28-14 would upply the drivers i would be happy to upgrade/update?

Can someone please help me with some more information on how to get this device running?
Thanks JK

---

### Post by realzippy on 2009-08-04
em28xx Chipset someone in a german forum said.Currently not running...
[http://www.vdrportal.de/board/thread.php?postid=832252](http://www.vdrportal.de/board/thread.php?postid=832252)

---

### Post by jensk on 2009-08-05
Thank you for the answer.

I am looking for an USB encoder for DVB-C/T with a CI/CAM port. The reason i am looking for USB is that i have no more free PCI slots in my backend server:
1 Gbit network
I PCI Sata card
1 PVR-500

Thats why i need a USB device. I know of one more the TechnoTrend CT-3650 but i can't find any list of if it will work.

Which USB DVB-C/T encoders with a CI/CAM slot do work with the current version of Mythbuntu.

The alternative is a combo analog DVB-C/T but i havent found any with a CI/CAM slot.

Any suggestions on good working devices will be appreciated.

---

### Post by realzippy on 2009-08-05
Sorry,no ideas.
If you find one that works,please let us know!!

---

### Post by jensk on 2009-08-05
Thanks for the quick answer.
My major problem is aparently that there is no up-to-date list over alle teh different devices and not all manufacturers list if their device will work under Linux.

I have tried the mythtv wiki and such but the information there seems pretty old.

Do you have a ref for a source of such a list?

---

### Post by inzpektor on 2009-11-22
If you wanna know what HW is supported by the Linux driver stack, you should take a look at the video4linux wiki: [http://www.linuxtv.org/wiki/index.php/DVB-C_USB_Devices](http://www.linuxtv.org/wiki/index.php/DVB-C_USB_Devices)

Ufortunately, the TerraTec H7 is not supported.

---

### Post by johnknuhtsen on 2009-12-08
> **inzpektor said:**
> If you wanna know what HW is supported by the Linux driver stack, you should take a look at the video4linux wiki: [http://www.linuxtv.org/wiki/index.php/DVB-C_USB_Devices](http://www.linuxtv.org/wiki/index.php/DVB-C_USB_Devices)

Ufortunately, the TerraTec H7 is not supported.

It should be possible to use the Sundtek drivers.
[http://support.sundtek.de/index.php?topic=4.0](http://support.sundtek.de/index.php?topic=4.0)

---

### Post by dirk44 on 2010-01-20
> **johnknuhtsen said:**
> It should be possible to use the Sundtek drivers.
[http://support.sundtek.de/index.php?topic=4.0](http://support.sundtek.de/index.php?topic=4.0)

Caution this doesn't work with it I tried it... I finally decided to buy such a Sundtek DVB-C/DVB-T/ATV USB device .. it works well but the driver does not work with the Terratec device!!!

---

### Post by The_old_man on 2011-04-11
There's now a semi-official download from terratec' linux page for the H7:

[http://linux.terratec.de/tv_en.html](http://linux.terratec.de/tv_en.html)

Does anybody know if it works?

---

### Post by Invisan on 2011-04-12
Well it kinda works

This is what ive done to install it 


1) apt-get install mercurial (otherwise the hg command wont work)
2) wget [http://linux.terratec.de/files/TERRATEC_H7/20110323_TERRATEC_H7_Linux.tar.gz](http://linux.terratec.de/files/TERRATEC_H7/20110323_TERRATEC_H7_Linux.tar.gz)
3) tar -xvvf ./20110323_TERRATEC_H7_Linux.tar.gz
4) cd 20110323_TERRATEC_H7_Linux
5) hg clone [http://mercurial.intuxication.org/hg/s2-liplianin-ahead](http://mercurial.intuxication.org/hg/s2-liplianin-ahead)
6) hg clone [http://mercurial.intuxication.org/hg/s2-liplianin](http://mercurial.intuxication.org/hg/s2-liplianin)
7) mv ./dvb-usb/* ./s2-liplianin/linux/drivers/media/dvb/
8) mv ./frontends/* ./s2-liplianin/linux/drivers/media/dvb/
9) mv dvb-usb-az6007-03.fw /lib/firmware/
10) mv terratec_h7.patch ./s2-liplianin
11) cd s2-liplianin
12) patch -p1 terratec_h7.patch (This step is not working for me so i ended it after around 50 minutes with strg-c and got on to step 13)
13) make
13a)  if you experience an error message with FIREDTV type this sed -i  's/CONFIG_DVB_FIREDTV=m/CONFIG_DVB_FIREDTV=n/' ./v4l/.config
14) make install
15) Your done

but i still cant use the card though

---

### Post by ZeroOneB on 2011-04-18
> **realzippy said:**
> em28xx Chipset someone in a german forum said.Currently not running...
[http://www.vdrportal.de/board/thread.php?postid=832252](http://www.vdrportal.de/board/thread.php?postid=832252)

It's seems to be no em28xx chipset 
terratex semiofficial site says under Hardware that the card uses following:
 
Micronas DRX3913
					Microtune MT2063
Source is (again) [http://linux.terratec.de/tv_en.html](http://linux.terratec.de/tv_en.html) 

No idea if this helps anyone and I'm a complete Noob. Would be great if someone could have a (second?) look at it.

Greez Zero

---

