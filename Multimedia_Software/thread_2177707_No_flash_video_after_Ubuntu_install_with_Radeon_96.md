---
title: "No flash video after Ubuntu install with Radeon 9600XT"
date: 2013-09-30
forum: Multimedia Software
---

### Post by bmass on 2013-09-30
I'm trying to set up Ubuntu 12.04.3 on my 10+ years old desktop with AMD Barton 3200+ processor and ATI Radeon 9600XT video card. 

I'm having a couple issues, but the main one that I'm trying to address in this thread is an inability to play any sort of flash video.

I have a vanilla install, fully updated, third part software included with installation, ubuntu-restricted-extras installed. I am using the open source drivers because I understand that ATI no longer supports proprietary drivers for this video card.

I have tried installing Ubuntu 12.10 and Ubuntu 13.04 on the same machine and had the same issue.

In firefox the black screen the size of the video window loads but nothing more.

In chrome there is a gray screen the size of the video window with a puzzle piece that says "Couldn't load plug-in."


Other solutions I've tried from research that worked for other people but did not work for me:

sudo apt-get install hal 

rolling back to different version of adobe flash player (in the past I tried a bunch of different versions that people had reported working, but to no avail)


If anyone can offer any suggested solutions I would be eternally grateful. Please let me know if I can provide any more information. Thanks.

---

### Post by bmass on 2013-09-30
I should also mention I'm currently using YouTube and DailyMotion to test this.

I just tried:

sudo apt-get remove flashplugin-installer

and now I've got DailyMotion ONLY working Chrome ONLY.

I'm  not sure why. I'm on my way out the door to work. With no flash plugin,  DailyMotion works in Chrome. No other flash is working. I will try some  other sites and more trouble-shooting when I get back from work. Thanks  for reading.

---

### Post by gordintoronto on 2013-10-01
Run this command: lshw -c cpu

It will show the "capabilities" of your CPU. I think they will not include "sse2" which the current version of the Adobe Flash Player requires. If you can find version 10.2 of the plugin, it should work. (And please let me know where you found it!)

---

### Post by bmass on 2013-10-10
```
cheesehammer@cheesefactory:~$ sudo lshw -c cpu
[sudo] password for cheesehammer: 
  *-cpu                   
       description: CPU
       product: AMD Athlon(tm) XP 3200+
       vendor: Hynix Semiconductor (Hyundai Electronics)
       physical id: 4
       bus info: cpu@0
       version: 6.10.0
       slot: Socket A
       size: 2200MHz
       capacity: 3GHz
       width: 32 bits
       clock: 200MHz
       capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 mmx fxsr sse syscall mmxext 3dnowext 3dnow cpufreq
```

So sse2 is not listed as you expected.

I've been running Ubuntu now with flash uninstalled and it seems that I can get videos to play when I refresh enough times... or sometimes. I haven't quite figured out how to make it work, but videos play sometimes. No flash installed. I will have to get back to you on tracking down flash 10.2

---

### Post by Yellow Pasque on 2013-10-11
[http://ubuntuforums.org/showthread.php?t=2179125&p=12812819#post12812819](http://ubuntuforums.org/showthread.php?t=2179125&p=12812819#post12812819)

---

