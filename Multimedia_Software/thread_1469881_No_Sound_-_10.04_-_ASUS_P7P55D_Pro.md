---
title: "No Sound - 10.04 - ASUS P7P55D Pro"
date: 2010-05-02
forum: Multimedia Software
---

### Post by J.L.C. on 2010-05-02
I just built a system with an ASUS P7P55D Pro board and I do not have any sound output with Lucid 10.04 64-bit (base was the release candidate all updates are up to date).

I am running a VirtualBox of Win7 64-bit, which plays sound just fine. So I'm assuming it's a driver issue of some sort.

Sound chip is the VIA VT1828S HD audio chip.

In alsa preferences, I only have the option of analog inputs and outputs

uname - a 

Linux desktop 2.6.32-22-generic #33-Ubuntu SMP Wed Apr 28 13:28:05 UTC 2010 x86_64 GNU/Linux

aplay -l

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: HDA Generic [HDA Generic]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.21.

head -n 1 /proc/asound/card*/codec#*
Codec: VIA ID 4441


Anyone else come across this or have a fix?

---

### Post by lidex on 2010-05-02
Go here:
[http://ubuntuforums.org/showpost.php?p=9136618&postcount=2]("http://ubuntuforums.org/showpost.php?p=9136618&postcount=2")
Follow the direction there to upgrade alsa to 1.0.23
When done: Check your levels in alsamixer.
```
 alsamixer 
```
Press F6 to select the correct soundcard.
Press F3 to show playback levels. F4 selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels.
Go to "System>Preferences>Sound" and make sure the correct soundcard is default.

---

### Post by ojuano on 2010-09-03
> **J.L.C. said:**
> I just built a system with an ASUS P7P55D Pro board and I do not have any sound output with Lucid 10.04 64-bit (base was the release candidate all updates are up to date).
 
I am running a VirtualBox of Win7 64-bit, which plays sound just fine. So I'm assuming it's a driver issue of some sort.
 
Sound chip is the VIA VT1828S HD audio chip.
 
In alsa preferences, I only have the option of analog inputs and outputs
 
uname - a 
 
Linux desktop 2.6.32-22-generic #33-Ubuntu SMP Wed Apr 28 13:28:05 UTC 2010 x86_64 GNU/Linux
 
aplay -l
 
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: HDA Generic [HDA Generic]
Subdevices: 0/1
Subdevice #0: subdevice #0
 
cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.21.
 
head -n 1 /proc/asound/card*/codec#*
Codec: VIA ID 4441
 
 
Anyone else come across this or have a fix?
 
 
Here is my solution:
 
[http://ubuntuforums.org/showthread.php?t=1567023&highlight=p7p55d](http://ubuntuforums.org/showthread.php?t=1567023&highlight=p7p55d)

---

### Post by anttir on 2011-08-17
> **lidex said:**
> Go here:
[http://ubuntuforums.org/showpost.php?p=9136618&postcount=2](http://ubuntuforums.org/showpost.php?p=9136618&postcount=2)
Follow the direction there to upgrade alsa to 1.0.23
When done: Check your levels in alsamixer.
```
 alsamixer 
```Press F6 to select the correct soundcard.
Press F3 to show playback levels. F4 selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels.
Go to "System>Preferences>Sound" and make sure the correct soundcard is default.

Thanks for this. I already did this once and forgot how to do it. I had to choose "Independent" Off with cursor down and move the Front levels up. I have my Soundworks connected to Headphone Out due to PC Chassis limitations.

---

