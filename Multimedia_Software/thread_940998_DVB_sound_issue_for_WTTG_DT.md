---
title: "DVB sound issue for WTTG DT"
date: 2008-10-07
forum: Multimedia Software
---

### Post by dcory on 2008-10-07
I've managed to install my Pinnacle 800e TV tuner on my Kubuntu Hardy system.  It works great for the most part and I'm getting digital TV in the Washington, DC area.

Problem is that WTTG DT (Fox) doesn't give my any sound!  I have no idea how to begin diagnosis on this problem.  After all, my hardware and software have to be generally correct in order for me to get the other channels.  What can be different about this one?

I'll gladly post any relevant information about my setup, but I don't even know what would be relevant at this point.  I can tell you that I'm using Kaffeine to watch.

Thanks in advance- I love these forums! 

DC

---

### Post by xc3RnbFO8P on 2008-10-08
did you try to change audiochannel?

---

### Post by dcory on 2008-10-08
I only see one option for audio channel, and that is "auto."  The only other option I see relating to audo is "audio pid," but I don't think that is relevant.

I feel like I'm missing something?

---

### Post by xc3RnbFO8P on 2008-10-08
Do you have **w32codecs** installed.
In Terminal:
> kaffeine --verbose DVB 

---

### Post by dcory on 2008-10-11
Well, I have w64codecs, which I think is the same thing but for a 64 bit system (which I have).  When I opened kaffeine in verbose mode and flipped to the offending channel, I did got the following:

