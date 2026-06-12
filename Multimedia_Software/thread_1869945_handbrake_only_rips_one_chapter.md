---
title: "handbrake only rips one chapter"
date: 2011-10-26
forum: Multimedia Software
---

### Post by beew on 2011-10-26
Hi,

I have a movie dvd which has 19 chapters, I am trying to rip it with handbrake several times but everytime it stops at around 3% and rips only the first chapter and announces job done. 

I wanted to isolate the problem so I tried ripping on another machine and it worked, handbrake successfully ripped all 19 chapters.

To make sure the condition of ripping is the same except for the hardware I was testing with Natty installed in an external drive. I booted it off two different machines and ran handbrake. On my main machine, handbrake ripped only one chapter while on a very old hp laptop it ripped the whole thing. 

I think this  has to be hardware related (the dvd drive) but what can be the reason? How can I check? I have ripped several dvds in my main machine using handbrake and this is the first time I encounter this problem.

Thanks.

---

### Post by JohnAStebbins on 2011-10-26
I would start by comparing the activity logs of the encodes on the 2 machines.  That should indicate what is different between the encodes.  All handBrake activity logs get saved in ~/.config/ghb/EncodeLogs if you are using the GUI.

---

### Post by beew on 2011-10-27
I have tried to play the dvd with command line instead of ripping it on the machine where it has problem ripping, it turned out that the dvd stop playing at some point , here is the output.

```
Starting playback...
Movie-Aspect is 1.78:1 - prescaling to correct movie aspect.
VO: [vdpau] 720x480 => 854x480 Planar YV12 
[mpeg2video @ 0x88256a0]ac-tex damaged at 24 7
[mpeg2video @ 0x88256a0]Warning MVs not available
[mpeg2video @ 0x88256a0]concealing 1035 DC, 1035 AC, 1035 MV errors
A:   0.7 V:   0.7 A-V: -0.008 ct: -0.017  13/ 11 ??% ??% ??,?% 3 0 

demux_mpg: 24000/1001fps progressive NTSC content detected, switching framerate.
A: 211.1 V: 211.1 A-V:  0.000 ct: -0.018 5058/5055  5%  3%  1.1% 3 0 
[ac3 @ 0x88256a0]incomplete frame
A: 211.3 V: 211.3 A-V:  0.004 ct: -0.001 5063/5060  5%  3% 21.9% 3 0 


Exiting... (End of file)
bee@bee-R469-P469:~$ 
```On the other machine the playback was continuous.

So it seems there is some problem with the DVD drive But what is the problem?The output doesn't seem very informative other than that mplayer quited. All other dvds play on this machine though.

---

### Post by beew on 2011-10-28
Hello? Anyone?

---

