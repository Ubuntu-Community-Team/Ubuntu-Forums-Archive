---
title: "Can't emit sound and video at the same time in gtalk"
date: 2011-03-13
forum: Multimedia Software
---

### Post by tanpopo_chan on 2011-03-13
Hello everyone!

Here's one that's been making me go crazy and I'm going to bet that is is probably a bug...

You see, I recently installed the plugin for Google voice and video chat, which can be found here: [http://www.google.com/chat/video](http://www.google.com/chat/video)
I also set-up Empathy to use Gtalk with the server set to talk.google.com, Use Old SSL, and encryption.

At first, my sound didn't work, so I tried a few workarounds and I finally got it working. But then, my video stopped emitting... So I tried something else and got the video working.

Here's the problem:
When, I make a video call I can't emit sound, but if I make a voice call I can emit sound... yet if I select to show video as well during the voice call the microphone stops functioning. This happens when I use gtalk over Chromium or Mozilla.

If I try the same thing in Empathy, it only lets me make voice calls. If I try a video call it says it connected, but it only emits sound.
If I enable video during a voice call, I can see myself but the other person can't.

Any ideas??

PS:

I'm running an HP Pavillion DV6. Ubuntu 10.10 x64. 

Here's my messages log:
```
Mar 13 13:15:25 TSUKI pulseaudio[1674]: ratelimit.c: 4881 events suppressed
Mar 13 13:15:30 TSUKI pulseaudio[1674]: ratelimit.c: 2997 events suppressed
Mar 13 13:15:35 TSUKI pulseaudio[1674]: ratelimit.c: 1550 events suppressed
Mar 13 13:16:25 TSUKI kernel: [  308.452514] hda-intel: azx_get_response timeout, switching to polling mode: last cmd=0x01270600
Mar 13 13:16:32 TSUKI pulseaudio[2346]: pid.c: Stale PID file, overwriting.
Mar 13 13:16:37 TSUKI pulseaudio[2346]: ratelimit.c: 3 events suppressed
Mar 13 13:16:43 TSUKI pulseaudio[2346]: ratelimit.c: 1 events suppressed
Mar 13 13:17:47 TSUKI pulseaudio[2486]: pid.c: Stale PID file, overwriting.
Mar 13 13:17:52 TSUKI pulseaudio[2486]: ratelimit.c: 6 events suppressed
Mar 13 13:18:53 TSUKI pulseaudio[2519]: pid.c: Stale PID file, overwriting.
Mar 13 13:18:59 TSUKI pulseaudio[2519]: ratelimit.c: 1 events suppressed
Mar 13 13:25:09 TSUKI pulseaudio[2519]: ratelimit.c: 9949 events suppressed
Mar 13 13:25:14 TSUKI pulseaudio[2519]: ratelimit.c: 7979 events suppressed
Mar 13 13:25:19 TSUKI pulseaudio[2519]: ratelimit.c: 7227 events suppressed
Mar 13 13:25:24 TSUKI pulseaudio[2519]: ratelimit.c: 9520 events suppressed
Mar 13 13:25:29 TSUKI pulseaudio[2519]: ratelimit.c: 5987 events suppressed
```


My lsusb:
```
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 093a:2510 Pixart Imaging, Inc. Optical Mouse
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 0408:03f1 Quanta Computer, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```


And my lspci:
```
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge Alternate
00:02.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (ext gfx port 0)
00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0)
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
00:0a.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 5)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3c)
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Link Control
01:00.0 VGA compatible controller: ATI Technologies Inc M96 [Mobility Radeon HD 4650]
01:00.1 Audio device: ATI Technologies Inc RV710/730
08:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
09:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
0a:00.0 FireWire (IEEE 1394): JMicron Technology Corp. IEEE 1394 Host Controller
0a:00.1 System peripheral: JMicron Technology Corp. SD/MMC Host Controller
0a:00.2 SD Host controller: JMicron Technology Corp. Standard SD Host Controller
0a:00.3 System peripheral: JMicron Technology Corp. MS Host Controller
0a:00.4 System peripheral: JMicron Technology Corp. xD Host Controller
```

---

