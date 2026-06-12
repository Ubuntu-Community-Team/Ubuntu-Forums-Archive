---
title: "No sound."
date: 2007-08-03
forum: Multimedia &amp; Video
---

### Post by Yookji on 2007-08-03
I have a fresh installation of feisty and get no sound from any application. Ubuntu detects my sound card but for some reason or another it won't play.
```
keith@ubuntu:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
keith@ubuntu:~$ lspci
00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:05.0 VGA compatible controller: nVidia Corporation C51 PCI Express Bridge (rev a2)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.3 Co-processor: nVidia Corporation MCP51 PMU (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev f1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
06:09.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller (rev 20)
```

EDIT: I checked alsamixer and got this:
[http://img301.imageshack.us/img301/5805/screenshotkeithubuntuuu9.png](http://img301.imageshack.us/img301/5805/screenshotkeithubuntuuu9.png)

---

### Post by Yookji on 2007-08-05
I am still soundless after searching google and the forums for solutions over the past couple days. Any help is appreciated.

---

### Post by Xzenome on 2007-08-05
This may or may not help, but on one computer I was setting up for some reason alsa didn't work. Anyway to cut a long story short I went into System > Preferences > Sound and screwed about with it (just randomly changing options) and through trial and error I managed to get it working. I've got no idea whether this will work for you, but I suppose it's worth a try.

---

### Post by ronny_d on 2007-08-05
Maybe try in but of course a terminal:

sudo asoundconf list


That would make you see your soundcards in the first place.

---

### Post by lisati on 2007-08-05
I had no sound on my laptop when I first installed Ubuntu - part of the solution was to install the updates, and part was to reset the volume control.

---

### Post by ronny_d on 2007-08-05
Yeah,  aplay -l ... . 
is it really 'exactly' the same as sudo asoundconf list
?


What is the "analog device" through which you receive sound / audio from your computer?

---

### Post by ronny_d on 2007-08-05
What is the "analog device" through which you receive sound / audio from your computer? "Modern"... computers do mostly nomore have built in sound only from the computer (no extra boxes plugged in, et cetera) as before (has "nothing to do with" soundcard built in).  And up the corner on the computerscreen of Feisty Fawn must be a 'sound symbol', click on it and check whether it is on "+". Too see and/or adjust with system > preferences > audio indeed all possible options and see if any of the given options there work and try out the options for the device...., then you could check whether with sudo  asoundconf list for example the same soundcard is given as what is working once you found 'sound' possibility by trying out the options, et cetera.  

But if the above does not give any sound with all possible options you have tried and the various devices, then... are you sure nvidia is totally "communicating"? Maybe then it is a problem with nvidia if all i mentioned above does not work to give you any sound as via headphone or something... Then check information on the web about nvdia in your system whether all is really supported or not.

---

### Post by Yookji on 2008-01-12
Update: I'm still unable to fix the problem in gutsy, but I burned a copy of hardy alpha 3 and the sound worked on the livecd. I assume this is because the developers have made drivers for my laptop's (relatively) new hardware. Is there any way to use this on gutsy?

---

### Post by wolfen69 on 2008-01-13
you could add a hardy repo and take your chances.

---

### Post by Yookji on 2008-01-14
I did that, and upgraded alsa-base, alsa-utils and linux-sound-base, but still no sound. Is there anything else I need to upgrade? The new kernel perhaps?

---

