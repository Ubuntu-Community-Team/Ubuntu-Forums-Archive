---
title: "VLC not maxing out the processor"
date: 2011-07-23
forum: Multimedia Software
---

### Post by Ranko Kohime on 2011-07-23
I've got an Intel Core i7-2720QM, with a rated frequency of 2.2GHz.  It runs too hot for my liking under load at that speed, and significantly cooler at lower speeds, so I slow it down using cpufreqd to about 1.3GHz.

At 2.2GHz, VLC will play a particular 1080p video well, only glitching the video on fast forwarding.  When slowed down to 1.3GHz, VLC runs consistently <200% via htop, and <35% via conky, but it drops reference frames around high-motion portions of the video.  This with post-processing and deinterlace disabled.  If either is enabled the video never recovers and I get nothing but the last frame it froze on until I turn these options off.

I never see spikes over 200%, even in top with refresh at 0.09, and running the above mentioned filters drags it up to about 250%, so I'm left wondering why VLC won't max out the processor if it needs to, to play the video smoothly?

---

### Post by handy on 2011-07-24
In case you can't find another answer, & if the machine is not a notebook or the like, you could spend a little & improve the CPU cooling situation. 

7 years ago I bought a completely copper heat-pipe/sink cooler with a large (quiet) fan, it did wonders for the Athlon64 3500+ that was over clocked to the max. Both the CPU & the cooler are still functioning fine. :)

---

### Post by Ranko Kohime on 2011-07-24
> **handy said:**
> In case you can't find another answer, & if the machine is not a notebook or the like, you could spend a little & improve the CPU cooling situation. 

7 years ago I bought a completely copper heat-pipe/sink cooler with a large (quiet) fan, it did wonders for the Athlon64 3500+ that was over clocked to the max. Both the CPU & the cooler are still functioning fine. :)
Yeah...Notebook.  I wish I could do something about cooling, I really do.  The temps bug me.  :(

Now if this was a desktop, I'd have it dunked in a tank of oil.

---

### Post by mc4man on 2011-07-24
Just curious about something - are you saying it runs too hot with the default of ondemand and your setting down to 1.3GHz all the time or just with vlc
Or aren't you using ondemand at all

As far as vlc I wouldn't expect it to be using all of your cores for decoding

---

### Post by Ranko Kohime on 2011-07-24
> **mc4man said:**
> Just curious about something - are you saying it runs too hot with the default of ondemand and your setting down to 1.3GHz all the time or just with vlc
Or aren't you using ondemand at all

As far as vlc I wouldn't expect it to be using all of your cores for decoding
I've modified the ondemand profile in cpufreqd to be between 800MHz and 1.3GHz, so the frequency maxes at 1.3GHz.

Any particular reason why VLC would NOT be using all the cores?  (It has the appearance of doing so, as no particular core is maxed out, according to htop, even when VLC is running over 200% CPU time, but all of the "real" cores (I have 8 due to hyperthreading, but only 4 real cores), show elevated levels, over 50% use each)

---

### Post by mc4man on 2011-07-24
Actually you're right, in 11.04 vlc does mt decoding thru avcodec
On a core2duo
 > avcodec decoder debug: trying to use direct rendering
[0x9779030] avcodec decoder debug: allowing 2 thread(s) for decoding
[0x9779030] avcodec decoder debug: ffmpeg codec (H264 - MPEG-4 AVC (part 10)) started
[0x9779030] avcodec decoder debug: using frame thread mode with 2 threads


Haven't paid any attention there because the only time I've had issue with some vids is when the cpu's aren't scaled up when needed during playback due to the high default up_threshold (90) for ondemand
(I only use ondemand in 11.04 and 11.10

So I think the freq is more important than the % of cpu(s) use. (At  least here where I have nvidia and don't find vaapi gpu decoding in vlc to work that well as compared to mplayer which works very well with vdpau
 I just lower the up_threshold, usually to 75

---

