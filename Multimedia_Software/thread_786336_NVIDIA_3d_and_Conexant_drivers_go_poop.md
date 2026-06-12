---
title: "NVIDIA 3d and Conexant drivers go poop"
date: 2008-05-08
forum: Multimedia Software
---

### Post by Sin@Sin-Sacrifice on 2008-05-08
Alrighty... seems like no matter how many times I try... I can't get anywhere on ubuntu when it comes to getting everything I can out of this HP m8000n PC. It came with a wintv card that has a lot of features incliding 2 RCA ins, 2 S-Videos, radio, satellite, and cable ins. Well... I wanted to play my playstation on the PC while the wife watches her shows and while I can do that on Craprosoft Bricked windows by just plugging it in and starting up Dscaler... I had to do some tweaking with the software and firmware in ubuntu. Regardless.... when I finally got it working, sort of... still blurry, by installing the conexant drivers and such... it stopped my nvidia drivers from working. Well.. the 3d stuff anyway. I can still get a display but all my toys went away including conky and wobbly windows.:(  I looked in the restricted drivers manager and they are turned off. I also tried turning them back on and well.... that was almost tragic. Starting with the fact that I almost couldn't log back in because I couldn't see the log in prompt. HA... If anyone knows anything about this please...help. I have the Hauppauge WinTV HVR-1600 - ATSC HDTV and the NVIDIA GeForce 6150 chipset (on-board piece of crap)

---

### Post by dblade on 2008-07-16
According to post #20 in [http://ubuntuforums.org/showthread.php?t=813429&highlight=hvr-1600](http://ubuntuforums.org/showthread.php?t=813429&highlight=hvr-1600) there are  "vmalloc=192M pci=nommconf" kernel options you can try.

Please report back if you do/have tried this.

---

