---
title: "Jetway NC62K (Geforce 8200 with ALC883) - Intermittant white noise"
date: 2008-08-04
forum: Multimedia Software
---

### Post by Lem on 2008-08-04
I've got one of the jetway nc62k mini-itx boards with the nvidia geforce8200 chipset using a realtek 883 for audio.

Problem is that I get intermittant white noise during audio playback.

lspci | grep Audio gives;
00:07.0 Audio device: nVidia Corporation Unknown device 0774 (rev a1)

and aplay -l gives;
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

I've tried the latest ALSA drivers, so any other help would be appreciated!

---

### Post by nylan on 2008-08-16
Hello, I'm having a similar problem with the same board.

Using iec958 as output:
- works perfectly for movies, dvd, etc
- doesn't work for mp3 (distortion, reverb)

The solution presented here didn't work at all:
[http://www.mythtv.org/wiki/index.php/Intel_HD_Audio_-_Realtek_ALC88x](http://www.mythtv.org/wiki/index.php/Intel_HD_Audio_-_Realtek_ALC88x)

Have you found a solution?

---

### Post by celem on 2008-08-19
I have the same problem with a new BioStar mobo. I tried the two shell script solution with no results. I also installed the Linux driver from the RealTek site and it totally ruined X and I had to reload.

---

### Post by nylan on 2008-08-21
I didn't have any problems installing the realtek drivers, but with the  same result:
mp3 playback doesn't work.

I'm going to write to the alsa mailing list about this issue.

---

### Post by kashew on 2008-08-22
Hello everybody,
I'm sorry to ask in this thread, but how exactly did you install Ubuntu on the nc62k?
I built a new pc with this mainboard but I can't figure out how to install Ubuntu 8.04 on it.
I tried with an old 8.04 live cd and even with the 8.04.1 alternate cd.
My problem is that my pc freezes when I hit enter in the cd menu and all I get is a blinking cursor in the top left corner and the cd stops spinning after a few seconds.

Do you have some advice for me? Where can I find a manual to put the 2.6.25 kernel onto the live cd to use as main kernel?
I've read somewhere that 2.6.25 should support the new nvidia chipset.

Thanks for any advice.

---

### Post by nylan on 2008-08-26
try following boot parameter:
generic.all_generic_ide=1

Just press F6 and add the additional parameter.

You have to build a new kernel. >2.6.25-r7 
Actually i'm using kernel 2.6.26-r1

---

### Post by celem on 2008-08-30
This isn't a Ubuntu issue, it is a Linux issue. I have loaded Ubuntu, and Sabayon Linux and the problem is in both releases. Windows XP works fine, so the sound device itself is fine. The suggested kernel option did nothing for me.

In my case, the ALC888S is on a BioStar TF8200 A2+ motherboard, but my lspci gives the same "*00:07.0 Audio device: nVidia Corporation Unknown device 0774 (rev a1)*".

The audio works but is very noisy, i.e., scratchy and distorted, at times seeming to go into a reverberation.

---

### Post by kashew on 2008-09-01
Thanks for your help nylan.
The suggested boot option was not recognized, so celem is right.
But I got the NC62K to install with the boot parameter: acpi=off
I don't know if it was an occasional bug, but my usb mouse didn't work after install, I had to append "noapic" as boot option too.
Later it worked without any boot option at all. :confused:

Anyway, I compiled the new 2.6.26.3 kernel. *yeah* proud of myself :lolflag:
Well, now it works without boot parameters.
lspci still shows a lot of nvidia unknown devices, is this normal behavior? Thought it should show the correct names, or are they mapped somewhere else in a file?

The graphics driver installed just fine, no errors so far.

Sound problems: I was only able to test it with a cheap headset but I heard some crackling and hiccups. I wouldn't call it white noise. Even though it's a cheap headset it seemed to be an OS problem.
Still have to test it with S/PDIF out, but for this I have to get a TOSLINK/Stereo Jack Adapter first.
Problem is, I don't have much time for testing at the moment.

Isn't there a way to get an electrical S/PDIF out of the sound-chip?

---

### Post by kdwillia on 2008-09-09
I have a Biostar TF720 A+.   Was able to install using the "noapic pci=msi" when I was booting the live cd.   Also had to boot into safe graphics mode because my Nvidia 8500 wasn't liked.  

As for my sound, I too have the scratchy / white noise.   I have noticed that it only occurs when the CPU load goes below 10%.   If it stays above that... works fine and the sound is good.  I have to say I am a little stumped on why it would do that when the CPU is not in heavy use.

---

### Post by u!mp3 on 2008-09-11
I was having the same problem with an Asus M3N78-EMH HDMI geforce 8200, ALC883

I was using the latest bios, the funny thing was I have to go back two BIOS releases  for the problem to go away.........so maybe you just need to try another BIOS or wait for the next ubuntu release...(Intrepid Ibex) the new kernel should be all set....with geforce 8200 mobos..

---

### Post by celem on 2008-09-11
Intrepid Ibex will not solve the issue. I loaded the latest Alpha release and the results are the same. I believe that it is an ALSA problem and thus will be present in any and all Linux distributions - I have tried five different distributions on this MoBo and the ALC883/ALC888S doesn't work on any of them. ALC883/ALC888 works on machines that don't use an nVidea support chipset and I believe that the ALSA support missing for the ALC883/ALC888 when supported by a nVidea chipset, which is why DMESG shows "*00:07.0 Audio device: nVidia Corporation Unknown device 0774 (rev a1)*".

I have, so far without success, been trying to find the UDEV patterns that support this chipset. I had luck in the past modifying UDEV patterns to support a Palm Pilot PDA but they seem to have really changed UDEV and I no longer recognize it from the past. I'll try again in the near future.

---

