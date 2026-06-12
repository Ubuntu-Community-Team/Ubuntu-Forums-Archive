---
title: "Intel G35 HDMI - No output"
date: 2008-10-12
forum: Multimedia Software
---

### Post by luckythedonkey on 2008-10-12
Hi All,

Apologies if this is in the incorrect section.

I have an Asus P5E-V HDMI board which uses the Intel G35 video chipset. I'm trying to get the HDMI port to work. I find that there is display up until X starts. I guess it drops out when the video driver is loaded. The TV doesn't say out of range so I'm not sure exactly what is happening.

The TV is an Acer AT3705 which is capable of 1080 resolution but I'm not too concerned about that.

I have done some reading up and other people have encountered similar issues but I think this might be a simple one. I'm using Ubuntu Hardy and my installation, including xorg.conf is stock standard. No drivers have been replaced or upgraded yet and I haven't edited my xorg.conf yet.

Can anyone point me in the right direction to troubleshoot this? I'm not very experienced with this. I have looked for the "ddcprobe" utility but I can't seem to find it. I can provide a copy of my xorg.conf if you'd like.

Thanks a lot.
Justin

---

### Post by luckythedonkey on 2008-10-15
cool thanks

---

### Post by Chuffinora on 2008-11-29
Hi,

  Did you find a solution?  I  have just bought this motherboard and am setting up a MythTV HTPC system. 

I have the exact same problem as you described.  

I am running Ubuntu 8.10, and am connected to an LG 42" LCD TV (720P resolution) and it boots up ok, then (When switching to X) displays INVALID FORMAT

I  ssh into my box and ran ddcprobe and got this output  (Which all seems ok)

vbe: VESA 3.0 detected.
oem: Intel(r)Q965/Q963/G965 Graphics Chip Accelerated VGA BIOS
vendor: Intel Corporation
product: Intel(r)Q965/Q963/G965 Graphics Controller Hardware Version 0.0
memory: 7616kb
mode: 1280x1024x256
mode: 1280x1024x64k
mode: 1280x1024x16m
mode: 1024x768x256
mode: 1024x768x64k
mode: 1024x768x16m
mode: 640x480x16m
mode: 800x600x64k
mode: 800x600x16m
mode: 640x480x256
mode: 800x600x256
mode: 640x480x64k
edid: 
edid: 1 3
id: 0001
eisa: GSM0001
serial: 00002cae
manufacture: 8 2006
input: analog signal.
screensize: 82 46
gamma: 2.200000
dpms: RGB, no active off, no suspend, no standby
timing: 720x400@70 Hz (VGA 640x400, IBM)
timing: 720x400@88 Hz (XGA2)
timing: 640x480@60 Hz (VGA)
timing: 640x480@67 Hz (Mac II, Apple)
timing: 640x480@75 Hz (VESA)
timing: 800x600@60 Hz (VESA)
timing: 800x600@75 Hz (VESA)
timing: 832x624@75 Hz (Mac II)
timing: 1024x768@87 Hz Interlaced (8514A)
timing: 1024x768@75 Hz (VESA)
timing: 1280x1024@75 (VESA)
ctiming: 640x480@75
ctiming: 800x600@75
ctiming: 1024x768@75
dtiming: 1024x768@74
monitorrange: 30-61, 56-75
monitorname: 42LC2D-UD

---

