---
title: "Wireless wont connect with Ubuntu 12.04"
date: 2012-09-01
forum: Networking &amp; Wireless
---

### Post by dkb12 on 2012-09-01
I have a Compaq Presario 2100 and It will detect my Wireless but will not connect. When I check for available drivers it dosent find any. Can someone please help. Thanks

---

### Post by ajgreeny on 2012-09-01
Open a terminal and show the output from command ```
lspci
```, which will let us know what the wireless card chipset is.

---

### Post by dkb12 on 2012-09-01
lskatelynsmommy@katelynsmommy-laptop:~$ lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] nee ATI RS100 AGP Bridge [IGP 320M] (rev 13)
00:01.0 PCI bridge: Advanced Micro Devices [AMD] nee ATI PCI Bridge [IGP 320M] (rev 01)
00:02.0 USB controller: ALi Corporation USB 1.1 Controller (rev 03)
00:06.0 Multimedia audio controller: ALi Corporation M5451 PCI AC-Link Controller Audio Device (rev 02)
00:07.0 ISA bridge: ALi Corporation M1533/M1535/M1543 PCI to ISA Bridge [Aladdin IV/V/V+]
00:08.0 Modem: ALi Corporation M5457 AC'97 Modem Controller
00:09.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 02)
00:0a.0 CardBus bridge: O2 Micro, Inc. OZ601/6912/711E0 CardBus/SmartCardBus Controller
00:0c.0 FireWire (IEEE 1394): Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link)
00:10.0 IDE interface: ALi Corporation M5229 IDE (rev c4)
00:11.0 Bridge: ALi Corporation M7101 Power Management Controller [PMU]
00:12.0 Ethernet controller: National Semiconductor Corporation DP83815 (MacPhyter) Ethernet Controller
01:05.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RS100 [Radeon IGP320M]

---

### Post by dkb12 on 2012-09-01
I have the wireless drivers installed. I have ndiswrapper also. Can someone please help me? Im new to Ubuntu. Thanks

---

### Post by ajgreeny on 2012-09-02
See what happens if you install **b43-fwcutter** if it is not already installed. Broadcom can be a bit of a problem some times, though I don't have a broadcom adapter in my machine, so can not give you any personal experience to go on.

---

### Post by dkb12 on 2012-09-02
I checked and its already installed.

---

### Post by Bowskikorsitoff on 2012-09-19
I have a Dell D610 which I have just dual booted with Ubuntu 12.04 LTS.

I get Network->Wireless-> "Firmware missing" in Ubuntu but wireless  OK with XP.

Using a terminal the Broadcom device is: BCM4306 [14e4:4324] rev 03.

I tried "sudo apt-get install firmware-b43-installer" and got "An unsupported BCM4301, BCM4306 or BCM4306/2 device was found. Use b43legacy firmware (firmware-b43legacy-installer package) instead. Aborting."

I then removed this half installed package.

Then I did "sudo apt-get install firmware-b43legacy-installer".

Appeared to install but I still get "Firmware missing".

I've tried rebooting but no good.

Come on Linux people what do I do now apart from retreating to XP. (Brand new Linux newbie)

---

