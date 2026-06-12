---
title: "Dell Studio Hybrid 140g video driver questions...?"
date: 2019-05-12
forum: MINT
---

### Post by RallyDarkstrike on 2019-05-12
Hi all,

Odd question concerning the little PC I just set up with Mint 19.1 MATE  as a Media Center PC. The machine is a Dell Studio Hybrid 140g (Intel  Core 2 Duo 2.1Ghz, 4GB RAM, 320GB hard drive). Not the most powerful rig  in the world, but it should be OK for a Media Center PC.

I looked up reviews for it before I bought it - it has an Intel GMA  X3100 video card, which is feeble by today's standards, but should be  fine for basic video watching. Reviews / stats from Dell said it can do 720p/1080p video.  My TV is only set to 1360x768 resolution because of how far back my  couch is from it...any higher a resolution and I can't really see what  I'm doing. That being said, when I try to play 1080p video, it will  play, but is noticeably skippy. 720p video is skippy at first, but  smooths out after a few seconds (though it still skips once and awhile).

I know it can BARELY do 1080p, but it can supposedly do it smoothly. I'm  happy if I could just watch things in 720p on it smoothly, but I'm a  bit stumped why mine is skippy as it is when it can supposedly handle  the content...? Is there a driver that works better  than the one my system automatically loaded?

System info as follows:
```
System:
  Host: Maluch Kernel: 4.15.0-48-generic x86_64 bits: 64 compiler: gcc 
  v: 7.3.0 Desktop: MATE 1.20.1 Distro: Linux Mint 19.1 Tessa 
  base: Ubuntu 18.04 bionic 
Machine:
  Type: Desktop System: Dell product: Studio Hybrid 140g v: 00 
  serial: <filter> 
  Mobo: Dell model: 0P096C v: A01 serial: <filter> BIOS: Dell v: 1.0.6 
  date: 09/26/2008 
CPU:
  Topology: Dual Core model: Intel Core2 Duo T5850 bits: 64 type: MCP 
  arch: Core Merom rev: D L2 cache: 2048 KiB 
  flags: lm nx pae sse sse2 sse3 ssse3 bogomips: 8645 
  Speed: 1200 MHz min/max: 1000/2167 MHz Core speeds (MHz): 1: 1287 2: 1495 
Graphics:
  Device-1: Intel Mobile GM965/GL960 Integrated Graphics vendor: Dell 
  driver: i915 v: kernel bus ID: 00:02.0 
  Display: x11 server: X.Org 1.19.6 driver: modesetting unloaded: fbdev,vesa 
  resolution: 1360x768~60Hz 
  OpenGL: renderer: Mesa DRI Intel 965GM v: 2.1 Mesa 18.2.8 
  direct render: Yes 
Audio:
  Device-1: Intel 82801H HD Audio vendor: Dell driver: snd_hda_intel 
  v: kernel bus ID: 00:1b.0 
  Device-2: Microsoft type: USB driver: snd-usb-audio,uvcvideo bus ID: 2-3:2 
  Sound Server: ALSA v: k4.15.0-48-generic 
Network:
  Device-1: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet 
  vendor: Dell driver: r8169 v: 2.3LK-NAPI port: e800 bus ID: 02:00.0 
  IF: ens35 state: down mac: <filter> 
  Device-2: Qualcomm Atheros AR928X Wireless Network Adapter vendor: Foxconn 
  driver: ath9k v: kernel port: e800 bus ID: 04:00.0 
  IF: wls32 state: up mac: <filter> 
Drives:
  Local Storage: total: 298.09 GiB used: 98.49 GiB (33.0%) 
  ID-1: /dev/sda vendor: Western Digital model: WD3200BPVT-00HXZT1 
  size: 298.09 GiB 
Partition:
  ID-1: / size: 288.97 GiB used: 98.49 GiB (34.1%) fs: ext4 dev: /dev/sda1 
Sensors:
  System Temperatures: cpu: 36.0 C mobo: N/A 
  Fan Speeds (RPM): cpu: 2835 
Info:
  Processes: 187 Uptime: 7h 44m Memory: 3.84 GiB used: 2.28 GiB (59.4%) 
  Init: systemd runlevel: 5 Compilers: gcc: 7.4.0 Shell: bash v: 4.4.19 
  inxi: 3.0.27
```

Somebody on the Mint forums suggested I install the older xserver-xorg-video-intel driver and reboot - tried installing it through Terminal and it told me that it was already installed, but inxi tells me the system is using the modesetting driver...?

How would I force the system to use the older intel-specific driver and see if that helps my issue? Thanks for any suggestions! :)

---

### Post by him610 on 2019-05-13
> BIOS: Dell v: 1.0.6   date: 09/26/2008 
Your system is over ten years old. Don't think your hardware can be upgraded. It uses integrated graphics.
Time to upgrade or accept 720p video.  
Not familiar with Mint, but you might get better performance from OS version that demands less resources - consider Lubuntu or Xubuntu. I don't know if Mint has equivalents.

---

### Post by RallyDarkstrike on 2019-05-13
I didn't think it could be upgraded, mainly that it it supposed to be  capable of running smoothly at 1080p in Windows but mine isn't doing  that in Linux, so I figured it may be a driver issue. I think it's  running the modesetting driver, I'm just curious if switching it to the  intel proprietary driver would help, but am not sure how to do so.

---

### Post by him610 on 2019-05-14
I have the intel 945GSE integrated graphics controller on my atom-powered netbook and it has the Intel driver loaded. It came with the Xubuntu 1.04 LTS operating system; not necessary to anything extraordinary; loaded during OS installation.. You might check in Settings > Additional Drivers or wherever you find them in Mint.

---

### Post by him610 on 2019-05-15
You might want to take a look at this, [https://ubuntuforums.org/showthread.php?t=2409607&p=13828277#post13828277]("https://ubuntuforums.org/showthread.php?t=2409607&p=13828277#post13828277")

---

