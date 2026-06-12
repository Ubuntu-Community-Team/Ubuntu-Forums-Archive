---
title: "Xubuntu64: M-Audio Delta 66, No sound and no input"
date: 2008-09-19
forum: Multimedia Software
---

### Post by jabeavers on 2008-09-19
Hello,

System:
I am running Xubuntu64 Hardy (Dual boot WinXP x64) on an Intel D975XBX MB with 4G Ram and a 4GHz processor.  I recently installed an M-Audio Delta 66 soundcard, but it will not work.

Symptoms:
When playing audio on the system, I can see the levels in envy24 moving, showing that it is seeing the audio, but there is no sound output.  Furthermore, when I plug in a sound source, the levels do not show that it is seeing the external source (mixing console, microphone, etc).  The levels do not move on the inputs like they do on the outputs.

The card does the same thing in Windows, no sound and no input movements.

What I've tried:
I tested on a different 32 bit Windows, and it works perfectly.  I also installed 32 bit XP on this computer, and it worked, so it's not the motherboard.
I have followed the Sound Problems Guide in this forum, no luck.  I have uninstalled alsa, installed OSS4, uninstalled OSS and reinstalled alsa, still same.  I have built the alsa sources from scratch (1.0.17), same.  The levels are set and the mutes are off.  It appears to be a 64 bit problem.  Right??  Is there a way to install a 32 bit driver for this card, or do you all have other suggestions.

Thanks,
John

---

### Post by jabeavers on 2008-09-22
Well, I got a response from M-audio reguarding no sound in XP64. They think it must be the driver, as well, and say there should be an update after the Vista x64 update, but they have no idea when it will be available.  I am most concerned about the card working in Linux rather than Windows, so if anyone could help me get it working here, I would be most appreciative.

John

---

### Post by Yellow Pasque on 2008-09-22
How did you install OSS4? Did you use this document? [https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)

---

### Post by jabeavers on 2008-09-22
Hello,

Now that I look at the document you provided, I guess I did not.  I simply installed in from Synaptic.  I'll use the howto and let you know.

Thanks,
John

---

### Post by jabeavers on 2008-09-22
Okay, I followed the document you provided, and everything went okay durring the build.  However, when I enter ossmix, it says Mixer device 0 dosen't exist.  The card is listed in lspci, but not in /proc/interrupts.  I have rebooted, and it is the same thing.  I feel like we're close, but I cannot test it with whatever problem this is.  Also, the program ossxmix is nowhere to be found on my HDD.

John

---

### Post by jabeavers on 2008-09-23
I got the card to show up, but since ossxmix did not compile/install, I cannot change the values of the output to test the card.  I don't really know how to use ossmix, but I'm trying to figure it out.  I'll keep you apprised.

John

---

### Post by jabeavers on 2008-09-23
Okay,

I'm pretty sure that I got ossmix working (I mean, got me to work it properly).  I think the levels were set up on it, to begin with, but I'll include the output from it just in case.

Selected mixer 0/M Audio Delta 66
Known controls are:

peak.out1/2 [<leftVU>:<rightVU>] (currently 114:116) (Read-only)
peak.out3/4 [<leftVU>:<rightVU>] (currently 0:0) (Read-only)
peak.spdout [<leftVU>:<rightVU>] (currently 0:0) (Read-only)
peak.in1/2 [<leftVU>:<rightVU>] (currently 0:0) (Read-only)
peak.in3/4 [<leftVU>:<rightVU>] (currently 0:0) (Read-only)
peak.spdin [<leftVU>:<rightVU>] (currently 0:0) (Read-only)
peak.main [<leftVU>:<rightVU>] (currently 114:116) (Read-only)

mon.out1/2 [<leftvol>:<rightvol>] (currently 51.0:51.0 dB)
mon.out3/4 [<leftvol>:<rightvol>] (currently 135.0:135.0 dB)
mon.spdout [<leftvol>:<rightvol>] (currently 135.0:135.0 dB)
mon.in1/2 [<leftvol>:<rightvol>] (currently 135.0:135.0 dB)
mon.in3/4 [<leftvol>:<rightvol>] (currently 135.0:135.0 dB)
mon.spdin [<leftvol>:<rightvol>] (currently 135.0:135.0 dB)

route.out1/2 <DMA|MONITOR|IN1/2|IN3/4|SPDIF> (currently MONITOR)
route.out3/4 <DMA|IN1/2|IN3/4|SPDIF> (currently DMA)
route.spdif <DMA|MONITOR|IN1/2|IN3/4|SPDIF> (currently MONITOR)

gain.out1/2 <+4DB|CONSUMER|-10DB> (currently +4DB)
gain.out3/4 <+4DB|CONSUMER|-10DB> (currently +4DB)
gain.in1/2 <+4DB|CONSUMER|-10DB> (currently +4DB)
gain.in3/4 <+4DB|CONSUMER|-10DB> (currently +4DB)
envy24.rate <8000|9600|11025|12000|16000|22050|24000|32000|44100|48000|64000|88200> (currently 48000)
envy24.sync <INTERNAL|SPDIF> (currently INTERNAL)
envy24.ratelock ON|OFF (currently ON)
envy24.actrate <decimal value> (currently 48000) (Read-only)
  Sample rate currently used by the device

By the way, I'm playing some music through vlc, and if I do ossmix -v2 twice in a row, I get different readings for peak.out1/2, so I'm pretty sure it is working correctly, and I've configured it correctly.  Oh yeah, it's doing the same thing, no sound (but apparently level indicators moving).  Well, I'm going to sleep now, I'll read more when I can.

John

---

### Post by jabeavers on 2010-08-18
I got it working a while back but forgot about this post. I have it working through alsa and I had to add a line in alsa-base.con to say "options ice1712 model=delta1010lt" It turns out there were some analog volume controls that did not show up in envy24control with model=delta66. When I turned up all the sliders, I got sound out of my card. I am also able to record through jack.

I have since upgraded to 10.04 and have my sound working nearly perfectly. Thanks for the help and I will change this to solved if I can figure out how.

---

### Post by tgalati4 on 2010-08-18
"It's Alive!"  Thanks for resurrecting this old thread.  I have a Delta66 that works well.  I'm sure this little magic option will help others.

---

### Post by jabeavers on 2010-08-18
Yep, just cleaning up my subscriptions and said, "Hmm, I better close this one...." Later.

John

---

