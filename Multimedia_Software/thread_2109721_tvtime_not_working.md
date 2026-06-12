---
title: "tvtime not working"
date: 2013-01-28
forum: Multimedia Software
---

### Post by prabhanjan on 2013-01-28
I have pinnacle110i tv tuner & i'm unable to watch tv using tvtimne
i'm unable to scan channels
i tried almost everything...

i'm gettin following error message
> Reading configuration from /etc/tvtime/tvtime.xml
I/O warning : failed to load external entity "/home/iamhttp/.tvtime/tvtime.xml"
I/O error : Permission denied
I/O error : Permission denied
xmlSaveFormatFile returned -1 for config_filename /home/iamhttp/.tvtime/tvtime.xml
mixer: find error: Success
mixer: Can't open mixer default, mixer volume and mute unavailable.
mixer: Can't open device default/Line, mixer volume and mute unavailable.



My pciids is
> 00:00.0 RAM memory: NVIDIA Corporation MCP61 Host Bridge (rev a1)
00:01.0 ISA bridge: NVIDIA Corporation MCP61 LPC Bridge (rev a2)
00:01.1 SMBus: NVIDIA Corporation MCP61 SMBus (rev a2)
00:01.2 RAM memory: NVIDIA Corporation MCP61 Memory Controller (rev a2)
00:02.0 USB controller: NVIDIA Corporation MCP61 USB 1.1 Controller (rev a3)
00:02.1 USB controller: NVIDIA Corporation MCP61 USB 2.0 Controller (rev a3)
00:04.0 PCI bridge: NVIDIA Corporation MCP61 PCI bridge (rev a1)
00:05.0 Audio device: NVIDIA Corporation MCP61 High Definition Audio (rev a2)
00:06.0 IDE interface: NVIDIA Corporation MCP61 IDE (rev a2)
00:07.0 Bridge: NVIDIA Corporation MCP61 Ethernet (rev a2)
00:08.0 IDE interface: NVIDIA Corporation MCP61 SATA Controller (rev a2)
00:08.1 IDE interface: NVIDIA Corporation MCP61 SATA Controller (rev a2)
00:09.0 PCI bridge: NVIDIA Corporation MCP61 PCI Express bridge (rev a2)
00:0b.0 PCI bridge: NVIDIA Corporation MCP61 PCI Express bridge (rev a2)
00:0c.0 PCI bridge: NVIDIA Corporation MCP61 PCI Express bridge (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Link Control
[COLOR="Black"][COLOR="Red"]01:08.0 Multimedia controller: Philips Semiconductors SAA7131/SAA7133/SAA7135 Video Broadcast Decoder (rev d1)[/COLOR][/COLOR]
02:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RV710 [Radeon HD 4350]
02:00.1 Audio device: Advanced Micro Devices [AMD] nee ATI RV710/730 HDMI Audio [Radeon HD 4000 series]

plese help me

Is its possible to setup using mythtv

---

### Post by josephmills on 2013-01-28
Looks like there is a bug for that in myth 
[http://code.mythtv.org/trac/ticket/6530](http://code.mythtv.org/trac/ticket/6530)

Looks like it has been fixed and closed.  

I know nothing about tvtime , but I do know that Ubuntu TV  is looking for alpha testers 

[http://ubuntuforums.org/showthread.php?t=2109679](http://ubuntuforums.org/showthread.php?t=2109679)

---

### Post by prabhanjan on 2013-01-28
> **josephmills said:**
> Looks like there is a bug for that in myth 
[http://code.mythtv.org/trac/ticket/6530](http://code.mythtv.org/trac/ticket/6530)

Looks like it has been fixed and closed.  

I know nothing about tvtime , but I do know that Ubuntu TV  is looking for alpha testers 

[http://ubuntuforums.org/showthread.php?t=2109679](http://ubuntuforums.org/showthread.php?t=2109679)

thanks for quick reply
but i tried mythtv, still analog cards are not detecting

---

