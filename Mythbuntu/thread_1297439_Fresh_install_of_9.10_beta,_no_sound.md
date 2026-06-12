---
title: "Fresh install of 9.10 beta, no sound"
date: 2009-10-21
forum: Mythbuntu
---

### Post by JerkyChew on 2009-10-21
Formatted and reloaded my machine with (32 bit) Mythbuntu 9.10 beta using an ISO downloaded yesterday (10/20). I ran a fresh install and on the first reboot downloaded the full set of updates.

This was a slave BE with FE. After getting it up and running I moved it to my living room and found that my sound didn't work. Up until this point there were no speakers plugged in so I don't know if I ever had sound. I've turned up everything in the xfce mixer applet as well as the alsamixer from a command prompt. I've tried Myth, youtube and Pandora with no luck.

The motherboard is a Biostar P4M890-M7 SE.

I saw that there's a similar thread that I didn't want to hijack, so here are the answers to jwbrown77's questions:

> **jwbrown77 said:**
> What version of Mythbuntu are you using?

Is your system using ALSA or OSS for sound?

What's the output of this:

lsmod | grep snd

Are you using regular analog audio cables or optical?

I believe ALSA because when I launch the mixer it says "HDA VIA VT82xx (Alsa mixer)"

```
matt@magic:~$ lsmod | grep snd
snd_hda_codec_realtek   203328  1
snd_hda_intel          26920  3
snd_hda_codec          75708  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               7200  1 snd_hda_codec
snd_pcm_oss            37920  0
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           2656  0
snd_seq_oss            28576  0
snd_seq_midi            6432  0
snd_rawmidi            22208  1 snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_m                            idi_event
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmi                            di,snd_seq
snd                    59204  18 snd_hda_codec_realtek,snd_hda_intel,snd_hda_cod                            ec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,s                            nd_timer,snd_seq_device
soundcore               7264  1 snd
snd_page_alloc          9156  2 snd_hda_intel,snd_pcm

```

I'm using plain old analog audio cables.

---

### Post by jimmux on 2009-10-21
I just had the same thing happen. I was already on 9.10 with working sound, but after an update it was gone. 

The same problem existed when I was on 9.04 and was fixed by updating alsa to version 1.0.20. 

However, I'm on that version now and having the same problem I used to have. You might like to try following the [ALSA upgrade process]("http://ubuntuforums.org/showthread.php?p=6589810") anyway.

---

### Post by jwbrown77 on 2009-10-22
I'm not a Linux sound expert, but I know on my default 9.10 install with full updates, my card was detected as using OSS.  I was attempting to adjust the volume with alsamixer and it wasn't having any effect.

I went into the frontend setup and changed the sound output from alsa to OSS and it started working for me.

Can you try launching a video in mplayer or something and see if you get sound in that (something that's independent of MythTV)?

Because I use optical audio, I had to tell mplayer to use -ao oss:/dev/adsp and it works great.

I think there's an audio FAQ somehwere on these forums (not in the MythBuntu section IIRC, on some other Ubuntu section).  You might try looking that up.

---

### Post by JerkyChew on 2009-10-31
I got it working, user error.

I followed the tips in the excellent ALSA troubleshooting wiki at [http://alsa.opensrc.org/index.php/TroubleShooting](http://alsa.opensrc.org/index.php/TroubleShooting) with no luck. I went back and re-opened my alsa mixer and selected everything in the switches section. I then found that my "Front" device was muted. Un-muted it, and I now have sound!

---

