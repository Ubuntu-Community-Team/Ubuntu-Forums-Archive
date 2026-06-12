---
title: "Flaky sound/Jaunty"
date: 2009-08-21
forum: Multimedia Software
---

### Post by Malibyte on 2009-08-21
Running 9.04 x86-64
This is my home multimedia server/MythTV box

Having some weird problems with sound (I'm using the SPDIF out to my receiver) since updating a while back from Intrepid.

Sometimes it just loses sound altogether.  Sometimes I can bring it back by opening up Alsamixer in a terminal and hitting the "M" key a few times while on "Master".  Sometimes it just doesn't come back, and I have to reboot.  This is, to say the least, annoying.  Sometimes it works for a week before it decides to cut out.  

Sometimes it'll be silent after a reboot, and I'll bring up Alsamixer and find that the master volume is *zero* and has also been disabled ("M" brings it back).

Per lspci, this is my sound hardware:
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)

using these modules:
[mythtv@vader: ~]$ lsmod | grep snd
snd_hda_intel         557492  5
snd_pcm_oss            52352  0
snd_mixer_oss          24960  1 snd_pcm_oss
snd_pcm                99464  3 snd_hda_intel,snd_pcm_oss
snd_timer              34064  1 snd_pcm
snd                    78920  14 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              16800  1 snd
snd_page_alloc         18704  2 snd_hda_intel,snd_pcm

Anyone else see this behavior and have a fix?  Drives me nuts. I think Pulse Audio is "not-yet-ready-for prime-time".  My office Jaunty box was doing the same thing for a while, too.

Thanks - Bob

---

