---
title: "ffmpeg and vhook on ubuntu 9.10 Karmic Koala"
date: 2009-11-24
forum: Multimedia Software
---

### Post by kirusoft on 2009-11-24
Hello,

I am running on ubuntu 9.10.

I installed ffmpeg with : apt-get install ffmpeg, but I believe vhook is disabled.

How can I enable vhook for ffmpeg?

Thanks for your help.
Kiru

---

### Post by Exheon on 2009-11-24
Sorry, I have to ask, (sometimes the answer is something you forget). did you put the " -vhook" option?. Cause the most of the time, if this is not defined, ffmpeg disable it.

If this is not the issue here, I would like more data, maybe the output of the error would be very helpful.

see ya

---

### Post by kirusoft on 2009-11-24
I tried to install it from source with --enable-vhook,

But I get this message **[COLOR=Red]Unknown option "--enable-vhook".[/COLOR]**

---

### Post by mc4man on 2009-11-24
You would either need to see what's possible with libavfilter, or build ffmpeg from a source revision before it was removed. ( not sure here of the actual -r.

Here's a thread from May about such ( in the context of jaunty), though also should be doable in karmic

[http://ubuntuforums.org/showthread.php?t=1153725&highlight=vhook](http://ubuntuforums.org/showthread.php?t=1153725&highlight=vhook)


Your biggest issue, if using the 0.5 ffmpeg release, would be to match up the libx264-XX and libx264-dev for 0.5. 

I'd try the karmic repo packages first, if you error out concerning x264 then **remove  libx264-dev only**, grab the jaunty libx264-XX and libx264-dev packages and install. (libx264-XX first, available [here]("http://packages.ubuntu.com/jaunty/libx264-65") and [here]("http://packages.ubuntu.com/jaunty/libx264-dev")

---

