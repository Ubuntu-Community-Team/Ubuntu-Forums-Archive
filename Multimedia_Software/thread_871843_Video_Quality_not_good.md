---
title: "Video Quality not good"
date: 2008-07-27
forum: Multimedia Software
---

### Post by sam2501 on 2008-07-27
Somehow, the quality of videos played in ubuntu is lower compared to when it was played in windows

this prob isnt file specific or even player specific,because quality is low both on totem(gstreamer) & vlc 

i uninstalled totem(gstreamer) & vlc, and installed totem(xine)
but the problem persists

---

### Post by gjoellee on 2008-07-27
this might be the video you are running, but you should try using the latest gstreamer, or if this happens while watching youtube or something go and get flash 10BETA

---

### Post by sam2501 on 2008-07-27
the problem isnt file specific & also not with embedded videos

all kinds of videos show some quality lag

---

### Post by nikgare on 2008-07-27
Maybe you need to change you graphics driver?
Which card do you have and which driver are you using?

---

### Post by sam2501 on 2008-07-28
How to know which graphic card & graphic card driver i have?


it says ati-sapphire Radeon X550 256 PCI-E HYPER-M 512MB on the box of the graphic card


system->Adminstration->Hardware drivers  shows ATI accelerated graphics driver is in use


> $ lscpi    gave this


> 01:00.0 VGA compatible controller: ATI Technologies Inc Unknown device 5657
01:00.1 Display controller: ATI Technologies Inc Unknown device 5677
    relating to graphics or display

do i need really hardcore graphic cards for playing plain videos? i mean i thought the driver is supported good enough because my resolution is 1400*900,& i am running compiz-fusion with many effects enabled

my pc config is 

intel core 2 duo
1 gb ram
intel 945g motherboard
Ati graphic card....i guess that's it

Should i tweak some settings to make the videos run better?

---

### Post by sam2501 on 2008-07-28
And this is the output when i run glxgears in terminal

> $ glxgears
8172 frames in 5.0 seconds = 1634.260 FPS
9321 frames in 5.0 seconds = 1864.175 FPS
8460 frames in 5.0 seconds = 1691.933 FPS
8916 frames in 5.0 seconds = 1783.065 FPS
8918 frames in 5.0 seconds = 1783.579 FPS
8665 frames in 5.0 seconds = 1732.929 FPS
8654 frames in 5.0 seconds = 1730.718 FPS

the gears are flickering a bit though
is this performance good ? what should i do to make it better?
ask me if you need any other info...i need this problem cleared for good

---

### Post by nikgare on 2008-07-28
I think you probably need the Ati drivers installed, I think it's this one:
**xserver-xorg-video-radeonhd**
Install it via synaptic, reboot and see if it helps.
Alternatively, you could install **envy** via synaptic, which should do a similar thing.

---

