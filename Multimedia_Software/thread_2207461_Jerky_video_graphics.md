---
title: "Jerky video graphics"
date: 2014-02-23
forum: Multimedia Software
---

### Post by btaz on 2014-02-23
I'm looking for some ideas to my problem where the videos and general screen playback is really jerky.  I have a plex server setup and can stream fine from the computer so I don't think it is a processor or hard driver throughput issue (and the tops below show only a 30% CPU usage).  My guess is that it has something to do with the graphics card or processor rending, but haven't been able to figure where the issue is nor do I really know how to go about testing where the issue might be.  I have a dell M1730 with an Nvidia graphics card. Below are a few details of some things I know to check.  Thanks for any ideas or solutions to work on.

lspci excerpt:
> 00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M-E) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801HM/HEM (ICH8M/ICH8M-E) SATA Controller [AHCI mode] (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
01:00.0 PCI bridge: NVIDIA Corporation Device 01b3 (rev a3)
02:00.0 PCI bridge: NVIDIA Corporation Device 01b3 (rev a3)
02:01.0 PCI bridge: NVIDIA Corporation Device 01b3 (rev a3)
03:00.0 VGA compatible controller: NVIDIA Corporation G92M [GeForce 8800M GTX] (rev a2)
04:00.0 3D controller: NVIDIA Corporation G92M [GeForce 8800M GTX] (rev a2)



glxinfo excerpt:
> OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce 8800M GTX/PCIe/SSE2
OpenGL core profile version string: 3.3.0 NVIDIA 319.60

top with youtube
> top - 14:12:46 up  5:15,  2 users,  load average: 1.45, 0.54, 0.28
Tasks: 233 total,   2 running, 230 sleeping,   0 stopped,   1 zombie
%Cpu(s): 35.2 us, 46.8 sy,  0.0 ni, 17.2 id,  0.2 wa,  0.0 hi,  0.7 si,  0.0 st
KiB Mem:   4129404 total,  3892536 used,   236868 free,   531324 buffers
KiB Swap:  4194300 total,        0 used,  4194300 free,  2257472 cached


top with plex video
> top - 14:14:40 up  5:17,  2 users,  load average: 1.42, 0.79, 0.40
Tasks: 233 total,   3 running, 229 sleeping,   0 stopped,   1 zombie
%Cpu(s): 24.6 us, 36.6 sy,  0.0 ni, 35.6 id,  2.7 wa,  0.0 hi,  0.5 si,  0.0 st
KiB Mem:   4129404 total,  3994396 used,   135008 free,   531812 buffers
KiB Swap:  4194300 total,        0 used,  4194300 free,  2250936 cached


---

### Post by btaz on 2014-03-01
Bump....any ideas or suggestions?

---

