---
title: "No sound out of center channel"
date: 2008-02-25
forum: Multimedia &amp; Video
---

### Post by malfist on 2008-02-25
My card is supported by ALSA but I seem to be having problems with it. I cannot get sound out of the center channel (even though I can get it out of the sub). Can someone help me?

audio card:
```

01:0b.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)
        Subsystem: C-Media Electronics Inc CMI8738/C3DX PCI Audio Device
        Flags: bus master, medium devsel, latency 32, IRQ 5

```

I attempted to fix it by addeding this to my .asoundrc
```

pcm.!default {
    type plug
    slave.pcm "surround51"
    slave.channels 6
    route_policy duplicate
}
```

And testing it fails like this:```

 speaker-test -Dplug:surround51 -c6 -l1 -twav

speaker-test 1.0.14

Playback device is plug:surround51
Stream parameters are 48000Hz, S16_LE, 6 channels
WAV file(s)
ALSA lib pcm_params.c:2135:(snd1_pcm_hw_refine_slave) Slave PCM not usable
Broken configuration for playback: no configurations available: Invalid argument
Setting of hwparams failed: Invalid argument

```

As a side note, because I could not get it working I compiled from the newest stable release from ALSA and still no go.

I can only get sound from all channels if I do 'matrix' on my logitech speakers (X-540).

---

### Post by msarro on 2008-02-25
I hate to ask the mundane, but in the mixer utility, did you turn up the sound? Yesterday when I was configuring a brand new install I noticed that it defaulted to 0/off, whereas the rest of the channels were at about 80% volume.

---

### Post by malfist on 2008-02-25
Yes, already checked alsamixer.

Here's my alsa mixer

---

### Post by malfist on 2008-02-25
Update, removed the thing from the asoundrc and I can test all speakers successfully, now everything works (even though that was not in the asoundrc before). Odd.


edit: not solved.

---

### Post by malfist on 2008-02-25
Update: Not solved, issue occured again after about 1 minute.
```

speaker-test -Dplug:surround51 -c6 -l1 -twav

speaker-test 1.0.14

Playback device is plug:surround51
Stream parameters are 48000Hz, S16_LE, 6 channels
WAV file(s)
ALSA lib pcm_params.c:2135:(snd1_pcm_hw_refine_slave) Slave PCM not usable
Broken configuration for playback: no configurations available: Invalid argument
Setting of hwparams failed: Invalid argument

```

No sound out of center speaker.

---

### Post by malfist on 2008-02-25
update:
```

jerome@jerome-desktop:~$ speaker-test -c 6 -D surround51

```
Can play out of all channels when all things using alsa have been killed (thanks to fuser for finding them). But apps like rhythmbox cannot seem to use it.

asoundrc is empty.

---

### Post by malfist on 2008-02-26
I can make some detect all 6 channels but not all. Can anyone help me?

---

### Post by malfist on 2008-02-26
fixed, set a pcm.!default W00t.

---

### Post by malfist on 2008-02-26
channels are out of order :(

---

### Post by malfist on 2008-02-26
I can reagrange the channels for MPlayer in the asoundrc but speaker-test would have it out of order and audacity still ignores it and rhythmbox does too.

---

