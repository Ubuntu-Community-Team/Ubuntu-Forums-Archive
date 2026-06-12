---
title: "Intel 945GM with additional drivers installed"
date: 2009-04-16
forum: Multimedia Software
---

### Post by hebeallrusty on 2009-04-16
I am using Jaunty with an Intel graphics card running the UXA acceleration method. It gives much better performance than EXA and has only crashed a few times in the past couple of weeks. 
My question though is that looking in Synaptic at the video drivers that are installed, I find that there are lots of them that have check marks by them. For example the following are installed:
xserver-xorg-video-all
xserver-xorg-video-ati
xserver-xorg-video-intel
xserver-xorg-video-mach64
xserver-xorg-video-radeon
xserver-xorg-video-sis
... and the list goes on. Is it really necessary to have them all installed, and are they interfering with each other? lspci reports that I have a:
```
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller [8086:27a2] (rev 03)
```
graphics card. Any light on the matter would be greatly appreciated. Thanks

---

### Post by hebeallrusty on 2009-04-17
The following drivers are installed:
(all begining with xserver-xorg-video- in Synaptic):
all
apm
ark
ati
chips
cirrus
fbdev
i128
intel
mach64
mga
neomagic
nv
openchrome
r128
radeon
rendition
s3
s3virge
savage
siliconmotion
sis
sisusb
tdfx
trident
tseng
v4l
vesa
vmware
voodoo

Any light on the matter would help. Thanks

---

### Post by eldragon on 2009-04-17
those are all drivers installed by default in order to cover the biggest population possible. it doesnt mean you use them all.

for instance, ive only got installed vesa, fbdev and intel, the first two are in case the intel driver fails in an update (although im quite used to the command line)

i dont know if removing those not in use will cause any side effects in ubuntu, i'd advice you to leave them as is (they dont take much space me thinks).... but if you know how to undo your mistakes, go ahead and remove them, restart x and report back just to leave a log on what can happen ;)

---

### Post by hebeallrusty on 2009-04-18
I think I'll leave alone then. I was mainly curious really as to why they were all installed. I thought that they'd mistakenly been installed on the upgrade to Jaunty, so now I know not to worry. Thanks for your time.

---

### Post by VMC on 2009-04-18
Thanks for bringing this to my attention. I'm having issues with no video playback on my integrated intel i856 chip. Using this xserver-xorg-video- in Synaptic I found that intel in installed. Using that didn't help, but vesa driver allows me to play movies, but only 640X480. Weird. It works in Harty but not in Jackalope.

---

