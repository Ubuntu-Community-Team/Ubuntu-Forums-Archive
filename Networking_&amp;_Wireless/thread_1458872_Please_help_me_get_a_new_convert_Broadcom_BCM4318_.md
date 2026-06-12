---
title: "Please help me get a new convert: Broadcom BCM4318 not working"
date: 2010-04-20
forum: Networking &amp; Wireless
---

### Post by Arthur_D on 2010-04-20
Hi folks, I'm trying to help a friend with his Acer Aspire 5003 WLMi computer, and if you guys can't help me get this to work, I have to resort to reinstalling Windows XP on his computer.

I've tried with f34cutter and the Windows driver with ndiswrapper, and both ways should work (many others seems to have got it working), but I haven't.

Please help me get this to work - I can't keep up with this much longer (he wants to have his laptop back someday), and I will post the relevant info as soon as you need it.

YES WE CAN! ;)

---

### Post by johngreth on 2010-04-20
Karmic or Lucid?

---

### Post by Arthur_D on 2010-04-20
Karmic. Haven't tested Lucid yet on his laptop.

---

### Post by johngreth on 2010-04-20
according to [the wiki]("https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4318"), the only thing that works is [this]("http://sampbar.com/2009/04/broadcom-bcm4318-ubuntu-intrepid/")

---

### Post by Arthur_D on 2010-04-21
WHAT THE LOL!!! IT FINALLY WORKED!!!
johngreth, I cannot thank you enough for that link! :D :D :D

You have just saved me and my friend from fiddling around with Windows XP. :lolflag:

---

### Post by kaze11 on 2010-06-10
The download on the link seems to have gone. Any idea of what it was and where else to find it?

---

### Post by bkratz on 2010-06-10
> **kaze11 said:**
> The download on the link seems to have gone. Any idea of what it was and where else to find it?



didn't actually download it, but the link in this posting still seems active and the description seems to match--hopefully it will help.

[http://ubuntuforums.org/showpost.php?p=713108&postcount=5](http://ubuntuforums.org/showpost.php?p=713108&postcount=5)

---

### Post by kaze11 on 2010-06-13
Thanks, I'm hitting problems though... The guide talks of needing a ini but the driver file is a exe. How do I get this installed?
When I tried booting from a CD some thing appeared up near the clock giving me the option to install some sofware for helping with 3rd party wireless drivers. WIth my install though there's no such thing present. 
I'm growing inreasingly clueless here and being really tempted to put xp back on this computer (that things run...jerky too doesn't help)

---

### Post by purelinuxuser on 2010-06-13
> **kaze11 said:**
> Thanks, I'm hitting problems though... The guide talks of needing a ini but the driver file is a exe. How do I get this installed?
When I tried booting from a CD some thing appeared up near the clock giving me the option to install some sofware for helping with 3rd party wireless drivers. WIth my install though there's no such thing present. 
I'm growing inreasingly clueless here and being really tempted to put xp back on this computer (that things run...jerky too doesn't help)

No need to use ndiswrapper :) Just plug into Ethernet, open Synaptic Package Manager (System > Administration), install "b43-fwcutter," be sure the checkbox that says "Automatically download and install firmware?" is **checked**, and reboot.

*Can't tell you how many times I've give those instructions out:lolflag:*

---

### Post by kaze11 on 2010-06-14
Wow, cool,it seems to have sorted itself out with that, somehow. Mysteriously :s
Thanks!

Any clue on the jerkyness though? Any similar methods for graphis/mainboard/whatever drivers?

---

### Post by purelinuxuser on 2010-06-14
> **kaze11 said:**
> Wow, cool,it seems to have sorted itself out with that, somehow. Mysteriously :s
Thanks!

I knew what was going on. :p Linux has drivers built in for your wireless card, but they need proprietary firmware to operate which is not distributed with Ubuntu due to licensing issues.  So it's left up to the user to download/install the firmware manually, which b43-fwcutter does for you (only drawback is you need an Internet connection).

> **kaze11 said:**
> Any clue on the jerkyness though? Any similar methods for graphis/mainboard/whatever drivers?

Jerkiness?  Are you talking about slowness with your video card?  You may need to install the proprietary drivers for it (System > Administration > Hardware Drivers).  If you see none open a Terminal (Applications > Accessories > Terminal) and post the output of the following command:
```
lspci
```

---

### Post by kaze11 on 2010-06-15
00:00.0 Host bridge: ATI Technologies Inc Device 5a31 (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:12.0 IDE interface: ATI Technologies Inc IXP SB400 Serial ATA Controller (rev 80)
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 82)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller (rev 80)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 80)
00:14.6 Modem: ATI Technologies Inc SB400 AC'97 Modem Controller (rev 80)
01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200M]
09:01.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controller
09:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
09:04.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

---

### Post by purelinuxuser on 2010-06-15
> **kaze11 said:**
> 00:00.0 Host bridge: ATI Technologies Inc Device 5a31 (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:12.0 IDE interface: ATI Technologies Inc IXP SB400 Serial ATA Controller (rev 80)
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 82)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller (rev 80)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 80)
00:14.6 Modem: ATI Technologies Inc SB400 AC'97 Modem Controller (rev 80)
** 01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200M]**
09:01.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controller
09:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
09:04.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

I'm sorry, but you have an old ATI graphics card that is no longer supported by ATI :( Good news, though, there are open-source drivers in the works that provide good 2D acceleration and fair 3D acceleration.  I'm afraid I can't help you with any problems related to graphics, you may want to post a new thread about this issue under the Hardware & Laptops subsection.

---

