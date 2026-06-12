---
title: "ubuntu 12.04: Dont'get Subtitle Editor working on importing video"
date: 2012-10-29
forum: Multimedia Software
---

### Post by zyspill on 2012-10-29
Dear forum users,

I tried to build various versions of subtitle-editor, but  in the end since there seemed to be not much of a differece between the  versions,
since they were basically all not working, I stuck to subtitleeditor0_0.39.0-2_amd64 from the repositories.
I installed gstreamer 1.0 besides 0.10, tried to downgrade 0.10, but didn't help and didn't know how to link the 1.0-version 
to subtitle editor if that works anyhow?
I spent the whole day trying to get this working,but I finally got stuck getting the following errors again and again while trying to import AVI, mkv or mp4 videos into Subtitle Editor:

*** glibc detected *** subtitleeditor: malloc(): memory corruption (fast): 0x0000000001439850 ***


My System Information:
Build 2012-10-29 on Linux 3.2.0-23-generic #36-Ubuntu SMP Tue Apr 10 20:39:51
UTC 2012 x86_64 x86_64 x86_64 GNU/Linux (Mint 13 XFCE, based on Ubuntu 12.04)

$ inxi -Fc 0
System:    Host: xxxx Kernel: 3.2.0-23-generic x86_64 (64 bit) Desktop: Xfce 4.10.0 Distro: Linux Mint 13 Maya
Machine:   System: SAMSUNG (portable) product: SR70S/SR71S version: 05AB
           Mobo: SAMSUNG model: SR70S/SR71S Bios: Phoenix version: 05AB date: 07/19/2007
CPU:       Dual core Intel Core2 Duo CPU T7300 (-MCP-) cache: 4096 KB flags: (lm nx sse sse2 sse3 ssse3 vmx) 
           Clock Speeds: 1: 800.00 MHz 2: 800.00 MHz
Graphics:  Card: NVIDIA G86 [GeForce 8600M GS] 
           X.Org: 1.11.3 drivers: nvidia (unloaded: nouveau,vesa,fbdev) Resolution: 1280x800@50.0hz 
           GLX Renderer: GeForce 8600M GS/PCIe/SSE2 GLX Version: 3.3.0 NVIDIA 295.40
Audio:     Card: Intel 82801H (ICH8 Family) HD Audio Controller driver: snd_hda_intel Sound: ALSA ver: 1.0.24
Network:   Card-1: Marvell 88E8055 PCI-E Gigabit Ethernet Controller driver: sky2 
           IF: eth0 state: down mac: xx:xx:xx:xx:xx:xx
           Card-2: Intel PRO/Wireless 4965 AG or AGN [Kedron] Network Connection driver: iwl4965 
           IF: wlan0 state: up mac: xx:xx:xx:xx:xx:xx
Drives:    HDD Total Size: 60.0GB (84.3% used) 1: /dev/sda INTEL_SSDSC2CW06 60.0GB 
Partition: ID: / size: 56G used: 48G (89%) fs: ext4 
Sensors:   System Temperatures: cpu: 43.0C mobo: 43.0C gpu: 55C 
           Fan Speeds (in rpm): cpu: N/A 
Info:      Processes: 165 Uptime: 6:03 Memory: 1117.7/3953.8MB Client: Shell inxi: 1.7.33

Thanks in advance,
zyspill

---

### Post by zyspill on 2013-04-28
I gave it up with subtitleeditor now
and will give aegisub a try,
installing by source from [http://www.aegisub.org/downloads/#source](http://www.aegisub.org/downloads/#source)
but before you need a player to work with, this is foundable in [http://code.google.com/p/ffmpegsource/downloads/list](http://code.google.com/p/ffmpegsource/downloads/list)
and I take the ffms-2.17-src.tar.bz2     FFmpegSource 2.17 source code 
some dependencies include libavformat-dev  libswscale-dev
pulseaudio developement files libass-dev, as various hunspell-files for spelling correction

AND! It works!
hurray!

---

