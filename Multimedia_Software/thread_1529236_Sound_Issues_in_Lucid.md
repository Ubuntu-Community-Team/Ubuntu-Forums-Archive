---
title: "Sound Issues in Lucid"
date: 2010-07-11
forum: Multimedia Software
---

### Post by mrphud on 2010-07-11
Hello,

I have had sound issues with Ubuntu since I switched from Windows. I must say I am enjoying using Linux but, am consistently frustrated with my sound issues. 

I have tried for help in the past and have learned a few things about the behavior of the system. Unfortunately, I still can't "fix" my sound to use it to its full potential.

The steps I took to get to my current setup are shown in this past thread.

[http://ubuntuforums.org/showthread.php?t=1516293]("http://ubuntuforums.org/showthread.php?t=1516293")

I will sum up behavior and specs:

1. I have a 4.1 speaker sound system that includes, headphone port, mic input, and some usb game ports.
2. I have pulse audio all updated but I have it set to audio duplex otherwise the connection terminates. Meaning, I can't set it to 4.1 output. If I do set it to 4.1 the sound is uneven (amplitude) out of sync and poppy.
3. When I have it set to duplex, I hear decent sound except when I play audio or video files on vlc or rythmbox. Internet vidoe sounds and startup sounds are fine.
4. The sound card for the system is recognized as CS46xx. I have a Hercules Game Theater XP sound card. This is consistent with the alsa.org listing.

I would love to get this fixed, but mostly I would like to understand what is going on. I plan on using linux from now on and wish to know how to fix these issues in the future unassisted.

Thanks

---

### Post by Yellow Pasque on 2010-07-12
You asked me to look at your situation, so here goes..
It sounds like you have ALSA apps (Flash, system sounds) working well. You might try using ALSA output in VLC's options to see if it improves things. For rhythmbox to use ALSA:
```
gconftool-2 --type string --set /system/gstreamer/0.10/default/audiosink alsasink
gconftool-2 --type string --set /system/gstreamer/0.10/default/chataudiosink alsasink
gconftool-2 --type string --set /system/gstreamer/0.10/default/musicaudiosink alsasink
```
This might be one of those cases where your system works better without pulseaudio or with OSS4: [https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)
Sorry that I can't provide more guidance with the pulse issues, but I only use pulseaudio on one of my partitions (and it works for my stereo system without issue).

---

### Post by mrphud on 2010-07-12
Wow you are awesome. That fixed the sound glitches from my speakers.

I still only have audio on 2 speakers and not on 4 though. Any ideas on that?

Of course I can switch the output to 4.1, but I still don't get output on 4 speakers.

It also degrades the sound quality when I do have it set to 4.1 speakers.

---

### Post by Yellow Pasque on 2010-07-13
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/428619](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/428619)

---

### Post by mrphud on 2010-07-13
It appears that this is a common bug for the CS46xx driver. I guess this means I will have to make due until someone is motivated to fix the problem.

Thanks again.

---

### Post by mrphud on 2010-07-14
Thanks for the help!!!

---

