---
title: "Trouble with 4K playback with VLC on 17.10 with Intel 7th gen i5/Iris 640 gfx"
date: 2018-02-11
forum: Multimedia Software
---

### Post by ltburch2000 on 2018-02-11
I assumed that with hardware decoding and all that a 7th gen i5 with Iris 640 graphics was more than enough to handle 4K video playback but it seems not.  When I do playback all four threads go to 100% and there is occasional stuttering.  I even moved the video onto the .m2 chip so I am very sure transfer rate is not a problem.

I can play back the 4K video on a 5+ year old i7 (i7-920) and it runs about 25% on all 8 threads.

Is the problem the intel drivers with 17.10 not doing hardware decoding?  Is a 7th gen i5 simply not up to the task?  I have tried VLC with hardware decoding on automatic and forced it to XCB (not VDPAU, which as I understand it is not compatible with Intel Iris).

1080P playback works fine and gets the 4 threads to about 25% but there is no stuttering.

So is my configuration causing the issue?  I thought an i5 would be plenty, but perhaps I need the i7?

As a side note, it doesn't seem to recognize any monitor I hook it to as being capable of 4K @ 60hz, it always comes up as 4K @ 30hz.

Lee Burch

---

### Post by mc4man on 2018-02-11
Did you try vaapi hwdec? What's vainfo report?
As far as "4k" that doesn't mean much. Is it. h264 or hevc , what is the bit rate, is it 8bit or 10bit?

---

### Post by mc4man on 2018-02-11
Also on 17.10 if using wayland then you'll find your hwdec options a bit limited, not sure that vlc supports vaapi in wayland, mpv does.

---

### Post by ltburch2000 on 2018-02-11
> **mc4man said:**
> Also on 17.10 if using wayland then you'll find your hwdec options a bit limited, not sure that vlc supports vaapi in wayland, mpv does.

Looks like you were right about that, switched to mpv and CPU utilitzation during 4K playback dropped from maxing all four threads to about 60-70% on the threads, not huge but changes play from stuttering to smooth.

---

### Post by ltburch2000 on 2018-02-11
Bitrate about 43K, 8 bit h.264.

---

### Post by mc4man on 2018-02-11
On this site what does the 1st 4k show as far as cpu, here on a haswell (quad core, 8 threads) it's pretty low, about 6-7% which shouldn't be much more than 14% on your cpu
Played here by downloading & then in mpv.
[http://jell.yfish.us/](http://jell.yfish.us/)   (- jellyfish-120-mbps-4k

---

### Post by ltburch2000 on 2018-02-13
Actually the way it worked out was abandoning 17.10 and rolling back to 16.04.4.  I had several troubles with 17.10, I think Wayland being one of them.  Running with the same i5 with stock VLC the same videos ran at about 50% CPU for 43kbps 4K video under 16.04.  I think I will stick with 16.04 and then test the waters with the next LTS.  I like some of the 17.10 improvements but not enough to sacrifice smooth 4K playback and the ability to turn off screen lock.

---

### Post by ltburch2000 on 2018-02-14
Actually the way it worked out was abandoning 17.10 and rolling back to 16.04.4.  I had several troubles with 17.10, I think Wayland being one of them.  Running with the same i5 with stock VLC the same videos ran at about 50% CPU for 43kbps 4K video under 16.04.  I think I will stick with 16.04 and then test the waters with the next LTS.  I like some of the 17.10 improvements but not enough to sacrifice smooth 4K playback and the ability to turn off screen lock.

---

### Post by Habitual on 2018-02-14
[https://www.videolan.org/vlc/releases/3.0.0.html](https://www.videolan.org/vlc/releases/3.0.0.html)

---

