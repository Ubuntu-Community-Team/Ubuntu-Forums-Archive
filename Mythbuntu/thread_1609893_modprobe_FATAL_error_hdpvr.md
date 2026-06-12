---
title: "modprobe: FATAL: error hdpvr"
date: 2010-10-30
forum: Mythbuntu
---

### Post by phroman on 2010-10-30
Hello peoples, I'm unable to get my Hauppauge HD PVR to work in 10.10, fresh install, and would love some help. All of the hardware and associated settings worked in 9.10.

At boot up I see an error flash across the screen:

modprobe: FATAL: Could not load /lib/modules/2.6.35-22-generic/modules.dep: No such file or direcory.

In mythbackend I enter the capture card setup screen, it recognizes the HD PVR, I enter my known settings that worked with this HD PVR on my 9.10 system.  Exit out of the backend, shut down the computer, power cycle the computer and the HD PVR for 90 seconds, restart.  At the frontend, I click on Watch Live TV, the screen says please wait, its black, and I'm kicked back out to the main menu.  

At a terminal I type: cat /dev/video0 > test.ts and it successfully records a video file to my desktop, so somethings working.  It just seems that myth can communicate with the HD PVR.  

I have updated the firmware on a windows machine.  Here's a few command outputs:

dmesg | grep hdpvr

```
joe@mythserver:~/Desktop$ dmesg | grep hdpvr
[   12.661238] hdpvr 2-3:1.0: untested firmware version 0x15, the driver might not work
[   12.956875] hdpvr 2-3:1.0: device now attached to video0
[   12.956893] usbcore: registered new interface driver hdpvr
joe@mythserver:~/Desktop$ 

```

lsusb

```
Bus 002 Device 002: ID 2040:4902 Hauppauge HD PVR
```
 

Any ideas what's happening with this?  Thank you for any help.

---

### Post by phroman on 2010-10-31
Well, this is embarrassing.  I had the audio optical cable from my direct tv satellite receiver plugged in to the OUTPUT audio port of the HD PVR, not the input.  That was enough to break it in mythtv.  

With the voice of Joe from Family Guy:

CHECK YOUR PORTS PEOPLE !!



And the boot error I foud a fix here:

[http://ubuntuforums.org/showthread.php?t=1592311&page=2](http://ubuntuforums.org/showthread.php?t=1592311&page=2)

Post # 13 did it for me. Here's the bulk of it:


Edit /etc/initramfs-tools/initramfs.conf (sudo gedit /etc/initramfs-tools/initramfs.conf in the console) and change the line MODULES=most to MODULES=dep.

Then use Synaptic to reinstall initramfs-tools

Cheers!

---

