---
title: "VLC and Totem problems"
date: 2007-12-29
forum: Multimedia &amp; Video
---

### Post by MasterRoshi on 2007-12-29
hey again all!

im having problems with my ATI drivers and the totem movie player. i enabled the ATI drivers in restricted, and it made my desktop MUCH crisper. totem will close on opening now, so i decided to install VLC. VLC plays the DVD, but it's all choppy and skippy. audio matches and does not skip. just video playback.

i know it is not the DVD drive, or the DVD, because they work on my vista partition (dual boot), and my desktop. it also worked before the ATI drivers were enabled.

anyone have a similar problem or suggestions? id like to keep my ATI drivers installed and operational.

thanks!

---

### Post by rainwalker on 2007-12-30
For the DVD, have you installed libdvdcss?

[http://packages.medibuntu.org/pool/free/libd/libdvdcss/](http://packages.medibuntu.org/pool/free/libd/libdvdcss/)

---

### Post by MasterRoshi on 2007-12-30
i believe i had it installed already...but just re-installed it to be sure. 

inserted a DVD, totem came up and then closed almost instantly. VLC still plays it, but it is still choppy. =/

any more ideas? it works without my ATI driver enabled...but i hate disabling it...it make makes me laptop look like crap.:(

---

### Post by rainwalker on 2007-12-30
Hm...I don't know, installing that did it for me.
I can tell you how to set it to automatically play with VLC, though. Kind of off-topic, but still nice.

---

### Post by usergroup81 on 2008-01-10
Not sure but this worked for me. Go into your VLC Settings>Preference>Video>Output Modules and check the Advanced option and choose X11 video output. The choppiness went away but the video quality also decreased. Hope it works for you.

---

### Post by eye208 on 2008-01-10
> **usergroup81 said:**
> choose X11 video output.
How about enabling XVideo in the ATI driver instead? That should give you much better quality (and less CPU load) than X11 video.

sudo aticonfig --ovt Xv

---

### Post by rainwalker on 2008-01-10
> **eye208 said:**
> How about enabling XVideo in the ATI driver instead? That should give you much better quality (and less CPU load) than X11 video.

sudo aticonfig --ovt Xv

If I'm using the open driver, not the restricted one, and I have all my video stuff working, will this improve anything?

---

### Post by eye208 on 2008-01-11
> **rainwalker said:**
> If I'm using the open driver, not the restricted one, and I have all my video stuff working, will this improve anything?
No. Only the proprietary driver has XVideo disabled by default.

---

### Post by MasterRoshi on 2008-01-13
it worked! the other option with the sudo command didnt do it for me...the video was still choppy. thanks guys!

---