demux_ts: PID 0x0034: corrupted pes encountered
audio_decoder: error, unknown buffer type: 0400001c
200 frames delivered, 17 frames skipped, 1 frames discarded
demux_ts: PID 0x0034: corrupted pes encountered
audio_decoder: error, unknown buffer type: 04000012
demux_ts: PID 0x0034: corrupted pes encountered
video_out: throwing away image with pts 8072787 because it's too old (diff : 58613).
demux_ts: PID 0x0031: unexpected cc 14 (expected 5)
demux_ts: PID 0x0034: unexpected cc 4 (expected 13)
demux_ts: PID 0x0034: corrupted pes encountered
demux_ts: PID 0x0034: corrupted pes encountered
demux_ts: PID 0x0034: corrupted pes encountered
demux_ts: PID 0x0034: corrupted pes encountered
demux_ts: PID 0x0034: corrupted pes encountered
audio_decoder: error, unknown buffer type: 04000006
demux_ts: PID 0x0034: corrupted pes encountered
demux_ts: PID 0x0034: corrupted pes encountered
demux_ts: PID 0x0034: corrupted pes encountered
demux_ts: PID 0x0034: corrupted pes encountered
demux_ts: PID 0x0034: corrupted pes encountered
demux_ts: PID 0x0034: corrupted pes encountered
audio_decoder: error, unknown buffer type: 07000006
demux_ts: PID 0x0034: corrupted pes encountered
demux_ts: PID 0x0034: corrupted pes encountered
demux_ts: PID 0x0034: corrupted pes encountered
demux_ts: PID 0x0034: corrupted pes encountered
demux_ts: PID 0x0031: unexpected cc 14 (expected 2)
demux_ts: PID 0x0034: unexpected cc 4 (expected 16)
demux_ts: PID 0x0034: corrupted pes encountered
demux_ts: PID 0x0034: corrupted pes encountered
audio_decoder: error, unknown buffer type: 04000006
demux_ts: PID 0x0031: unexpected cc 4 (expected 8)
demux_ts: PID 0x0034: unexpected cc 14 (expected 10)
demux_ts: PID 0x0034: corrupted pes encountered
demux_ts: PID 0x0034: corrupted pes encountered
audio_decoder: error, unknown buffer type: 07000006
demux_ts: PID 0x0034: corrupted pes encountered
demux_ts: PID 0x0034: corrupted pes encountered
demux_ts: PID 0x0034: corrupted pes encountered
demux_ts: PID 0x0034: corrupted pes encountered
demux_ts: PID 0x0034: corrupted pes encountered
demux_ts: PID 0x0034: corrupted pes encountered
demux_ts: PID 0x0034: corrupted pes encountered
demux_ts: PID 0x0034: corrupted pes encountered
demux_ts: PID 0x0034: corrupted pes encountered
demux_ts: PID 0x0034: corrupted pes encountered
demux_ts: PID 0x0034: corrupted pes encountered
video jump
demux_ts: PID 0x0034: corrupted pes encountered
video jump
demux_ts: PID 0x0034: corrupted pes encountered
video jump
demux_ts: PID 0x0034: corrupted pes encountered
demux_ts: PID 0x0034: corrupted pes encountered
demux_ts: PID 0x0034: corrupted pes encountered
demux_ts: PID 0x0034: corrupted pes encountered
demux_ts: PID 0x0034: corrupted pes encountered
demux_ts: PID 0x0034: corrupted pes encountered
demux_ts: PID 0x0034: corrupted pes encountered
demux_ts: PID 0x0034: corrupted pes encountered
audio_decoder: error, unknown buffer type: 07020006
audio_decoder: error, unknown buffer type: 0400000a
demux_ts: PID 0x0034: corrupted pes encountered
demux_ts: PID 0x0034: corrupted pes encountered
demux_ts: PID 0x0034: corrupted pes encountered
demux_ts: PID 0x0034: corrupted pes encountered
audio_decoder: error, unknown buffer type: 04000000
video_out: throwing away image with pts 8248463 because it's too old (diff : 58618).
demux_ts: PID 0x0034: corrupted pes encountered
demux_ts: PID 0x0034: corrupted pes encountered
audio_decoder: error, unknown buffer type: 0400001e
demux_ts: PID 0x0034: corrupted pes encountered
demux_ts: PID 0x0034: corrupted pes encountered
demux_ts: PID 0x0034: corrupted pes encountered
audio_decoder: error, unknown buffer type: 04000002
audio_decoder: error, unknown buffer type: 07000002
demux_ts: PID 0x0034: corrupted pes encountered
audio_decoder: error, unknown buffer type: 0400000b
demux_ts: PID 0x0034: corrupted pes encountered
demux_ts: PID 0x0034: corrupted pes encountered
demux_ts: PID 0x0034: corrupted pes encountered
demux_ts: PID 0x0034: corrupted pes encountered
demux_ts: PID 0x0034: corrupted pes encountered
demux_ts: PID 0x0034: corrupted pes encountered
demux_ts: PID 0x0034: corrupted pes encountered
demux_ts: PID 0x0034: corrupted pes encountered
demux_ts: PID 0x0034: corrupted pes encountered
demux_ts: PID 0x0031: unexpected cc 15 (expected 16)
demux_ts: PID 0x0034: unexpected cc 3 (expected 2)
demux_ts: PID 0x0034: corrupted pes encountered
demux_ts: PID 0x0031: unexpected cc 7 (expected 9)
demux_ts: PID 0x0034: unexpected cc 11 (expected 9)
demux_ts: PID 0x0031: unexpected cc 6 (expected 10)
demux_ts: PID 0x0034: unexpected cc 12 (expected 8)
demux_ts: PID 0x0034: corrupted pes encountered
audio_decoder: error, unknown buffer type: 0702000b
demux_ts: PID 0x0034: corrupted pes encountered
demux_ts: PID 0x0034: corrupted pes encountered
demux_ts: PID 0x0034: corrupted pes encountered
demux_ts: PID 0x0034: corrupted pes encountered
demux_ts: PID 0x0034: corrupted pes encountered
demux_ts: PID 0x0034: corrupted pes encountered
demux_ts: PID 0x0034: corrupted pes encountered
demux_ts: PID 0x0034: corrupted pes encountered
demux_ts: PID 0x0034: corrupted pes encountered
audio_decoder: error, unknown buffer type: 04000015
demux_ts: PID 0x0031: unexpected cc 7 (expected 11)
demux_ts: PID 0x0034: unexpected cc 11 (expected 7)
demux_ts: PID 0x0031: unexpected cc 13 (expected 16)
demux_ts: PID 0x0031: unexpected cc 11 (expected 13)
demux_ts: PID 0x0034: unexpected cc 7 (expected 2)
demux_ts: PID 0x0034: corrupted pes encountered
video jump
demux_ts: PID 0x0031: unexpected cc 8 (expected 10)
demux_ts: PID 0x0034: unexpected cc 10 (expected 8)
demux_ts: PID 0x0034: corrupted pes encountered
audio_decoder: error, unknown buffer type: 04000012
demux_ts: PID 0x0034: corrupted pes encountered
demux_ts: PID 0x0034: corrupted pes encountered
demux_ts: PID 0x0031: unexpected cc 6 (expected 12)
demux_ts: PID 0x0034: unexpected cc 12 (expected 6)
demux_ts: PID 0x0034: corrupted pes encountered
demux_ts: PID 0x0034: corrupted pes encountered
demux_ts: PID 0x0034: corrupted pes encountered
audio_decoder: error, unknown buffer type: 04000000
200 frames delivered, 42 frames skipped, 2 frames discarded
demux_ts: PID 0x0034: corrupted pes encountered
demux_ts: PID 0x0034: corrupted pes encountered
demux_ts: PID 0x0034: corrupted pes encountered
demux_ts: PID 0x0034: corrupted pes encountered
demux_ts: PID 0x0034: corrupted pes encountered
demux_ts: PID 0x0034: corrupted pes encountered
demux_ts: PID 0x0034: corrupted pes encountered
demux_ts: PID 0x0034: corrupted pes encountered
demux_ts: PID 0x0034: corrupted pes encountered
audio_decoder: error, unknown buffer type: 07020000
demux_ts: PID 0x0034: corrupted pes encountered
demux_ts: PID 0x0034: corrupted pes encountered
demux_ts: PID 0x0034: corrupted pes encountered
demux_ts: PID 0x0034: corrupted pes encountered
demux_ts: PID 0x0034: corrupted pes encountered
demux_ts: PID 0x0034: corrupted pes encountered
demux_ts: PID 0x0031: unexpected cc 1 (expected 4)
demux_ts: PID 0x0034: unexpected cc 1 (expected 14)
demux_ts: PID 0x0034: corrupted pes encountered
demux_ts: PID 0x0034: corrupted pes encountered
demux_ts: PID 0x0034: corrupted pes encountered
demux_ts: PID 0x0034: corrupted pes encountered
audio_decoder: error, unknown buffer type: 0400000e
demux_ts: PID 0x0034: corrupted pes encountered
audio_decoder: error, unknown buffer type: 0700000e
demux_ts: PID 0x0034: corrupted pes encountered
audio_decoder: error, unknown buffer type: 0400001d
demux_ts: PID 0x0034: corrupted pes encountered
demux_ts: PID 0x0034: corrupted pes encountered
demux_ts: PID 0x0034: corrupted pes encountered
demux_ts: PID 0x0034: corrupted pes encountered
demux_ts: PID 0x0034: corrupted pes encountered
audio_decoder: error, unknown buffer type: 0702001d
demux_ts: PID 0x0034: corrupted pes encountered
video jump
demux_ts: PID 0x0034: corrupted pes encountered
demux_ts: PID 0x0034: corrupted pes encountered
demux_ts: PID 0x0034: corrupted pes encountered
demux_ts: PID 0x0034: corrupted pes encountered

---

### Post by xc3RnbFO8P on 2008-10-11
Search **xine** in Synaptic Package Manager,
I am not sure what is missing.
libxine1-ffmpeg
libxine1-misc-plugins
libxine1-plugins

---

### Post by dcory on 2008-10-11
I already have all the packages you mention there, as well as most of the other libxine plugins (I just don't have xvdr- I don't know what that is).

---

### Post by dcory on 2008-10-16
So new sound trouble- now, on certain stations (NBC for example), I get sound only during the commercials.  I have some theories about why this might be, but I have no idea how to fix it.

Sometimes when I load the channel it says that the audio device is unavailable because it is in use.  I'm really at a loss this time.

Thanks to anyone who posts!

---

### Post by dcory on 2008-10-16
Whoops- jumped the gun on posting that last one.  Turns out, Kaffeine is having trouble mixing 5.1 audio.  I was getting only the background noise!  Thats a different problem...

---

