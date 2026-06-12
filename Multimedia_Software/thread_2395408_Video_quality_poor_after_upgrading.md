---
title: "Video quality poor after upgrading"
date: 2018-07-01
forum: Multimedia Software
---

### Post by KayeNg on 2018-07-01
Hello guys.  It seems video quality has become poor after my last  upgrade.  It is evident when I watch youtube videos as well as my own  videos via VLC player.

How can I fix it?

If it matters:

```
Kernel: 4.4.0-53-generic i686 (32 bit)
           Desktop: Cinnamon 3.2.7  Distro: Linux Mint 18.1 Serena
Machine:   Mobo: SAMSUNG model: R439/R478
           Bios: Phoenix v: 00UN.M001.20100814.LEO date: 08/14/2010
CPU:       Dual core Intel Core i3 M 380 (-HT-MCP-) speed/max: 1066/2533 MHz
Graphics:  Card: Advanced Micro Devices [AMD/ATI] Park [Mobility Radeon HD 5430/5450/5470]
           Display Server: X.Org 1.18.4 drivers: ati,radeon (unloaded: fbdev,vesa)
           Resolution: 1366x768@60.00hz
           GLX Renderer: Gallium 0.4 on AMD CEDAR (DRM 2.43.0, LLVM 3.8.0)
           GLX Version: 3.0 Mesa 11.2.0
Network:   Card-1: Broadcom BCM4313 802.11bgn Wireless Network Adapter
           driver: bcma-pci-bridge
           Card-2: Marvell 88E8040 PCI-E Fast Ethernet Controller driver: sky2
Drives:    HDD Total Size: 500.1GB (23.1% used)
Info:      Processes: 211 Uptime: 1:28 Memory: 808.8/1938.8MB
           Client: Shell (bash) inxi: 2.2.35 
```

Here is the output if I open vlc in terminal and played a video.

```
VLC media player 2.2.2 Weatherwax (revision 2.2.2-0-g6259d80)
[09285930] core libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
Failed to open VDPAU backend libvdpau_r600.so: cannot open shared object file: No such file or directory
Failed to open VDPAU backend libvdpau_r600.so: cannot open shared object file: No such file or directory

```

deleting this doesn't help.
 .config/vlc/

I don't know how to describe the quality.  It's not smooth.  Like it skips frames.  And it's like that in other media player, not just vlc.

Thank you.

---

### Post by wildmanne39 on 2018-07-01
*Thread moved to **Multimedia Software for a more appropriate fit**.*

---

### Post by TheFu on 2018-07-02
Sounds like a GPU driver issue.  I don't know anything about AMD GPUs anymore since Radeon HD 5430 support ended over 3 yrs ago and my E-350 APU couldn't keep up.

[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver) has some steps that might help.

Be certain to check the *Removing the proprietary fglrx driver* section.

---

### Post by KayeNg on 2018-07-17
Just to be clear, this is what I have:

```
System:    Host: kaye-nb Kernel: 4.13.0-45-generic i686 (32 bit)
           Desktop: Cinnamon 3.2.7  Distro: Linux Mint 18.1 Serena
Machine:   Mobo: SAMSUNG model: R439/R478
           Bios: Phoenix v: 00UN.M001.20100814.LEO date: 08/14/2010
CPU:       Dual core Intel Core i3 M 380 (-HT-MCP-) speed/max: 1537/2533 MHz
Graphics:  Card: Advanced Micro Devices [AMD/ATI] Park [Mobility Radeon HD 5430/5450/5470]
           Display Server: X.Org 1.18.4 driver: N/A
           Resolution: 1366x768@60.00hz
           GLX Renderer: AMD CEDAR (DRM 2.50.0 / 4.13.0-45-generic, LLVM 6.0.0)
           GLX Version: 3.0 Mesa 18.0.5
Network:   Card-1: Broadcom Limited BCM4313 802.11bgn Wireless Network Adapter
           driver: bcma-pci-bridge
           Card-2: Marvell 88E8040 PCI-E Fast Ethernet Controller driver: sky2
Drives:    HDD Total Size: 500.1GB (2.1% used)
Info:      Processes: 173 Uptime: 20 min Memory: 747.1/1937.4MB
           Client: Shell (bash) inxi: 2.2.35

```

Notice these lines:

```
Machine:   Mobo: SAMSUNG model: R439/R478
Graphics:  Card: Advanced Micro Devices [AMD/ATI] Park [Mobility Radeon HD 5430/5450/5470]

```

On this page: [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)  ,   under the list of the "Fully supported", there is no R439 or R478.

There is however,    **CEDAR    Radeon HD 5430/5450/6330/6350/6370**   , which I guess is similar to my terminal output: (bold highlight by me)

```
Graphics:  Card: Advanced Micro Devices [AMD/ATI] Park [Mobility **Radeon HD 5430/5450**/5470]
           Display Server: X.Org 1.18.4 driver: N/A
           Resolution: 1366x768@60.00hz
           GLX Renderer: AMD **CEDAR** (DRM 2.50.0 / 4.13.0-45-generic, LLVM 6.0.0)
           GLX Version: 3.0 Mesa 18.0.5

```


That's where I'm at.  I don't know what to do from here.  Should I just revert back to the previous kernel? 

Thanks!

---

### Post by kazakore on 2018-07-17
> **KayeNg said:**
> 

Notice these lines:

```
Machine:   Mobo: SAMSUNG model: R439/R478
Graphics:  Card: Advanced Micro Devices [AMD/ATI] Park [Mobility Radeon HD 5430/5450/5470]

```

On this page: [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)  ,   under the list of the "Fully supported", there is no R439 or R478.



The HD 5430/5450/5470 is listed there under CEDAR. That page is rather old although it does show your card should have been supported for some time (although it doesn't mention 5470, only 5430 and 5450....)

What driver are you using? Have you checked for Propriety Device Drivers in the Software Centre? Or [This One]("http://www.opendrivers.com/download/driver-160164.html") from the Open Driver project??

---

