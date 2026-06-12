---
title: "My rear right speaker isn't working."
date: 2009-03-16
forum: Multimedia Software
---

### Post by ShadowTek on 2009-03-16
My sound card will only output sound to my rear speakers if I use the multichannel playback ALSA driver, but even then it will only output both rear channels to my left rear speaker, while outputing nothing to my rear right speaker.

I know that the rear right speaker works because I can unplug the rear channels input line from the amp and the rear speakers are automatically fed a copy of the front channel audio, so I can then see that the rear right speaker *is* working just fine.

Anybody got any idea what the problem is?

Sound card info from lshw:
>            *-multimedia
                description: Multimedia audio controller
                product: SB Live! EMU10k1
                vendor: Creative Labs
                physical id: 1
                bus info: pci@0000:02:01.0
                version: 0a
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=EMU10K1_Audigy latency=64 maxlatency=20 mingnt=2 module=snd_emu10k1


---

### Post by ShadowTek on 2009-03-18
Any ideas on where to start?

---

### Post by markbuntu on 2009-03-18
You can try these. reampping may be your best bet.

[http://www.automaticable.com/2008-05-28/how-to-enable-surround-sound-on-ubuntu-hardy/](http://www.automaticable.com/2008-05-28/how-to-enable-surround-sound-on-ubuntu-hardy/)

[http://ubuntuforums.org/showthread.php?t=795525](http://ubuntuforums.org/showthread.php?t=795525)

[http://ubuntuforums.org/showthread.php?t=899139](http://ubuntuforums.org/showthread.php?t=899139)

---

### Post by ShadowTek on 2009-03-19
That first link helped me to get surround sound partially, temporarily working with pulse audio, as I was previously unaware that you had to manually configure the daemon.conf file in order to get PA to work with surround sound. But, the result is buggy, and I am still having the same original problem.

I rebooted the computer and tried doing a speaker-test, but it crashed after a few iterations, and all sound to the rear speakers was lost.

```
user@user-desktop:~$ speaker-test -c 4

speaker-test 1.0.17

Playback device is default
Stream parameters are 48000Hz, S16_LE, 4 channels
Using 16 octaves of pink noise
Rate set to 48000Hz (requested 48000Hz)
Buffer size range from 48 to 524288
Period size range from 16 to 174763
Using max buffer size 524288
Periods = 4
was set period_size = 131072
was set buffer_size = 524288
 0 - Front Left
 1 - Front Right
 3 - Rear Right
 2 - Rear Left
Time per period = 11.074343
 0 - Front Left
 1 - Front Right
 3 - Rear Right
 2 - Rear Left
Time per period = 9.455247
 0 - Front Left
speaker-test: pcm_pulse.c:360: pulse_write: Assertion `pcm->stream' failed.
Aborted
```I then tried to edit the default.pa file to manually configure the channel mapping. I have tried several different settings, each time swapping the assignment of the last two entries, but I haven't made any progress.

After each time I changed the channel_map settings, I would reboot the computer and test the output with:
 speaker-test -c4

The result from any channel_map settings I try is that the rear channel outputs would both be directed to the RL speaker, while the RR speaker gets no output. Or, no output will be delivered to either RL or RR speaker. Either way, the speaker-test will crach after a few iterations of the test, and then all sound from the rear speakers will cease.

I have now restored the default.pa and daemon.conf to their default state. I went back to using ALSA multichannel, and I can do a speaker-test without crashing, but the original remains, of course.

Another odd note, now that I'm using ALSA again,
 speaker-test -c 4
doesnt output any sound to my rear speakers, but 
 speaker-test -Dplug:surround40 -c4 -l5 -twav
outputs sound to the rear left speaker just fine.

Anybody got any ideas as to what I can try now?

---

### Post by markbuntu on 2009-03-19
That is sounding more and more like a bug in the alsa driver.

---

### Post by awilkins on 2011-10-14
I'm getting the same thing. It's not the first time I've had problems with the ALSA driver on this hardware.

I'll have a squizz at the patch-panel code.

---

