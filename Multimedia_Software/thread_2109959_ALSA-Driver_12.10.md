---
title: "ALSA-Driver 12.10"
date: 2013-01-29
forum: Multimedia Software
---

### Post by davidbuntu on 2013-01-29
Hey everyone. I've been off an on ubuntu for a few years now (since 09.04 or something like that). 

I had origanlly installed 10.10 and installed the Linuxant ALSA-Driver which helped me switch between laptop speakers and headphones.. But since doing a fresh install of 12.10, I can't get my sound to work. Tried installing the linuxant deb file, but it errors out. Just wanted to see if anyone knows of a work around? I'm thinking of dropping back to 10.10 or maybe 11. and seeing if I can get it to work again. I do long haul trucking and have alot of movies that I like to watch at night before bed, but can't without sound.

```
david@Gizmo:~$ aplay -l
aplay: device_list:252: no soundcards found...

``` that comes up when I do aplay. 

```
david@Gizmo:~$ lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] Family 14h Processor Root Complex
00:01.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Wrestler [Radeon HD 6310]
00:01.1 Audio device: Advanced Micro Devices [AMD] nee ATI Wrestler HDMI Audio [Radeon HD 6250/6310]
00:11.0 SATA controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode]
00:12.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:12.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:13.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:13.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:14.0 SMBus: Advanced Micro Devices [AMD] nee ATI SBx00 SMBus Controller (rev 42)
00:14.2 Audio device: Advanced Micro Devices [AMD] nee ATI SBx00 Azalia (Intel HDA) (rev 40)
00:14.3 ISA bridge: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 LPC host controller (rev 40)
00:14.4 PCI bridge: Advanced Micro Devices [AMD] nee ATI SBx00 PCI to PCI Bridge (rev 40)
00:15.0 PCI bridge: Advanced Micro Devices [AMD] nee ATI SB700/SB800/SB900 PCI to PCI bridge (PCIE port 0)
00:15.2 PCI bridge: Advanced Micro Devices [AMD] nee ATI SB900 PCI to PCI bridge (PCIE port 2)
00:15.3 PCI bridge: Advanced Micro Devices [AMD] nee ATI SB900 PCI to PCI bridge (PCIE port 3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 0 (rev 43)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 1
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 2
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 3
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 4
00:18.5 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 6
00:18.6 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 5
00:18.7 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 7
06:00.0 Ethernet controller: Atheros Communications Inc. AR8151 v2.0 Gigabit Ethernet (rev c0)
07:00.0 Network controller: Atheros Communications Inc. AR9287 Wireless Network Adapter (PCI-Express) (rev 01)

``` 

My laptop is an Acer Aspire 5253 with a conexant Audio card. (atleast thats what the windows driver is )

1.6 GHz AMD E-Series E-350 dual core processors
4 GB of installed DDR3 RAM
500 GB hard disk drive
ATI Radeon HD 6310 graphics card

seams my ATI card is pulling up as the only sound card available. 

Anyone have ideas on how to fix this?

Thanks,

David

---

### Post by davidbuntu on 2013-01-30
BUMP!


Anyone come across this issue?? really need some help.

---

### Post by Yellow Pasque on 2013-01-30
> aplay: device_list:252: no soundcards found...
Did it work like that "out of the box" or is that the result of you experimenting with different drivers? I would try the latest driver: [https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS](https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS)

---

### Post by davidbuntu on 2013-01-30
> **Temüjin said:**
> Did it work like that "out of the box" or is that the result of you experimenting with different drivers? I would try the latest driver: [https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS](https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS)

that was out of the box with a fresh install. I will give the link a shot and see... Thanks.

---

### Post by davidbuntu on 2013-01-30
I didn't get a chance to try the above, but I did another fresh install and everything works now. I'll keep the above bookmarked for the future... 

Thanks.

---

