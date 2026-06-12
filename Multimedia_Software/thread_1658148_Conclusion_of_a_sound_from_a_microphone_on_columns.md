---
title: "Conclusion of a sound from a microphone on columns [ALSA]"
date: 2011-01-02
forum: Multimedia Software
---

### Post by Krovavii on 2011-01-02
Hello, I'm have one problem with sound adjustment, to be exact - I should create the bridge between a linear input and output. It is desirable, with possibility to impose effects on a sound. (But it isn't obligatory)

Standard decisions don't help

Alsamixer:
[[IMG]http://savepic.org/1161504m.png[/IMG]]("http://savepic.org/1161504.htm")

lspci | grep Audio:
> egor@egor-ubuntu:~$ lspci | grep Audio
00:08.0 Audio device: nVidia Corporation MCP79 High Definition Audio (rev b1)
02:00.1 Audio device: nVidia Corporation High Definition Audio Controller (rev a1)lspci (full):
> 00:00.0 Host bridge: nVidia Corporation MCP79 Host Bridge (rev b1)
00:00.1 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.0 ISA bridge: nVidia Corporation MCP79 LPC Bridge (rev b2)
00:03.1 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.2 SMBus: nVidia Corporation MCP79 SMBus (rev b1)
00:03.3 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.5 Co-processor: nVidia Corporation MCP79 Co-processor (rev b1)
00:04.0 USB Controller: nVidia Corporation MCP79 OHCI USB 1.1 Controller (rev b1)
00:04.1 USB Controller: nVidia Corporation MCP79 EHCI USB 2.0 Controller (rev b1)
00:06.0 USB Controller: nVidia Corporation MCP79 OHCI USB 1.1 Controller (rev b1)
00:06.1 USB Controller: nVidia Corporation MCP79 EHCI USB 2.0 Controller (rev b1)
00:08.0 Audio device: nVidia Corporation MCP79 High Definition Audio (rev b1)
00:09.0 PCI bridge: nVidia Corporation MCP79 PCI Bridge (rev b1)
00:0b.0 SATA controller: nVidia Corporation MCP79 AHCI Controller (rev b1)
00:0c.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:15.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:16.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
02:00.0 VGA compatible controller: nVidia Corporation Device 0a2d (rev a2)
02:00.1 Audio device: nVidia Corporation High Definition Audio Controller (rev a1)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
04:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)uname -a:
> egor@egor-ubuntu:~$ uname -a
Linux egor-ubuntu 2.6.32-21-generic #32-Ubuntu SMP Fri Apr 16 08:10:02 UTC 2010 i686 GNU/LinuxAlsa and PulseAudio was installed from PPA.

Google hasn't given the answer to this question. 

Please, help me to fix this problem! Thanks! 

PS, Pleas, sorry for my bad English. ;)

---

### Post by Krovavii on 2011-01-03
Up!
Please, help! :)

---

