---
title: "sound issues"
date: 2008-10-04
forum: Multimedia Software
---

### Post by melzanis on 2008-10-04
Okay it seems i'm having a bit of an issue playing more then one audio format. I don't know how to explain it other then if I have Rythmbox playing songs then say I want to switch to a youtube video it doesn't want to play the youtube video with sound. Therefore, the sound is missing. I was just wondering if I need a special codecs or something alone those lines to play more then audio format, any help with this would be great.

Cheers

---

### Post by Braytok on 2008-10-04
This is perhaps the biggest bug ubuntu has IMHO. for some ungodly reason, Feisty was the last release that actually had sound working right.

One would think that getting sound working across the board would be top priority... 

I know this is not helpful but I've been fighting this issue myself since the Feisty and I'm almost ready to consider another OS all together. A desktop computer without proper multimedia use useless to the average user.](*,)

---

### Post by melzanis on 2008-10-04
Ya one would think having sound would be a top priority. I use the 'sudo lshw' to get the out of my sound device. 

        *-multimedia
             description: Audio device
             product: 82801G (ICH7 Family) High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 01
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=HDA Intel latency=0 module=snd_hda_intel


For hardware I have:

Intel(R) Core(TM)2 Quad CPU 2.40GHz
ASUS P5KPL-CM motherboard
and an ASUS EN9800GT video card 

I'm using the on-board sound as well.
and the only way to fix this problem, or get the youtube video is to logout
but then if I play the youtube video, I can't listen to music. This is really
strange
:(

I hope someone out their can help

Cheers,
and thanks for any help

---

### Post by markbuntu on 2008-10-04
You need to get:

libflashsupport

to fix that problem with flash9. If you have flash 10, you need to remove it. Also, in System/Preferences/Sound, change everything to alsa from autodetect. If you want a more comprehensive guide go here:

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

### Post by Braytok on 2008-10-05
> **markbuntu said:**
> You need to get:

libflashsupport

to fix that problem with flash9. If you have flash 10, you need to remove it. Also, in System/Preferences/Sound, change everything to alsa from autodetect. If you want a more comprehensive guide go here:

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

even doing that I still had intermittent sound and also flash files render on top of other page items blocking them with a black box. But if you can live with janky flash displays then this is about th only option I have had any success with.

---

### Post by markbuntu on 2008-10-05
You can look in my guide here for more extensive help:


[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

