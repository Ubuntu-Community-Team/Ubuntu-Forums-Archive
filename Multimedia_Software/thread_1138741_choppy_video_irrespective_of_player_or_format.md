---
title: "choppy video irrespective of player or format"
date: 2009-04-26
forum: Multimedia Software
---

### Post by khizar on 2009-04-26
i need some help here. i was using hardy until yesterday and life was sweet.i did a clean jaunty install today n now i have a problem. the video at first was not playing irrespective of the format. i went to system->prefs->multimedia selecter n in the video tab the default output was autodetect. i pressed the test button n it crashed or sumthing i.e it just (the multimedia selector window) disapeared.so i again opened it n changed the autodetect option to X Window System(x11/xShm/xv) n again it crashed on test. now i changed it to X Window System(no xv) n did the test n thr was a small screen with colored bars watever to show the test result is gud. so now i come back n run videos n they a choppy like the computer is really slow or sumthing , n they also take a lot of cpu. (all this same for diffrent formats n players). so now i am at a dead end n need asistance.
BTW i have 2.4Ghz intel cpu , an intel d865 motherboard n 512mb ram.no external video card. 
ny help will be graetly appreciated.

cheers 
khizar

---

### Post by inobe on 2009-04-26
post your 

```
lspci
```

tell us about the video player and the format you are trying to play.

tel us about your video driver, we need the version currently installed.

---

### Post by khizar on 2009-04-26
> khizar@khizar-desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
01:00.0 Multimedia audio controller: Avance Logic Inc. ALS4000 Audio Chipset
01:02.0 Communication controller: Agere Systems 56k WinModem (rev 01)
01:08.0 Ethernet controller: Intel Corporation 82562EZ 10/100 Ethernet Controller (rev 01)


 i have tried it on totem , vlc n mplayer.n i have played .avi , .wmv, .mp4 , .mpg. all with the same choppy results.vlc is just a little better as it doesnt take the cpu usage to 100% as is teh case with totem but still the video is chopy.

> tel us about your video driver, we need the version currently installed
i havnt installed any , never had to in gutsy n hardy n they worked great. i dun know how can i tell wat is installed by default.

---

### Post by inobe on 2009-04-26
there is a thread in this forum specific to intel graphics, it's probably on the second page.

your video driver is the problem.

---

### Post by inobe on 2009-04-26
hey i think this is it, this should save you a search.

[http://ubuntuforums.org/showthread.php?t=1130582](http://ubuntuforums.org/showthread.php?t=1130582)

goodluck

---

### Post by khizar on 2009-04-27
thanx alot . the how to looked a bit scary but i tried n it worked. just one more question.i cant seem to add my monitor , the detect monitor buton in Display doesnt work, can i add it somehow through command line? i have an LG 505G.

---

### Post by VMC on 2009-04-27
> **khizar said:**
> thanx alot . the how to looked a bit scary but i tried n it worked. just one more question.i cant seem to add my monitor , the detect monitor buton in Display doesnt work, can i add it somehow through command line? i have an LG 505G.
I'm surprised that it worked for you, since you have the exact Intel chip that I have. "VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)"

The only one that worked for me was [[COLOR="Lime"]**this**[/COLOR]]("https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4") one. It rolled back Intel driver.

I tried this [[COLOR="Red"]**fix**[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1130582") that you mentioned, and it failed miserably. 
Interesting. Also I don't like the RCx kernel that is recommended. I see nothing on either logon or logoff.

---

