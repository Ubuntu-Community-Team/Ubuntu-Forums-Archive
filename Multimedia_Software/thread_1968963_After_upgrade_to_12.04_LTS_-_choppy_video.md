---
title: "After upgrade to 12.04 LTS - choppy video"
date: 2012-04-29
forum: Multimedia Software
---

### Post by gen2600 on 2012-04-29
Just as it sounds, upgraded to 12.04 LTS and our families media center computer now displays low frame rates in vids that are large windowed or especially full screened.

Prior to this, I have played vids in full screen without any sort of low frame issue every time.

Facts:

*Using Unity.

*Tried VLC as well as standard media player.

*System load is .19 on average.

*Vid card: ATI Radeon HD 3200.

*Linux 3.2.0-24-generic #37-Ubuntu SMP Wed Apr 25 08:43:22 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux.

*lspci output:
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:01.0 PCI bridge: ASUSTeK Computer Inc. RS880 PCI to PCI bridge (int gfx)
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780/RS880 PCI to PCI bridge (PCIE port 1)
00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
00:11.0 RAID bus controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 SATA Controller [Non-RAID5 mode]
00:12.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:12.1 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0 USB OHCI1 Controller
00:12.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:13.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:13.1 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0 USB OHCI1 Controller
00:13.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:14.0 SMBus: Advanced Micro Devices [AMD] nee ATI SBx00 SMBus Controller (rev 3a)
00:14.1 IDE interface: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 IDE Controller
00:14.3 ISA bridge: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 LPC host controller
00:14.4 PCI bridge: Advanced Micro Devices [AMD] nee ATI SBx00 PCI to PCI Bridge
00:14.5 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI2 Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Link Control
01:05.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RS780 [Radeon HD 3200]
01:05.1 Audio device: Advanced Micro Devices [AMD] nee ATI RS780 HDMI Audio [Radeon HD 3000-3300 Series]
02:00.0 FireWire (IEEE 1394): JMicron Technology Corp. IEEE 1394 Host Controller
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
04:06.0 Ethernet controller: ADMtek NC100 Network Everywhere Fast Ethernet 10/100 (rev 11)
04:07.0 Multimedia audio controller: Creative Labs CA0106 Soundblaster

...any help would be greatly appreciated!!!

---

### Post by mvmacd on 2012-04-29
just curious, have you enabled a proprietary AMD graphics driver? 
or are you using the default open source driver.
you might try switching to whatever driver you're not using, and see if it makes a difference. it seemed to fix youtube when I went back to the open source driver

---

### Post by gen2600 on 2012-04-30
> **mvmacd said:**
> just curious, have you enabled a proprietary AMD graphics driver? 
or are you using the default open source driver.
you might try switching to whatever driver you're not using, and see if it makes a difference. it seemed to fix youtube when I went back to the open source driver

When I go into system settings and additional drivers I have two options which both say, "ATI/AMD Proprietary FGLRX graphics driver" and one of them has an additional tag that reads "post-release updates".  I currently have the one labeled "post-release updates" selected.

I don't seem to have an option to go to an open source driver.  Can you give me more info on that?

Btw, thanks for responding!

---

### Post by gen2600 on 2012-04-30
Also:

mediauser@Hunin:~$ fglrxinfo
display: :0  screen: 0
OpenGL vendor string: Advanced Micro Devices, Inc.
OpenGL renderer string: ATI Radeon HD 3200 Graphics
OpenGL version string: 3.3.11627 Compatibility Profile Context

---

### Post by mvmacd on 2012-04-30
Ok by default, the open source driver is used for Radeon.  Those drivers listed are by AMD. So if neither are activated, your using open source.

You might try your luck with them. For me the "post release updates"  won't install for me and the other doesn't seem to work well so I'm using open source for now.

---

### Post by gen2600 on 2012-04-30
SOLVED.

I measured differences between the open source drivers as well as what was available from proprietary driver with almost no effect in my FPS.


I ended up installing Gnome3 and selected the no effects version.

add-apt-repository ppa:gnome3-team/gnome3
apt-get update
apt-get install gnome-shell

...poof, flawless video, with any of the graphics drivers.

Thanks for looking at this :)

---

