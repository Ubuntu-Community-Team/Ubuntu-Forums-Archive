---
title: "NVidia Graphics Dell XPS M170"
date: 2010-03-14
forum: Multimedia Software
---

### Post by dfwsupergeek on 2010-03-14
I've been pulling out my hair about this one. I'm working with a Dell XPS, nVidia GeForce GO 6800 graphics card. The laptop is very cool, with a nice, big screen- HOWEVER, I cannot get the resolution right on it. 
It's stuck on 1280x1050, which distorts images- making circles look like ovals- I've tried everything I've been able to find in forums I've lost count of, and the same kind of thing happens every time.
I install the nVidia driver- restart the computer- and it will not boot. At best, I get a garbled screen full of random crap- at worst, the machine will not boot, and I have to use the live CD to rescue it. Regardless, I am back at square one, meaning I'm using the vesa drivers, which gives me a nice, crisp picture which is distorted horizontally.
Does ANYONE know what I'm missing? 
I've tried using the drivers included with the nVidia tool, when that didn't work, I've downloaded and used the clock tool to make sure the graphics card is set to the factory settings, and even downloaded the newest driver from nVidia, installed it according to the instructions on the nVidia (and Ubuntu) forums... 
What am I missing? Thanks for any help! 
PS- if anyone can give me some insight to why I can't import video via firewire from a JVC camcorder, that would be a huge help too...

---

### Post by dfwsupergeek on 2010-04-02
I followed the steps I found somewhere else on this forum, and have made some progress- now, I have the correct resolution, but it's completely by accident- and no output on the vga or dvi ports, and no accelerated effects either... 
Any insight would be greatly appreciated! 
ps- to fix it this far, I did a search for all .ko files and .so files with nvidia in the name, and deleted them... when I rebooted, the vesa driver tells me Ubuntu is running in low graphics mode, and once I boot, I have the right resolution- but technically no driver installed, and a resolution that causes me to get a message saying the x server doesn't support that resolution.

---

### Post by RedSingularity on 2010-04-02
How exactly did you go about installing the graphics drivers?

---

### Post by dfwsupergeek on 2010-04-21
I actually REMOVED them... after uninstalling them, on some advice I found in this forum or another... 
After uninstalling the driver, I deleted all the folders with the name nvidia, and when I rebooted, I got an error message saying Ubuntu is running in low graphics mode, but at least the resolution is correct... 
I'm trying again- and at least have a picture, which I didn't before, but it's acting as though the nvidia driver hasn't been installed, and a search for nvidia.ko gives no results... 
This is kind of starting to p**s me off, I don't mind saying... though not enough to go back to Windows... 
;)

---

