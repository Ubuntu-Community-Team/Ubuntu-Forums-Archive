---
title: "Jumpy LiveTV/recordings..."
date: 2009-08-12
forum: Mythbuntu
---

### Post by vip2 on 2009-08-12
I have a strange problem after updating my hardware for my MythTV box.  
The LiveTV and recordings jump every few seconds.

These are my current specs:
CPU - AMD Phenom II X4 810 2.6GHz
Motherboard - ECS GF8100VM-M3
Graphics - GeForce 8100 IGP
RAM - 4GB DDR2 800
HDDs - 2x Seagate 7200 RPM 500GB
HVR-1600 Model 1199
MythBuntu 9.04 x64 (fresh install using software RAID 0 for the recordings volume)
1280x1024 Resolution output to a Acer p1265 LCD Projector.

The HVR-1600 worked fine (smooth video) on my previous AMD Athlon XP 2200+ Compaq with a GeForce 2MX IGP and Mythbuntu 8.10 i386.  The HVR is the only component that has not changed.

I am running my DirecTV receiver via S-Video/RCA to the HVR-1600.  The receiver is controlled via Serial port.  I am not using the HDTV tuner of the HVR card (maybe later).

I have Googled and tried many tips (changing playback profiles, nvidia options, even installing a VDPAU MythTV) none of which have smoothed out my video.  The processor cores never go even close to 100% utilization while watching LiveTV or recordings.  

Any suggestions will be greatly appreciated.

Thanks...


hdparm -Tt /dev/md0 (the OS volume RAID1):
/dev/md0:
 Timing cached reads:   7110 MB in  2.00 seconds = 3556.19 MB/sec
 Timing buffered disk reads:  398 MB in  3.01 seconds = 132.20 MB/sec

hdparm -Tt /dev/md1 (the recordings volume RAID0):
/dev/md1:
 Timing cached reads:   7226 MB in  2.00 seconds = 3614.60 MB/sec
 Timing buffered disk reads:  770 MB in  3.00 seconds = 256.61 MB/sec


lspci:

00:00.0 RAM memory: nVidia Corporation MCP78S [GeForce 8200] Memory Controller (rev a2)
00:01.0 ISA bridge: nVidia Corporation MCP78S [GeForce 8200] LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP78S [GeForce 8200] SMBus (rev a1)
00:01.2 RAM memory: nVidia Corporation MCP78S [GeForce 8200] Memory Controller (rev a1)
00:01.3 Co-processor: nVidia Corporation MCP78S [GeForce 8200] Co-Processor (rev a2)
00:01.4 RAM memory: nVidia Corporation MCP78S [GeForce 8200] Memory Controller (rev a1)
00:02.0 USB Controller: nVidia Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller (rev a1)
00:02.1 USB Controller: nVidia Corporation MCP78S [GeForce 8200] EHCI USB 2.0 Controller (rev a1)
00:04.0 USB Controller: nVidia Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller (rev a1)
00:04.1 USB Controller: nVidia Corporation MCP78S [GeForce 8200] EHCI USB 2.0 Controller (rev a1)
00:06.0 IDE interface: nVidia Corporation MCP78S [GeForce 8200] IDE (rev a1)
00:07.0 Audio device: nVidia Corporation MCP78S [GeForce 8200] High Definition Audio (rev a1)
00:08.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Bridge (rev a1)
00:09.0 SATA controller: nVidia Corporation MCP78S [GeForce 8200] AHCI Controller (rev a2)
00:0a.0 Ethernet controller: nVidia Corporation MCP78S [GeForce 8200] Ethernet (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Express Bridge (rev a1)
00:10.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Express Bridge (rev a1)
00:12.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Express Bridge (rev a1)
00:13.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Bridge (rev a1)
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] Link Control
01:04.0 Multimedia video controller: Conexant Systems, Inc. CX23418 Single-Chip MPEG-2 Encoder with Integrated Analog Video/Broadcast Audio Decoder
02:00.0 VGA compatible controller: nVidia Corporation GeForce 8100 / nForce 720a (rev a2)


Partial mythfrontend.log (after a series of jumps in LiveTV): 

2009-08-11 17:07:36.034 TV: Attempting to change from None to WatchingLiveTV
2009-08-11 17:07:36.034 Using protocol version 40
2009-08-11 17:07:41.752 DPMS Deactivated 
2009-08-11 17:07:42.385 AFD: Opened codec 0x17cf430, id(MPEG2VIDEO) type(Video)
2009-08-11 17:07:42.385 AFD: codec MP2 has 2 channels
2009-08-11 17:07:42.385 AFD: Opened codec 0x17d7880, id(MP2) type(Audio)
2009-08-11 17:07:42.556 Opening audio device '/dev/dsp'. ch 2(2) sr 48000
2009-08-11 17:07:42.556 Opening OSS audio device '/dev/dsp'.
Unable to open mixer: 'default'
2009-08-11 17:07:43.129 VideoOutputXv: XVideo Adaptor Name: 'NV17 Video Texture'
2009-08-11 17:07:43.141 OSD Theme Dimensions W: 640 H: 480
2009-08-11 17:07:43.391 TV: Changing from None to WatchingLiveTV
2009-08-11 17:07:43.392 New DB connection, total: 3
2009-08-11 17:07:43.392 New DB connection, total: 4
2009-08-11 17:07:43.392 Connected to database 'mythconverg' at host: 127.0.0.1
2009-08-11 17:07:43.393 Connected to database 'mythconverg' at host: 127.0.0.1
2009-08-11 17:07:43.393 Realtime priority would require SUID as root.
Initialize Yadif Deinterlacer. In-Pixformat = 1 Out-Pixformat=1
yadifdeint: size changed from 0 x 0 -> 480 x 480
2009-08-11 17:07:43.495 Video timing method: USleep with busy wait
2009-08-11 17:07:53.222 NVP: prebuffering pause
2009-08-11 17:07:54.926 NVP: Prebuffer wait timed out 10 times.
2009-08-11 17:08:21.470 NVP: prebuffering pause
2009-08-11 17:08:23.163 NVP: Prebuffer wait timed out 10 times.
2009-08-11 17:08:24.855 NVP: Prebuffer wait timed out 20 times.
2009-08-11 17:08:26.547 NVP: Prebuffer wait timed out 30 times.
2009-08-11 17:08:27.514 MythSocket(7f3166951f00:30): readStringList: Error, timeout (quick).
2009-08-11 17:08:27.514 RemoteEncoder::SendReceiveStringList(): No response.
2009-08-11 17:08:27.514 NVP, Error: Unknown error, exiting decoder
2009-08-11 17:08:27.518 LiveTVChain(live-mythtv-2009-08-11T17:07:36): SwitchTo() not switching to current
2009-08-11 17:08:27.519 MythSocket(7f3166951f00:-1): writeStringList: Error, called with unconnected socket.
2009-08-11 17:08:27.519 MythSocket(7f3166951f00:-1): readStringList: Error, called with unconnected socket.
2009-08-11 17:08:27.519 RemoteEncoder::SendReceiveStringList(): No response.
2009-08-11 17:08:27.521 TV: Attempting to change from WatchingLiveTV to None

---

