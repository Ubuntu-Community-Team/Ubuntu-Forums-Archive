---
title: "ATI hardware acceleration problem"
date: 2008-06-14
forum: Multimedia Software
---

### Post by Dbugger on 2008-06-14
Hello.

When I activate the ATI hardware acceleration, and I restart the computer, i get a black screen, instead of the login.

Im using Hardy. this is my lspci

> 00:00.0 Host bridge: ATI Technologies Inc Unknown device 5a31 (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 83)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller (rev 80)
00:14.2 Audio device: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200M]
02:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:07.0 Ethernet controller: Atheros Communications Inc. AR2413 802.11bg NIC (rev 01)
02:09.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b4)
02:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 1
02:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller
02:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 09)
02:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 04) 

Please help!

---

### Post by overdrank on 2008-06-14
> **Dbugger said:**
> Hello.

When I activate the ATI hardware acceleration, and I restart the computer, i get a black screen, instead of the login.

Im using Hardy. this is my lspci



Please help!

Hi and please do not make multiple post on the same issue
[http://ubuntuforums.org/showthread.php?t=829062](http://ubuntuforums.org/showthread.php?t=829062)
If you reach a black screen you can try and use the keys alt, ctrl, F1 to reach the command line and login. Then use the command to reconfigure your xorg ```
sudo dpkg-reconfigure -phigh xserver-xorg
``` the use the command sudo reboot and hopefully this will get you back to the desktop.

---

### Post by Dbugger on 2008-06-14
> **overdrank said:**
> Hi and please do not make multiple post on the same issue
[http://ubuntuforums.org/showthread.php?t=829062](http://ubuntuforums.org/showthread.php?t=829062)
If you reach a black screen you can try and use the keys alt, ctrl, F1 to reach the command line and login. Then use the command to reconfigure your xorg ```
sudo dpkg-reconfigure -phigh xserver-xorg
``` the use the command sudo reboot and hopefully this will get you back to the desktop.

Sorry about the double post. I just didnt know what was the right cattegory to ask.

The problem is not to go back. In recovery mode, i choose "xfix" and I recover it... what i was asking is for a solution to get hardware acceleration.

---

### Post by overdrank on 2008-06-14
> **Dbugger said:**
> Sorry about the double post. I just didnt know what was the right cattegory to ask.

The problem is not to go back. In recovery mode, i choose "xfix" and I recover it... what i was asking is for a solution to get hardware acceleration.

Ok sorry and I have had no luck with assistants on the hardware acceleration with that model. :(

---

