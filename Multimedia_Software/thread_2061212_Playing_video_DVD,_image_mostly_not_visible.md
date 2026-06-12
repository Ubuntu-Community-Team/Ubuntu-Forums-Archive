---
title: "Playing video DVD, image mostly not visible"
date: 2012-09-21
forum: Multimedia Software
---

### Post by pwabrahams on 2012-09-21
I'm running Kubuntu 12.04 with libdvdcss, etc. installed.  I'm trying to play a DVD with a menu using **vlc**.  I can bring up the DVD menu with no difficulty.  But when I start to play the actual movie, I have sound but no image.

Now here's the really strange part.  If I move the window around by dragging it with the mouse, the image appears -- but only while I'm holding down the left mouse button.  I get essentially the same behavior with the Dragon Player.

What is going on here?

---

### Post by carl4926 on 2012-09-22
What graphics device do you have

---

### Post by pwabrahams on 2012-09-22
I'm running this on a Dell Inspiron 1000 laptop.

---

### Post by carl4926 on 2012-09-22
Open a terminal
Post the result of

```
inxi -F
```

---

### Post by pwabrahams on 2012-09-22
It took some doing because inxi is not on my system nor in my usual repositories, but here's the result:

> eva@Eva:~/Documents$ inxi -F
System:    Host: Eva Kernel: 3.2.0-31-generic-pae i686 (32 bit) Desktop: KDE 4.9.1 Distro: Ubuntu 12.04 precise
Machine:   System: Dell (portable) product: Inspiron 1000
           Mobo: Quanta model: Inspiron 1000 Bios: Dell version: A08 (Q3B01) date: 03/04/2004
CPU:       Single core Mobile Intel Celeron CPU (-UP-) cache: 256 KB flags: (sse sse2) clocked at 2191.269 MHz 
Graphics:  Card: Silicon Integrated Systems [SiS] 65x/M650/740 PCI/AGP VGA Display Adapter 
           X.Org: 1.11.3 drivers: sis (unloaded: fbdev,vesa) Resolution: 1024x768@60.0hz 
           GLX Renderer: Gallium 0.4 on llvmpipe (LLVM 0x300) GLX Version: 2.1 Mesa 8.0.4
Audio:     Card: Silicon Integrated Systems [SiS] SiS7012 AC'97 Sound Controller driver: snd_intel8x0 Sound: ALSA ver: 1.0.24
Network:   Card: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet driver: sis900 
           IF: eth0 state: up speed: 100 Mbps duplex: full mac: 00:11:43:47:ad:33
Drives:    HDD Total Size: 40.0GB (10.0% used) 1: id: /dev/sda model: FUJITSU_MHT2040A size: 40.0GB 
Partition: ID: / size: 37G used: 3.8G (11%) fs: ext4 ID: swap-1 size: 0.47GB used: 0.07GB (14%) fs: swap 
RAID:      No RAID devices detected - /proc/mdstat and md_mod kernel raid module present
Sensors:   System Temperatures: cpu: 54.0C mobo: N/A 
           Fan Speeds (in rpm): cpu: N/A 
Info:      Processes: 111 Uptime: 12:41 Memory: 259.2/430.4MB Client: Shell inxi: 1.8.4 

---

### Post by carl4926 on 2012-09-22
> Graphics:  Card: Silicon Integrated Systems [SiS] 65x/M650/740 PCI/AGP VGA Display Adapter 
There couldn't be a more useless make I can think of - sorry

---

### Post by pwabrahams on 2012-09-22
So you think it's a problem with the video hardware, then?  Any idea why the action of moving the window with the mouse and holding the mouse button down would cause the image to reappear?

Are there any experiments I might try to verify this hypothesis?

---

### Post by BicyclerBoy on 2012-09-22
You could try different video overlay methods or desktop effects manager..

If moving window/mouse changes the video redraw then there could be a window decorator/composite problem. Different video playback method could help..
In VLC preferences select advanced/full & then video tab..

Does full screen work better than windowed?
Could try settings in the composite effects manager used by KDE (KWin).
Is there a "unredirect full screen" option?

Some kubuntu installs (optional extra?) use compiz (ccsm).
Low end video cards probably can't support compiz or any bling/eye candy.

---

### Post by pwabrahams on 2012-09-22
I tried jiggling various settings, with no effect on the reduced view.  But the fullscreen view came alive, and that's good enough.  Thanks!!!

---

### Post by BicyclerBoy on 2012-09-22
I think that KWin has "un-redirect on full screen" as default (sensible)..

If you disable effects (composite) than video should (might) work in window..

---

