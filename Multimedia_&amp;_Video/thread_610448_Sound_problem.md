---
title: "Sound problem"
date: 2007-11-12
forum: Multimedia &amp; Video
---

### Post by Frogsmasher on 2007-11-12
I am experiencing a problem with my sound. My speakers are working and I am using an on-board sound card. I can get the normal feedback, and buzz from my speakers saying they are plugged in, but I can get no sound except buzzing to come out. I went to Youtube and tried to watch a video. I got the video but none of the sound. I tried to stream a video through totem media play no sound. and I tried to play an mp3 in totem, but no sound. I am a new Linux user, and have not been able to get the sound to work since I started.

---

### Post by rsambuca on 2007-11-12
The easiest thing to try first is to right-click the volume control on the top menu bar.  Then select "Open Volume Control".  Make sure PCM is turned up, as well as your Front levels.

---

### Post by Frogsmasher on 2007-11-12
Yeah every single bar is unmuted, and all the way up.

---

### Post by rsambuca on 2007-11-12
What is your soundcard?

---

### Post by Frogsmasher on 2007-11-12
I just have my onboard motherboard thats it.

---

### Post by Frogsmasher on 2007-11-12
I can copy the lspci for you if it will help

---

### Post by Frogsmasher on 2007-11-12
```
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 735 Host (rev 01)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] Virtual PCI-to-PCI bridge (AGP)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS85C503/5513 (LPC Bridge)
00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
00:02.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 07)
00:02.3 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 07)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev d0)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 90)
00:13.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 50)
00:13.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 50)
00:13.2 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 51)
01:00.0 VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200 SE] (rev 01)
01:00.1 Display controller: ATI Technologies Inc RV280 [Radeon 9200 SE] (Secondary) (rev 01)

```

---

### Post by rsambuca on 2007-11-12
I am not familiar with the SIS AC97.  Try checking out[ this thread]("http://ubuntuforums.org/showthread.php?t=205449"), as there is a lot of info there.

---

### Post by negerbarn on 2007-11-12
thanks!! really... everythings is not fixed though.. but i checked out the open volume control and now theres soun from the computer. not from my speakers though:(

---

### Post by Frogsmasher on 2007-11-12
Mines not fixed :( oh well if anyone has any ideas I am open to anything

---

### Post by Yellow Pasque on 2007-11-13
> **Frogsmasher said:**
> Mines not fixed :( oh well if anyone has any ideas I am open to anything

Try removing ALSA (deselect alsa-base in Synaptic).
Go [here](http://www.4front-tech.com/download.cgi) and select the x86 DEB package for Linux 2.6.x
Download the file and follow the installation instructions.
Report back here.

Note that your sound codec is supported by the SIS 7012 driver module.

---

