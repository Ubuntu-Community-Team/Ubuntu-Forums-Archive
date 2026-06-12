---
title: "Hissing sound with headphones, Asus G750, HDA Intel PCH, Realtek ALC282"
date: 2014-10-19
forum: Multimedia Software
---

### Post by armstrong-gra on 2014-10-19
Hi there,

I've got Ubuntu 14.04 LTS installed on my laptop, an Asus ROG G750JW, which is fine except I'm having an audio problem.

The sound card is detected, and works. The speakers work without an issue, the problem is using the headphone jack. I notice that there's a distinct static noise when the headphones are plugged in; it's not affected by the volume and it's noticeable even with quiet music playing, the only thing that makes it stop is muting the audio.

I'll pop the output of lspci here in case it's of use. Note that the audio device I'm trying to use is the first one.
```
00:00.0 Host bridge: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor DRAM Controller (rev 06)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor PCI Express x16 Controller (rev 06)
00:14.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB xHCI (rev 04)
00:16.0 Communication controller: Intel Corporation 8 Series/C220 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 8 Series/C220 Series Chipset High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #1 (rev d4)
00:1c.2 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #3 (rev d4)
00:1c.3 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #4 (rev d4)
00:1c.4 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #5 (rev d4)
00:1d.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation HM87 Express LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 8 Series/C220 Series Chipset Family 6-port SATA Controller 1 [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation 8 Series/C220 Series Chipset Family SMBus Controller (rev 04)
01:00.0 VGA compatible controller: NVIDIA Corporation GK106M [GeForce GTX 765M] (rev a1)
01:00.1 Audio device: NVIDIA Corporation GK106 HDMI Audio Controller (rev a1)
03:00.0 Network controller: Qualcomm Atheros AR9485 Wireless Network Adapter (rev 01)
04:00.0 Ethernet controller: Qualcomm Atheros QCA8171 Gigabit Ethernet (rev 10)
```

Might anybody have any idea why this is?

Thanks,
Graham

---

### Post by redbull00 on 2014-10-20
The only thing that comes to my mind is that Asus basically turned really bad making their laptops not support anything with exception for the version of Windows they were certified for of course. Have you tried to play around with program called HdaJackRetask? It lets you override settings for respective ports and perhaps your headphone port is improperly assigned. This program helped me with my headphones because their port was marked as speakers and headphone preamplifier built in my mobo wasn't working for them, making it all quiet and of poor quality. Maybe that's the case in your case :)

---

### Post by emad-shi on 2014-11-13
were u able to solve it armstrong-gra?

---

