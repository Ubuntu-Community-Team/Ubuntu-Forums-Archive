---
title: "Yet another no sound thread"
date: 2006-08-22
forum: Multimedia &amp; Video
---

### Post by the_stranger on 2006-08-22
Seems like I can't get sound to work under Linux at all. I installed Fedora about a year back, but could get the sound to work. Now I'm trying out Ubuntu and I still have the same problem. Right now I'm only using the live cd trial. I see no point in wasting time installing it permanently if the sound doesn't work. Which is a shame since I like it more then xp. I'm hoping that maybe someone here will find a solution so I can keep using Ubuntu.

I've tried the comprehensive sound trouble guide that's posted here to no avail. From what I can tell my sound card is detected and all the drivers installed, so I really don't know what the problem can be. i unmuted and maxed the volume on everything...nothing.

If you have any ideas about what could be wrong and how to fix please respond. Just remember my experience with Ubunutu spans a grand total of a couple of hours so I'm still trying to get my bearings. So please be as detailed as possible in your explanations.

---

### Post by the_stranger on 2006-08-22
Anybody?

---

### Post by tomplast on 2006-08-22
> **the_stranger said:**
> Anybody?

Sorry I can't help you my friend but have you tried asking someone on #ubuntu at irc.freenode.net?

---

### Post by lodp on 2006-08-23
you said in that other thread:

```
I'm a little hesitent doing a permanent install before clearing up the sound problem. If it turns out the sound problem can't be fixed, then I would have to spend a huge amount of time reinstalling XP and all the programs I have right now.

```

it's not like installing ubuntu will destroy your windows partition -- in fact, most people (afaik) leave a windows double boot for a very long time. so you might as well just go for it..

once you've got ubtuntu installed, i would suggest you install the latest release candidate of ALSA (as described in the comprehensive sound problems guide).

btw, have you tried playing a .wav file with ```
aplay <file>
``` in terminal? just for troubleshooting..

and yeah, and it's probably a good thing to repost the results of lspci, lsmod|grep snd, from that other thread you posted to.

---

### Post by the_stranger on 2006-08-23
I installed Ubuntu permanently now.

I tried compiling new ALSA drivers, but it didn't have any effect. aplay doesn't work either. i don't get an error, but there's no sound either. Everything is unmuted and maxed in alsamixer.

Here's my data:

lspci:
```
0000:00:00.0 Host bridge: nVidia Corporation nForce2 AGP (different version?) (rev a2)
0000:00:00.1 RAM memory: nVidia Corporation nForce2 Memory Controller 1 (rev a2)0000:00:00.2 RAM memory: nVidia Corporation nForce2 Memory Controller 4 (rev a2)0000:00:00.3 RAM memory: nVidia Corporation nForce2 Memory Controller 3 (rev a2)0000:00:00.4 RAM memory: nVidia Corporation nForce2 Memory Controller 2 (rev a2)0000:00:00.5 RAM memory: nVidia Corporation nForce2 Memory Controller 5 (rev a2)0000:00:01.0 ISA bridge: nVidia Corporation nForce2 ISA Bridge (rev a3)
0000:00:01.1 SMBus: nVidia Corporation nForce2 SMBus (MCP) (rev a2)
0000:00:02.0 USB Controller: nVidia Corporation nForce2 USB Controller (rev a3)
0000:00:02.1 USB Controller: nVidia Corporation nForce2 USB Controller (rev a3)
0000:00:02.2 USB Controller: nVidia Corporation nForce2 USB Controller (rev a3)
0000:00:04.0 Ethernet controller: nVidia Corporation nForce2 Ethernet Controller (rev a1)
0000:00:05.0 Multimedia audio controller: nVidia Corporation nForce Audio Processing Unit (rev a2)
0000:00:06.0 Multimedia audio controller: nVidia Corporation nForce2 AC97 Audio Controler (MCP) (rev a1)
0000:00:08.0 PCI bridge: nVidia Corporation nForce2 External PCI Bridge (rev a3)0000:00:09.0 IDE interface: nVidia Corporation nForce2 IDE (rev a2)
0000:00:0c.0 PCI bridge: nVidia Corporation nForce2 PCI Bridge (rev a3)
0000:00:0d.0 FireWire (IEEE 1394): nVidia Corporation nForce2 FireWire (IEEE 1394) Controller (rev a3)
0000:00:1e.0 PCI bridge: nVidia Corporation nForce2 AGP (rev a2)
0000:01:0b.0 RAID bus controller: Silicon Image, Inc. SiI 3112 [SATALink/SATARaid] Serial ATA Controller (rev 01)
0000:02:01.0 Ethernet controller: 3Com Corporation 3C920B-EMB Integrated Fast Ethernet Controller [Tornado] (rev 40)
0000:03:00.0 VGA compatible controller: ATI Technologies Inc RV350 AR [Radeon 9600]
0000:03:00.1 Display controller: ATI Technologies Inc RV350 AR [Radeon 9600] (Secondary)

```

lsmod|grep snd
```
snd_intel8x0           34076  1
snd_ac97_codec         92832  1 snd_intel8x0
snd_ac97_bus            2304  1 snd_ac97_codec
snd_pcm_oss            61728  0
snd_mixer_oss          19456  2 snd_pcm_oss
snd_pcm                99080  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              26500  1 snd_pcm
snd                    62956  6 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              10208  2 snd
snd_page_alloc         11272  2 snd_intel8x0,snd_pcm

```

aplay -l
```
card 0: nForce2 [NVidia nForce2], device 0: Intel ICH [NVidia nForce2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: nForce2 [NVidia nForce2], device 2: Intel ICH - IEC958 [NVidia nForce2 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

cat /proc/asound/version
```
Advanced Linux Sound Architecture Driver Version 1.0.10.
Compiled on Aug 23 2006 for kernel 2.6.15-26-386.

```

cat /proc/asound/card0/codec#0
```
cat: /proc/asound/card0/codec#0: No such file or directory
```

I assume this is where the problem lies.

---

