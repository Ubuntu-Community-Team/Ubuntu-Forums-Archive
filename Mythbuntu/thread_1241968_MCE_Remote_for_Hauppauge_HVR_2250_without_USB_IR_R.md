---
title: "MCE Remote for Hauppauge HVR 2250 without USB IR Receiver"
date: 2009-08-16
forum: Mythbuntu
---

### Post by EternalStudent on 2009-08-16
I'm new to Ubuntu and MythTV, but loving it.  I'm currently running Ubuntu with mythTV installed on it (mythbuntu distro didn't play well with my ATI card).

I followed these instructions to get my Hauppauge 2250 tuner working: [http://ubuntuforums.org/showpost.php?p=7429560&postcount=47](http://ubuntuforums.org/showpost.php?p=7429560&postcount=47) (thanks, worked perfectly)   The tuner came with a MCE remote: [http://www.newegg.com/Product/Product.aspx?Item=N82E16815116036](http://www.newegg.com/Product/Product.aspx?Item=N82E16815116036)  Recent reviews on newegg mentioned trouble with the new non-usb receiver in windows.

Apparently Hauppage used to include a USB IR Receiver, but now has switched to a IR sensor on the blaster wire. [http://www.hauppauge.com/site/products/data_hvr2250.html](http://www.hauppauge.com/site/products/data_hvr2250.html)

I've selected several options for IR remote in the mythbuntu setup section, however none seem to work. Am I missing something?   

Any ideas would be appreciated. Thanks!

---

### Post by LowSky on 2009-08-17
I dont know If i can help but, could you post the output of this command from a terminal.

```
lspci
```

I want to see if its is showing up

---

### Post by EternalStudent on 2009-08-17
lspci:

00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 10)
00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 10)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: ATI Technologies Inc RV770 [Radeon HD 4850]
01:00.1 Audio device: ATI Technologies Inc HD48x0 audio
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
03:00.0 Multimedia controller: Philips Semiconductors Device 7164 (rev 81)

lsusb:
Bus 001 Device 002: ID 148f:2870 Ralink Technology, Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
(didn't really think it would show up here.)

more pics:
[http://www.hauppauge.com/pics/hvr2250-contents-diagram-b.jpg](http://www.hauppauge.com/pics/hvr2250-contents-diagram-b.jpg)

Thanks.

---

### Post by nasha on 2009-08-17
The HVR-2200/2250 Driver is still experimental, and may not yet include support for the onboard IR connection. I haven't seen this refernced anywhere in regards to being supported by Steve Toth's driver. It might be worth getting into contact with Steve to see the level of support for it.

Definitely seems like a driver issue to me. due to the fact that it hasn't turned up in lspci or lsusb. Might also be worth taking a look at */etc/lirc/lircd.conf* & *hardware.conf*, as well as output of *ls /dev | grep lirc* && *ps aux|grep lirc* just to make sure lirc is operating properly also.

Cheers,
Nasha

---

### Post by clutzer on 2010-01-28
Hey, I just picked up this card randomly at Micro Center and as of 9.10 ubuntu (mythbuntu) there isn't support for this card yet.  I had to manually compile v4l-dvb as you did.  That gets the tuners working (at least somewhat, I'm having all sorts of reliability problems).  But, I suspect IR is going to be more of a LIRC issue than a V4L-DVB issue, at least in the present state of things.

I have an ancient Hauppage PVR-250 in my system as well which has the exact same IR interface (very similar cable, same plug, different remote model).  I believe I see the IR receiver get recognized in dmesg:

[FONT="Courier New"][    9.368904] tveeprom 0-0050: has no radio, has IR receiver, has no IR transmitter
[   10.351397] input: cx88 IR (pcHDTV HD3000 HDTV) as /devices/pci0000:00/0000:00:1e.0/0000:06:02.0/input/input5
[   10.351448] Creating IR device irrcv0
[   11.312795] input: em28xx IR (em28xx #0) as /devices/pci0000:00/0000:00:1a.7/usb1/1-2/input/input7
[   11.312845] Creating IR device irrcv1
[   16.340742] lirc_dev: IR Remote Control driver registered, major 61 
[   16.528976] lirc_i2c: chip 0x0 found @ 0x18 (Leadtek IR)
[   20.790256] tveeprom 3-0000: has radio, has IR receiver, has no IR transmitter[/FONT]

I think the tveeprom 3-0000 is the HVR-2250 and tveeprom 0-0050 is the old PVR-250.  To make things even more difficult on my system, my HD3000 and my Pinnacle USB both have IR receivers that register as irrcv0/1 which are totally unrelated to LIRC as far as I can tell.

I currently can no longer get any of my Hauppage IR remotes to work, so I am very interested in seeing if anybody has any information to add to this thread.

Oddly enough, I can not for the life of me get my original PVR-250 remote to work anymore (/dev/lirc0).  And as I eluded to before, it's giving me a headache to debug but my Hauppage remote causes irrcvX events to go off (9 increases volume, 3 decreases volume).

I got so fed up I installed Windows 7 and Media Center and everything just worked, flawlessly.  I really hope I don't have to convert because there are a small number of features that I don't want to lose from MythTV.

Thanks everyone.

C.

---

### Post by juicedM3 on 2010-02-04
clutzer, I was recently looking around Steven Toth's site hoping there was new information on the HVR-2250 with regards to the onboard IR remote.  He had a couple of interesting post that may help you.  The posts basically say that the cx88-IR driver is blacklisted by hald   [http://www.kernellabs.com/blog/?p=1355]("http://www.kernellabs.com/blog/?p=1355").  So I searched his site some more to find out how to unblacklist the driver and came across this post [http://www.kernellabs.com/blog/?p=1309]("http://www.kernellabs.com/blog/?p=1309").  I don't know if that will help you or not with your other IR receivers/remotes.  My HVR-2250 only shows this one line associated to the IR receiver and nothing else:

[   21.960365] tveeprom 1-0000: has radio, has IR receiver, has no IR transmitter

So that looks to match your tveeprom 3-000.

---

### Post by jjwest85 on 2010-02-06
I have the same tv tuner card and remote as the original poster.  I also get the "tveeprom" line from "dmesg | grep tveeprom".  I read through the Devin Heitmueller's posts about the remote and cx88 blacklist problem, but his was a PCTV 800i from Hauppauge. Does this relate back to the 2250's remote issues?  

I also found on the wiki for mythtv that the remote is not yet supported from the driver: 

[http://www.mythtv.org/wiki/Talk:Hauppauge_HVR-2250](http://www.mythtv.org/wiki/Talk:Hauppauge_HVR-2250)

is this true?

---

### Post by LaurentD on 2010-02-16
Also looking at getting the MCE remote working with the cables provided with the HVR 2250 card...
Would buying a usb IR receiver the best option at this point?
Any recommendation on what to get?

Thanks

---

### Post by winewood on 2010-05-04
I found it!
 
[http://www.siig.com/ViewProduct.aspx?pn=CE-000022-S1](http://www.siig.com/ViewProduct.aspx?pn=CE-000022-S1)
 
This enabled my black MCE remote from my Hauppauge 2250 to work. Once I plugged it in the /dev/lirc0 appeared, and I mapped my frontend options to it, then presto!
 
I paid $39 for it for the SIIG kit with remote. The USB receiver allowed the Hauppauge remote to work AND the SIIG remote to work with the same exact options. Now you can have 2 remotes laying around the house that can work without changing any configs.
 
Remember, your remote won't work until that can show up using the usb device appears in your output. See "Formosa" line ```
 lsusb
Bus 002 Device 002: ID 147a:e03c Formosa Industrial Computing, Inc. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

``` The part information is: "USB Receiver" model: IR605A for the USB portion alone.
 
I must add: I had to go to the Myth MCE remote pages, find the drivers for the MCE remotes and add them.  Once I installed them, I was able to go into the Myth configuration tool and find MCE remotes there.  Remember to install your Hauppauge driver as well.  This bad boy isnt exactly plug-n-play with the Mythbuntu package for 10.4 64bit.

---

