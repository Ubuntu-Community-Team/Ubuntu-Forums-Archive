---
title: "HOWTO: Play DVDs"
date: 2007-03-29
forum: Multimedia &amp; Video
---

### Post by geckorock69 on 2007-03-29
This HOWTO is guaranteed to work on my system. Your mileage may vary.

Tested on a fresh install of Feisty (Ubuntu 7.04) Beta after installing all updates and rebooting.

I was able to watch a commercial DVD, including navigating the title menu, extra features, and subtitles.

**Enable Extra Repositories**

The extra repositories were enabled by default in Feisty. If you are using an earlier version of Ubuntu, you may need to enable these repositories.

System -> Administration -> Software Sources

Make sure that Main, Universe, Restricted, and Multiverse are selected, then click on the Close button.

**Add the Medibuntu Repositories**

The Medibuntu repositories include additional multimedia packages that are not otherwise included with Ubuntu.

First, open a terminal:

Applications -> Accessories -> Terminal

Follow the instructions on the Medibuntu website to add the repositories for your release of Ubuntu:

[http://medibuntu.sos-sts.com/repository.php]("http://medibuntu.sos-sts.com/repository.php")

**The Meat and Vegetables**

Open the Synaptic Package Manager:

System -> Administration -> Synaptic Package Manager

Mark the following packages for installation:

libxine-extracodecs
totem-xine
libdvdcss2

Note: installing totem-xine will uninstall totem-gstreamer. This is OK, because totem-gstreamer has its own issues that may yet require years of therapy.

Click on the Apply button.

Note: when the updates are done installing, you may exit Synaptic.

You're done. Enjoy the popcorn.

:popcorn:

---

### Post by WiFi Ed on 2007-03-30
Your how-to worked for me!:)

---

### Post by wolfjb on 2007-04-08
These instructions didn&#8217;t work for me. My laptop is an HP Special Edition L2000 and after following these directions, I still get the message

&#8220;The source seems encrypted, and can&#8217;t be read. Are you trying to play an encrypted DVD without libdvdcss?&#8221;

lspci gives the following:

00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 11)
00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller ATI
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC&#8217;97 Audio Controller (rev 02)
00:14.6 Modem: ATI Technologies Inc ATI SB400 - AC&#8217;97 Modem Controller (rev 02)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc ATI Radeon XPRESS 200M 5955 (PCIE)
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
05:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
05:09.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
05:09.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
05:09.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
05:09.4 Generic system peripheral [0805]: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller

Any hints would be appreciated.

---

### Post by rockingmtranch on 2007-04-10
Thank you.

---

### Post by RxRated on 2007-04-10
I went to the medibuntu site, but when I type in the edgy specific command:
sudo wget [http://medibuntu.sos-sts.com/sources.list.d/edgy.list](http://medibuntu.sos-sts.com/sources.list.d/edgy.list) -O /etc/apt/sources.list.d/medibuntu.list  I get an error saying:
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.

What am I doing wrong?:confused:

---

### Post by chriswyatt on 2007-04-19
Thanks :)

---

### Post by chriswyatt on 2007-04-19
Oh, I have an issue.  Totem can't get past the encryption, it asks if libdvdcss is installed, which it is :( .

> The source seems encrypted, and can't be read. Are you trying to play an encrypted DVD without libdvdcss?

Not sure if this has anything to do with it but I region-hacked my DVD drive a while back.

---

### Post by iWill on 2007-04-19
Thx works great!:popcorn:

---

### Post by TristanMike on 2007-04-20
Thank you, worked for me.

The Support documentation under System didn't work for me.....

The Restricted Formats site on the [wiki](https://help.ubuntu.com/community/RestrictedFormats) didn't work for me.....

Your very simple instructions worked like a charm and as an added bonus, fixed some of the issues that arose with following the above instructions, nicely done :D

---

### Post by nitebum on 2007-04-20
Works great for me, even fixes VLC. Thanks.

---

### Post by rmfought on 2007-04-25
Awesome!  Thanks!

---

### Post by skrimpy on 2007-04-25
thanks :KS

---

### Post by TimJBart on 2007-04-25
Wow thanks for the guide in the first post, worked like a charm!

I had previously tried ubuntuguide.org but t didn't work...this did. 

Cheers

---

### Post by TimJBart on 2007-04-25
One quick question, how do I set the default player that opens when I insert a DVD disk?  Thanks :)

EDIT - Nevermind...the answer is here:  [http://ubuntuforums.org/showpost.php?p=1982510&postcount=3](http://ubuntuforums.org/showpost.php?p=1982510&postcount=3)

---

### Post by ninjabob7 on 2007-05-05
Isn't this illegal in the US due to the DMCA?

---

### Post by SlappyPappy on 2008-04-04
No, this doesn't work.

Still just want to play a DVD.

---

### Post by mdpalow on 2008-04-04
Not sure what happened to the OP. Seems as though he disappeared. :(

Anyway, if you're still having a problem watching a DVD, please click on the link in my signature. My script should do it all for you and work.

Good luck.

---

### Post by vs8 on 2008-04-06
There is no "libxine-extracodec" package in my synaptic after installing the medibuntu repo. This is not my PC, this is my girlfriend's Laptop (Acer Aspire 5050-5410). I really need to make this DVD thing work for her because I want to convince her that Ubuntu is better than XP. 

Man laptop hardware suck's!!! It works so different than desktops. Whenever I install Ubuntu or PCLinucOS on any desktop they just work. But with laptops, I have to waste hours and hours looking for codecs, drivers etc etc. t's so frustrating!!!! I can't imagine Linux in it's begginings. It had to be so hard to get it running properly.


Nevermind I solved the problemusing Xine Movie Player!!!! Thnx :)

---

