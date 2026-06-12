---
title: "how do i install linksys wpc54g v4 in ubuntu 8.04"
date: 2010-10-16
forum: Networking &amp; Wireless
---

### Post by purdurabo33 on 2010-10-16
hey guys i need some help. i just installed 8.04 on a dell inspiron 2500 and am trying to figure out how to get my wireless card(linksys wpc54g v4) to work. i tried to follow a few how-to's but none of them seem to do the trick. i have been playing with ubuntu for awhile now so i am not a complete noobie, but at the same time this is above my head.

here is my lspci so that you can see what is all on my system

```
allen@allen-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82815 815 Chipset Host Bridge and Memory Controller Hub (rev 11)
00:02.0 VGA compatible controller: Intel Corporation 82815 Chipset Graphics Controller (CGC) (rev 11)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801BAM ISA Bridge (LPC) (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801BAM IDE U100 Controller (rev 03)
00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 03)
00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus Controller (rev 03)
00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801BA/BAM AC'97 Audio Controller (rev 03)
01:03.0 CardBus bridge: O2 Micro, Inc. OZ6933/711E1 CardBus/SmartCardBus Controller (rev 01)
01:03.1 CardBus bridge: O2 Micro, Inc. OZ6933/711E1 CardBus/SmartCardBus Controller (rev 01)
01:0b.0 PCI bridge: Actiontec Electronics Inc Mini-PCI bridge (rev 11)
02:04.0 Ethernet controller: Intel Corporation 82557/8/9/0/1 Ethernet Pro 100 (rev 08)
02:08.0 Communication controller: Agere Systems WinModem 56k (rev 01)
03:00.0 Ethernet controller: Linksys, A Division of Cisco Systems [AirConn] INPROCOMM IPN 2220 Wireless LAN Adapter (rev 01)
 
```

and this is what i get with iwconfig


```
allen@allen-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.
```

any help is greatly appreciated!!!

---

### Post by TBABill on 2010-10-16
I just looked up your wireless card and wonder, because it seems to be a newer model, if 8.04 is too old to support it? If you have the ability to create another disk you could try 10.04 since it is also a long term support version but with a much updated kernel from 8.04 and probably a great deal more drivers available.

Edit: searched for it via Google and see reviews as far back as 2004 so I'm probably off on my response.

---

### Post by SeijiSensei on 2010-10-17
Support for these devices has been flaky recently, but the current Maverick kernel works well.  I have WUSB54G v.4 which is now quite stable with the 10.10 kernel.

---

### Post by purdurabo33 on 2010-10-17
that is a great idea, but to tell you the truth i am scared to do that. like i said i put it on an old dell laptop. when i tried to install 10.04 on it wouldn't let me set the resolution correctly, and i had to go back to 8.04 because it had some older tool that are no longer used. i did all this awhile back and when i upgraded to 10.04 it let me keep the resolution setting that i changed in the xorg in 8.04, but i am scared that i will not do that this time. do you think it will let me keep my settings if i upgrade?

and how do i upgrade to 10.10 from inside 8.04.. the update manager says that 10.04 i available but i want to go to 10.10.

---

### Post by purdurabo33 on 2010-10-17
well i got it to work after updating to 10.04 and installing the windows drivers with ndiswrapper. it was easier than i thought at first. now i fell like an *** for even starting this thread. thanx guys

---

