---
title: "VLC player stopped working for DVB and local files"
date: 2016-11-18
forum: Multimedia Software
---

### Post by pablosquared on 2016-11-18
Hi all,
VLC was working fine up till yesterday, when some system updates were applied - not sure if that's relevant or not. Now, the app loads ok and opens and displays the DVB playlist (channels.conf) but won't playback any of the channels. Starting VLC from the terminal gives:

```

unknown option (code-rate-hp=2/3:code-rate-lp=1/2:modulation=64QAM:transmission=-1:guard=1/32:hierarchy=0)

```

I use an elderly Hauppauge TC tuner (Listed as Conexant, below). VLC is configured to access /dev/dvb/adaptor0, as always. I don't see any errors on boot up that would indicate it's faulty.

```

00:00.0 Host bridge: Intel Corporation Sky Lake Host Bridge/DRAM Registers (rev 07)
00:01.0 PCI bridge: Intel Corporation Sky Lake PCIe Controller (x16) (rev 07)
00:14.0 USB controller: Intel Corporation Sunrise Point-H USB 3.0 xHCI Controller (rev 31)
00:16.0 Communication controller: Intel Corporation Sunrise Point-H CSME HECI #1 (rev 31)
00:17.0 SATA controller: Intel Corporation Sunrise Point-H SATA controller [AHCI mode] (rev 31)
00:1b.0 PCI bridge: Intel Corporation Sunrise Point-H PCI Root Port #17 (rev f1)
00:1c.0 PCI bridge: Intel Corporation Sunrise Point-H PCI Express Root Port #1 (rev f1)
00:1c.3 PCI bridge: Intel Corporation Sunrise Point-H PCI Express Root Port #4 (rev f1)
00:1d.0 PCI bridge: Intel Corporation Sunrise Point-H PCI Express Root Port #9 (rev f1)
00:1d.5 PCI bridge: Intel Corporation Sunrise Point-H PCI Express Root Port #14 (rev f1)
00:1f.0 ISA bridge: Intel Corporation Sunrise Point-H LPC Controller (rev 31)
00:1f.2 Memory controller: Intel Corporation Sunrise Point-H PMC (rev 31)
00:1f.3 Audio device: Intel Corporation Sunrise Point-H HD Audio (rev 31)
00:1f.4 SMBus: Intel Corporation Sunrise Point-H SMBus (rev 31)
01:00.0 VGA compatible controller: NVIDIA Corporation GM107 [GeForce GTX 750 Ti] (rev a2)
01:00.1 Audio device: NVIDIA Corporation Device 0fbc (rev a1)
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 11)
06:00.0 PCI bridge: ASMedia Technology Inc. ASM1083/1085 PCIe to PCI Bridge (rev 04)
07:00.0 Multimedia audio controller: Creative Labs CA0106 Soundblaster
07:01.0 Multimedia video controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
07:01.2 Multimedia controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [MPEG Port] (rev 05)
07:01.4 Multimedia controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [IR Port] (rev 05)


```


Not sure what the error message means but it looks related to frequencies. As well as DVB not working, VLC won't playback local video files (MP4, MKV) either, so the problem looks fundamental. The only other clue is that I now have 2 VLC icons in the system tray, where there was only one before, and selecting Quit from them does nothing. 


Any ideas?

---

### Post by ajgreeny on 2016-11-18
What version of *ubuntu and what version of VLC?

I have Xubuntu 16.04 here in the UK running VLC version 2.2.2 Weatherwax and all is working fine here on both local files of all kinds, and network streams of BBC radio programs.

---

### Post by pablosquared on 2016-11-18
Thanks, interesting that you've not seen the same problems. I'm running Ubuntu 16.04 with the Weatherwax version of VLC. 

The other thing that's started happening in the same timeframe is that Ubuntu doesn't shut down now, It hangs at the purple Plymouth Ubuntu screen and I have to power the system off with the button. Only since yesterday's updates which I think included a kernel update among other things (maybe libc too).

---

### Post by pablosquared on 2016-11-22
Ok, so I tried various things - uninstall / reinstall VLC, resetting configuration etc. - nothing worked. In hope rather than expectation, I upgraded ubuntu to 16.10, and that seems to have fixed this problem. I note that 16.10 installs VLC 2.2.4, rather than the 2.2.2 that comes with 16.04. So, for anyone else having that problem, it might be worth trying the later version.

Thanks for your help..:p

---

