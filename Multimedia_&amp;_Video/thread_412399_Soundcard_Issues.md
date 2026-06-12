---
title: "Soundcard Issues"
date: 2007-04-18
forum: Multimedia &amp; Video
---

### Post by mrfredman on 2007-04-18
I have been trying for weeks but I am still unable to get any sound out of my computer. I have been googling for solutions for hours, and while I have narrowed down my problem, but I think its unique, or rare enough that there is no solution. 

First of all I'm running Ubuntu edgy 6.1 with KDE.

Here's my lspci

00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 04)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 04)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 04)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 04)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 04)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d4)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 04)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 04)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 04)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 04)
02:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5789 Gigabit Ethernet PCI Express (rev 11)
06:07.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
06:07.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
06:07.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
06:07.4 Class 0805: Texas Instruments PCI6411, PCI6421, PCI6611, PCI6621, PCI7411, PCI7421, PCI7611, PCI7621 Secure Digital (SD) Controller
06:09.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)


So my soundcard seems to exist there, but I can't get kmix, or any of my other sound card configuration programs to recognize it. Any help? Whats the next step?
What questions can I answer to help narrow down my problem before.

Note: One thing that may be contributing to this issue is that my soundcard a conexant ac-link is unsuported on linux, but people seem to have found ways to get around this.

---

### Post by deadgobby on 2007-04-18
[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

---

### Post by mrfredman on 2007-04-18
So that link was a great start, but in the end, couldn't fix my problem. I downloaded the newest versions of alsa, which I didn't have before. But my latest problem is that I cant get alsa to run. When I type alsamixer in the command line this is what I get:

alsamixer: function snd_ctl_open failed for default: No such device

Does this mean I installed it wrong? Or is this still a hardware issue or something?

Kmix is currently my default audio mixer (Im running KDE), And that refuses to recognize any soundcards, but my other question is: How to I make alsa my default sound mixer? Because whenever I hit the volume up or down keys on my keyboard kmix automatically opens.

Help?

---

### Post by scott_kirkwood on 2007-04-21
Ok I get the same error but I've discovered something weird:
```

scott@scott-desktop:~$ alsamixer

alsamixer: function snd_ctl_open failed for default: No such device
scott@scott-desktop:~$ sudo alsamixer

alsamixer: function snd_ctl_open failed for default: No such device
scott@scott-desktop:~$ sudo su
root@scott-desktop:/home/scott# alsamixer

root@scott-desktop:/home/scott# 

```
If I'm root the alsamixer work, otherwise it doesn't.

```

scott@scott-desktop:~$ ls -la /dev/dsp /dev/audio /dev/mixer
crw-rw---- 1 root audio 14, 4 2007-04-21 10:08 /dev/audio
crw-rw---- 1 root audio 14, 3 2007-04-21 10:08 /dev/dsp
crw-rw---- 1 root audio 14, 0 2007-04-21 10:08 /dev/mixer
scott@scott-desktop:~$ groups
scott audio admin
scott@scott-desktop:~$ 

```
One post somewhere recommended adding yourself to the audio group, but the instructions were flawed and it took me out of the admin group and I had no sudoers privileges - no fun (but I learned some new things!).

Anyway, still no alsa, sound works just not any alsa sound.

---

### Post by sgx on 2007-04-21
please just save your sanity and get a cheap-as-in-price ice envy24 chip   soundcard/usb soundcard...linux is backwards: you must buy specific hardware for your OS...those on
the dark side must buy hardware -AND- software for their rental-copy OS...

[http://www.hydrogenaudio.org/forums/lofiversion/index.php/t52773.html](http://www.hydrogenaudio.org/forums/lofiversion/index.php/t52773.html)

this links to a short thread of a successful buyer...great site for audio
...also
[www.headfi.com](www.headfi.com) is great...many smart audio and linux folk in those forums

---

### Post by scott_kirkwood on 2007-04-22
Fixed:
Solution was to 
```

rm ~/.asoundrc
```

I found the problem by doing
```

strace -eopen alsamixer
```
And noticing that it was loading ~/.asoundrc. something in that file was screwing up my sound.

---

### Post by skrimpy on 2007-04-23
> **scott_kirkwood said:**
> Fixed:
Solution was to 
```

rm ~/.asoundrc
```

I found the problem by doing
```

strace -eopen alsamixer
```
And noticing that it was loading ~/.asoundrc. something in that file was screwing up my sound.

Thanks so much.  I was helping a very frustrated friend troubleshoot his sound troubles and this solution got his sound working.  Most pleased.  I don't know what that little file is but this solution should perhaps be added to the sound sticky?

---

