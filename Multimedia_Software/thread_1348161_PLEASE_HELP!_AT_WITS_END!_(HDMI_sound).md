---
title: "PLEASE HELP! AT WITS END! (HDMI sound)"
date: 2009-12-06
forum: Multimedia Software
---

### Post by theidealist on 2009-12-06
Okay,

I have spent hours and hours on this and I am about ready to throw this stupid computer across the room.

I have a (relatively) new Acer Revo that I am trying to set up as my HTPC (Boxee).  I am not new to linux, however I am rather new to linux with multimedia.

My problem is this: others using my exact same machine report that HDMI sound "just works" out-of-the-box with Karmic (9.10), however nothing I've done seems to help, and it most certainly is not working.  Even more frustrating, nothing I do seems to even indicate that there is anything wrong, it's just that no sound ever comes out.  I am confident all hardware involved is working, as it was working less than two months ago in Ubuntu 9.04.

[LIST]
[*]alsamixer has everything unmuted and set at reasonable volume
[*]I have been through at least three sticky guides on sounds problems, hdmi sound problems, pulse audio problems, alsa sound problems, etc.
[*]I cannot determine if the problem is pulseaudio or alsa, or maybe something with oss?  I already know way more than I ever thought I would have to learn, but REALLY want to get to the bottom of this!
[*]aplay -l says:
```
root@varie:~# aplay -l
**** List of PLAYBACK Hardware Devices ****
Home directory /home/mcmichaelps1 not ours.
card 0: NVidia [HDA NVidia], device 0: ALC662 rev1 Analog [ALC662 rev1 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```
[*]ls -la /proc/asound/ says:
```
root@varie:~# ls -la /proc/asound/
total 0
dr-xr-xr-x   5 root root 0 2009-12-06 20:33 .
dr-xr-xr-x 172 root root 0 2009-12-06 19:57 ..
dr-xr-xr-x   5 root root 0 2009-12-06 20:33 card0
-r--r--r--   1 root root 0 2009-12-06 20:33 cards
-r--r--r--   1 root root 0 2009-12-06 20:33 devices
-r--r--r--   1 root root 0 2009-12-06 20:33 hwdep
-r--r--r--   1 root root 0 2009-12-06 20:33 modules
lrwxrwxrwx   1 root root 5 2009-12-06 20:33 NVidia -> card0
dr-xr-xr-x   2 root root 0 2009-12-06 20:33 oss
-r--r--r--   1 root root 0 2009-12-06 20:33 pcm
dr-xr-xr-x   2 root root 0 2009-12-06 20:33 seq
-r--r--r--   1 root root 0 2009-12-06 20:33 timers
-r--r--r--   1 root root 0 2009-12-06 20:33 version

```
[*]lsmod | grep snd
```
root@varie:~# lsmod | grep -i snd
snd_hda_codec_nvhdmi     4828  1
snd_hda_codec_realtek   203328  1
snd_hda_intel          26920  1
snd_hda_codec          75708  3 snd_hda_codec_nvhdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               7200  1 snd_hda_codec
snd_pcm_oss            37920  0
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           2656  0
snd_seq_oss            28576  0
snd_seq_midi            6432  0
snd_rawmidi            22208  1 snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    59204  14 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               7264  1 snd
snd_page_alloc          9156  2 snd_hda_intel,snd_pcm

```
(this just blows me away there is this much nonsense going on)
[/LIST]

No matter what I do, things always play and work correctly as if there is sound coming out of the speaker, but there is no sound coming out.  I have double and triple checked volumes.

Can anyone offer any help?  Please?

---

### Post by theidealist on 2009-12-08
Any ideas from anyone?

---

### Post by eryulant on 2009-12-09
The line:
Home directory /home/mcmichaelps1 not ours.
 means that something has changed permissions on your home folder, change back to proper user ownership

---

### Post by theidealist on 2009-12-09
> **eryulant said:**
> The line:
Home directory /home/mcmichaelps1 not ours.
 means that something has changed permissions on your home folder, change back to proper user ownership

Thanks eryulant!

I did some checking and I'm not sure where this line came from.  I didn't notice it when posting, but am pretty sure my home directory permissions are correct:

```

mcmichaelps1@varie:~$ ls -la ../
total 28
drwxr-xr-x  4 root         root          4096 2009-10-19 17:04 .
drwxr-xr-x 21 root         root          4096 2009-12-05 22:16 ..
drwx------  2 root         root         16384 2009-07-17 20:32 lost+found
drwxr-xr-x 45 mcmichaelps1 mcmichaelps1  4096 2009-12-08 22:01 mcmichaelps1

```

And when I run aplay I do not get this message, either as root or as my user mcmichaelps1:

```

mcmichaelps1@varie:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC662 rev1 Analog [ALC662 rev1 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
mcmichaelps1@varie:~$ sudo aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC662 rev1 Analog [ALC662 rev1 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
mcmichaelps1@varie:~$

```

Any other ideas?  Am I missing something?

---

### Post by theidealist on 2009-12-20
Just to report, I should let everyone know that I managed to get this solved, but I am not sure how exactly.

I was giving up on Ubuntu and tried a bootable iso of XBMC Live, which didn't work.  While I was doing that I had to completely power off the machine, and I also tightened the HDMI cable a little bit.  After I booted back into Ubuntu after failing with XBMC Live, the sound was at full volume.

Frustrating!  I hope the fix sticks around.  For now I'm a little afraid to do any updates or to power-off again.  Hopefully it was just the cable was loose.

---

