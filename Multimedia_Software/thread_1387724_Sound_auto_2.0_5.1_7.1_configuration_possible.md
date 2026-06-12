---
title: "Sound: auto 2.0 5.1 7.1 configuration possible?"
date: 2010-01-22
forum: Multimedia Software
---

### Post by leodp on 2010-01-22
Dear all,

I have an amplifyer with a 5.1 speaker system, with all the analog and digital in/out that may be needed.
I would like to connect it with a Linux multimedia PC/laptop or whatever.

Basically I will use it to:
- listen to CDs (stereo)
- watch movies  (5.1 or 7.1 audio channels)


Is there a way to setup the audio environment so that when I play something with 5.1 audio channels they are correctly routed to the speakers without mixing and when I play stereo audio all the 5.1 speakers are active?
I have looked in various threads where people explain how to config alsa, but I have not found yet a solution that works for the two situations at the same time. 
Or am I wrong?


Thanks,
Leodp

---

### Post by VertexPusher on 2010-01-22
If you use ALSA without PulseAudio, this .asoundrc should do the trick:
```
pcm.!default {
    type plug
    slave.pcm {
        type asym
        playback.pcm {
            type dmix
            ipc_key 10001
            slave {
                pcm "hw:0"
                channels 8
            }
        }
        capture.pcm "hw:0"
    }
    route_policy duplicate
}
```
"route_policy duplicate" makes ALSA copy channels if the number of client channels is lower than the number of slave channels which is set to 8. For a 5.1 soundcard change "channels 8" to "channels 6".

---

### Post by leodp on 2010-01-22
> **VertexPusher said:**
> If you use ALSA without PulseAudio, ...


So I have another reason to purge Pulseaudio.
Thanx VertexPusher, I'll give a try over the WE.

Leodp

---

### Post by leodp on 2010-01-22
That works perfect.
Moreover, it also works on pulseaudio. I have edited the file /etc/pulse/daemon.conf
by changing line 77 from
; default-sample-channels = 2

to:
default-sample-channels = 6


However, for some strange reason the audio card in my old laptop is recognised as a 4.0 channels, so front_center and LFE (subwoofer) are mixed with the other channels (no matter if I change the surround jack mode setting between shared and independent). But that's another problem.

Thanks again,
Leodp

---

