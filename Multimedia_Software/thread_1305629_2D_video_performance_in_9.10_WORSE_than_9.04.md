---
title: "2D video performance in 9.10 WORSE than 9.04"
date: 2009-10-30
forum: Multimedia Software
---

### Post by ubigT on 2009-10-30
Playing .avi and .mkv files (some 720p) lags and stutters in 9.10.  I just installed Karmic today and enabled/installed medibuntu and the 185 Nvidia drivers for my GT9500.  I use this computer as my media PC so video performance is important. My resolution is 1400x1050 and I have tried VLC, Totem and Gnome MPlayer and none of them play smooth video, 9.04 was way better in this regard. So what can I try? Any advice would be greatly appreciated!

---

### Post by ubigT on 2009-10-30
BUMP

Anyone had similar problems?

---

### Post by slumbergod on 2009-10-30
I had a nightmare with Jaunty and video playback (many mkv files would overheat my CPU so much the pc shutoff). Ok, I just use a laptop with onboard Intel graphics. Video performance is a little better with Karmic but still not as smooth as I was hoping. Actually, Karmic feels quite sluggish on my system.

---

### Post by c-shadow on 2009-10-30
> **ubigT said:**
> Playing .avi and .mkv files (some 720p) lags and stutters in 9.10.  I just installed Karmic today and enabled/installed medibuntu and the 185 Nvidia drivers for my GT9500.  I use this computer as my media PC so video performance is important. My resolution is 1400x1050 and I have tried VLC, Totem and Gnome MPlayer and none of them play smooth video, 9.04 was way better in this regard. So what can I try? Any advice would be greatly appreciated!

Try using mplayer and VDPAU output. That solved my problems in 8.10, my 9600GT does all the decoding now, CPU usage with 720p movies is about 5% and no more stuttering and tearing.

---

### Post by ubigT on 2009-10-30
Wow, that made a ton of difference! Thanks.  I had tried a few different output settings but not this one, my CPU has almost no load while playing videos now, and they are smooth.

---

