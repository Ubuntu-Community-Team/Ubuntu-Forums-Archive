---
title: "trouble getting 5.1 sound out"
date: 2007-09-30
forum: Multimedia &amp; Video
---

### Post by slowpoke on 2007-09-30
I finally purchased an external dialup modem to I could try and dump windhose again.  Installed fine, been using fiesty 7.04 for about a week and love it.  But I can't figure out how to get 5.1 sound.  I have a mad dog entertainer 7.1 card:   

Multimedia audio controller: VIA Technologies Inc. VT1720/24 [Envy24PT/HT] PCI Multi-Channel Audio Controller (rev 01)
        Subsystem: VIA Technologies Inc. Albatron PX865PE 7.1
        Flags: bus master, medium devsel, latency 32, IRQ 20
        I/O ports at d000 [size=32]
        I/O ports at d400 [size=128]
        Capabilities: <access denied>

and it sounds fine on the two front speakers and the sub, but the other three aren't making any noise.  I've looked in the volume control preferences and found no channel option even after check the surround option.  Nothing is muted and searched the forum and the internet with no luck yet.

---

### Post by slowpoke on 2007-09-30
speaker-test -Dplug:surround51 -c6-l1 -twav

speaker-test 1.0.13

Playback device is plug:surround51
Stream parameters are 48000Hz, S16_LE, 6 channels
WAV file(s)
Rate set to 48000Hz (requested 48000Hz)
Buffer size range from 8 to 10920
Period size range from 4 to 5460
Using max buffer size 10920
Periods = 4
was set period_size = 0
was set buffer_size = 10920
Unable to set sw params for playback: Invalid argument
Setting of swparams failed: Invalid argument

anybody understand the results, I could use a little help translating.

---

