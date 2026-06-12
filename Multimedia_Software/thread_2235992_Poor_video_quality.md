---
title: "Poor video quality:"
date: 2014-07-24
forum: Multimedia Software
---

### Post by radibg2 on 2014-07-24
The video quality is poor and on flash player and on SMPlayer here is a picture of 1080p video in youtube which i watched on my windows and android phone and the quality is way better:
[IMG]http://prikachi.com/images/169/7490169T.png[/IMG]
I have not changed any graphic card settings, here is lspci:
```
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)00:01.0 PCI bridge: Intel Corporation Core Processor PCI Express x16 Root Port (rev 02)
00:1a.0 USB controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05)
00:1c.4 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 (rev 05)
00:1c.7 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 8 (rev 05)
00:1d.0 USB controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 6 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 05)
01:00.0 VGA compatible controller: NVIDIA Corporation GT216M [GeForce GT 320M] (rev a2)
01:00.1 Audio device: NVIDIA Corporation GT216 HDMI Audio Controller (rev a1)
02:00.0 Network controller: Broadcom Corporation BCM43225 802.11b/g/n (rev 01)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 03)
04:00.0 FireWire (IEEE 1394): JMicron Technology Corp. IEEE 1394 Host Controller
04:00.1 System peripheral: JMicron Technology Corp. SD/MMC Host Controller
04:00.2 SD Host controller: JMicron Technology Corp. Standard SD Host Controller
04:00.3 System peripheral: JMicron Technology Corp. MS Host Controller
04:00.4 System peripheral: JMicron Technology Corp. xD Host Controller
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)

```

---

### Post by kc1di on 2014-07-24
Hi radibg2  and welcome to Ubuntu,

can you post the output of ```
lspci -v -s `lspci | awk '/VGA/{print $1}'`
``` 
I suspect that your using the open source driver nouveau.  You'll need to install the propritory driver for your card. in your case try the nvidia-331 driver.
you can do that by going to software center >edit>addtional drivers and install the recommended driver.
or you can install it in the terminal with this command ```
sudo apt-get install nvidia-331
```

---

### Post by radibg2 on 2014-07-24
result of lspci -v -s `lspci | awk '/VGA/{print $1}'`:
```
01:00.0 VGA compatible controller: NVIDIA Corporation GT216M [GeForce GT 320M] (rev a2) (prog-if 00 [VGA controller])
    Subsystem: Hewlett-Packard Company Device 365c
    Flags: bus master, fast devsel, latency 0, IRQ 43
    Memory at d2000000 (32-bit, non-prefetchable) [size=16M]
    Memory at c0000000 (64-bit, prefetchable) [size=256M]
    Memory at d0000000 (64-bit, prefetchable) [size=32M]
    I/O ports at 6000 [size=128]
    Expansion ROM at d3080000 [disabled] [size=512K]
    Capabilities: <access denied>
    Kernel driver in use: nouveau
```
By Software Center>Edit>Aditional drivers i am with NVIDIA binary driver - version 331.8 from nvidia-331-updates(proprietary), now i will try to install it by sudo apt-get install nvidia-331
-------------------------
I've tried it is very little better,still on a lot of places is on squares, when the resolution is 720p and not full screen normal loadpage youtube video screen the whole video is on squares, but on my Windows and Android the quality is ok with no squares anywhere(forat 720p and 1080p).
-------------------------
I've changed the video player from VLC to SMPlayer and now video quiality is ok, i tried to watch video on Firefox instead of Chrome and the quality was ok with no squares, how to fix this problem in Chrome?

---

### Post by kc1di on 2014-07-24
I'm not sure how to fix it with chrome as it has it's own flashplayer and that may be the problem. 
but at the moment that's the newest nvidia driver that's stable.   There are newer ones but think you should stick to the one 
in the repositories for now. I don't think the problem with chrome is cause by the video driver. 

maybe some one with experience with chrome will chime in.
good Luck :)

---

### Post by radibg2 on 2014-07-24
I think YouTube uses HTML5 for playing videos when it is available, not FlashPlayer.

---

### Post by kc1di on 2014-07-24
Hi radibg2, 
I think your right but I don't see how HTML5 would cause the problem the op is talking about in chrome.  It works fine here.  Sometimes wiht a flashplayer video however it gets choppy in chrome on my machine. and Like the op said it fine in F.F.  so it must be something in Chrome, Only thing different would be flash as far as I know.  But haven't really researched it.

---

### Post by renanrischiotto1 on 2014-07-25
Same problem here. The video quality is not stable and does not run in 720p. If I open the video and do not change the resolution, it runs in 360p, if I try to change to 480p or 720p will not, the resolution falls, sometimes goes up to 144p (on Chrome). This happens in a video I'm trying to watch. On Firefox the video runs in 240p e and all other resolutions are disabled except for 720p and 144p, but when trying to run at 720p will not, the resolution falls to 144p. In another video, the quality at 480p works, but when switching to 720p quality gets worse, he until changed, but the quality is bad (on Chrome). On Firefox works. Happens several different things, less run the video normally.

Xubuntu 14.04 x86_64
NVIDIA 331.38 driver
Google Chrome 36
Firefox 31

---

### Post by renanrischiotto1 on 2014-07-31
The problem still remains? I wanted to go back to using Xubuntu.

---

