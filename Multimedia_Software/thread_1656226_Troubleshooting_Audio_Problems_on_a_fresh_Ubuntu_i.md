---
title: "Troubleshooting Audio Problems on a fresh Ubuntu install."
date: 2010-12-30
forum: Multimedia Software
---

### Post by WinterCarroll on 2010-12-30
Hello Ubuntu Community. I recently made the switch to Ubuntu with an older laptop of mine and while I find the OS itself quite effective, I found that my audio was not working. To start, some minor specs on my laptop: It is a Gateway M210, stock with the exception of a 120GB HDD and 1GB Ram in the expanded slot on top of the on board 256. And I doubt it matters, but the screen has been replaced. It used to run Windows XP Professional and the audio worked fine, I am working with Ubuntu 11.04. I started looking for help with this thread: [Comprehensive Sound Problem Solutions Guide v0.5e]("http://ubuntuforums.org/showthread.php?t=205449"). Now I started from the top, and I even reinstalled Ubuntu as suggested because it might have been a bug, but to no avail. I'll explain everything I've done to see if it helps.

First off, to avoid feeling stupid, I've made sure the physical volume is up, as well as checking alsamixer. None of my channels are muted, and they all are at appropriate volume levels.

So, on step one, this is what I get as a response:
```
aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 0: Intel ICH [Intel 82801DB-ICH4]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 4: Intel ICH - IEC958 [Intel 82801DB-ICH4 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```Which explained to me that my card was detected, and so my adventure into alsamixer to make sure none of my channels were muted.

So in step two, I'll trim down what I got back since we are only interested in my multimedia.
```
lspci -v
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
    Subsystem: Rioworks Device 203e
    Flags: bus master, medium devsel, latency 0, IRQ 17
    I/O ports at 1c00 [size=256]
    I/O ports at 18c0 [size=64]
    Memory at e0100c00 (32-bit, non-prefetchable) [size=512]
    Memory at e0100800 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: Intel ICH
    Kernel modules: snd-intel8x0
```And that is where I stopped. At step three, the link provided does not lead to where I'm sure it is meant to. So I am wondering if someone knows were this site has moved, or even easier, if the above information well let them help me continue my way through this guide or perhaps even direct me to my fix. I appreciate anyone who can help me out. Thanks.

---

### Post by lidex on 2010-12-30
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by WinterCarroll on 2010-12-30
Thank you lidex. I appreciate your help. I ran the script and here is the link for my ALSA information: [http://www.alsa-project.org/db/?f=11e59277228f25e2f878d44d37272b6e6dc75e31](http://www.alsa-project.org/db/?f=11e59277228f25e2f878d44d37272b6e6dc75e31)

Not sure exactly what I am looking at sadly. Could you explain the output file to me so I can better understand?

---

### Post by lidex on 2010-12-30
Threads that I've seen for this comp for the most part point to 'external amplifier' option. First open 'sound preferences'. Click the speaker icon in the panel and select it. On the hardware tab make sure the correct device is selected and down below use the drop-down menu to select/toggle the profile. Look for "Analog Output / No Amplifier". If that doesn't work, install gnome-alsamixer. 
**Gnome-alsamixer**
Using Alt+F2 run dialog
```
 gnome-alsamixer 
```
**Use 'Edit -> Sound Card Properties' menu to enable elements.** Enable 'external amplifier' or eapd there.
Soundcard tab to select / adjust levels. Uncheck 'external amplifier' or eapd there.
To install:
```
sudo apt-get install gnome-alsamixer
```

---

### Post by WinterCarroll on 2010-12-30
Lidex, my hat is off to you. You have gotten me farther than anyone so far. But there is still a problem. I installed gnome-alsamixer and fixed the external amplifier situation, and the audio works now, but only while I have headphones on. Not sure why it is being selective., but maybe you can put up with my inexperience a little longer and help me figure out how to get full audio.

---

### Post by lidex on 2010-12-30
In sound preferences, the output tab, for 'Connector', make sure analog output/speakers is selected - not headphone.

---

### Post by WinterCarroll on 2010-12-30
I have it set as that and no luck. Here is a brief run-down of my Sound Preferences right now:
- Output Volume 100%
- Hardware: Internal Audio, Profile: Analog Stereo Duplex
- Input: Internal Audio Analog Stereo
- Output: Internal Audio Analog Stereo, Connector: Analog Output/No Amplifier
- Applications: Nothing.

---

