---
title: "Sound over separate channels (front,rear,center/sub), but not combined"
date: 2010-02-02
forum: Multimedia Software
---

### Post by SaryonOnline on 2010-02-02
Hello everyone,

I am using kubuntu 9.10 with a creative x-fi extremegamer sound card. Out of the box 5.1 surround sound worked on all channels, but i had to start alsamixer to unmute a few. 

```
speaker-test -Dplug:surround51 -c6 -l1 -twav
```

This named all 5 speakers correctly and also said 'rear center' on my front center speaker. Output:

speaker-test 1.0.20

Playback device is plug:surround51
Stream parameters are 48000Hz, S16_LE, 6 channels
WAV file(s)
Rate set to 48000Hz (requested 48000Hz)
Buffer size range from 86 to 10922
Period size range from 6 to 5461
Using max buffer size 10920
Periods = 4
was set period_size = 2730
was set buffer_size = 10920
 0 - Front Left
 4 - Center
 1 - Front Right
 3 - Rear Right
 2 - Rear Left
 5 - LFE
Time per period = 8.419145

The problem is this: sound is only played over the top channel from the sound configuration screen (except when i use speaker-test) and when i put pulseaudio at the top it skips to the next entry.

I followed these steps: [http://wiki.debian.org/X-Fi](http://wiki.debian.org/X-Fi) but that changed nothing.

Does this mean it is a pulseaudio problem? Should i reinstall it?

Thanks in advance

---

### Post by SaryonOnline on 2010-02-02
By watching a dvd with 5.1 Dolby Digital sound and selecting sound device 5.1 in VLC i found out surround sound does actually work. Does this mean there is an upmixing problem?

---

### Post by SaryonOnline on 2010-02-02
I managed to solve my problem, for future references:
[http://old.nabble.com/PCI-Express-SB-X-Fi-Xtreme-Audio-td24527789.html](http://old.nabble.com/PCI-Express-SB-X-Fi-Xtreme-Audio-td24527789.html) from step 4 onward.

Everything turned out to be fine, it turned out the windows creative driver had an upmix feature turned on i never thought about.

---

