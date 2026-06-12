---
title: "Flash video lag"
date: 2008-09-28
forum: Multimedia Software
---

### Post by afterburner on 2008-09-28
Hi all, I have an IMB T40 with an ATI Radeo 7500 32MB video card, 1.5 GHz, 512MB RAM, and Ubuntu 8.04.

The problem is as follows...When I visit YouTube and play a video normally the CPU goes up to 50% usage. I'm fine with this, but if I want to full screen a video, the CPU usage goes to 100% and the video lags.

I'm wondering if this is normal, and whether this is because of the old hardware or maybe some kind of a bug. I'm pretty sure I have the latest flash player version, In fact I tried reverting to an older version to see if that would change anything, and it did - the flash videos didnt show up at all, so I reinstalled the latest version of flash player...

All other functions work perfectly - namely the compiz desktop effect.

Any ideas?

---

### Post by Bakon Jarser on 2008-09-28
By latest flash version I'll assume you mean flash 9.  Flash 10 has improved performance quite a bit.  It is currently in it's second release candidate and is very stable.  But to answer your question yes, flash is a cpu hog.

---

### Post by Grimhound on 2008-09-28
> **Bakon Jarser said:**
> By latest flash version I'll assume you mean flash 9.  Flash 10 has improved performance quite a bit.  It is currently in it's second release candidate and is very stable.  But to answer your question yes, flash is a cpu hog.
Running 10 here, improves nothing. Sucks 95-100% CPU.

---

### Post by afterburner on 2008-09-29
Ok, I've found a compromise solution for this.

Since the normal youtube video size takes up 50% CPU, and full screen is 100%, i resize the video of the screen in such a way, so that the cpu usage is 80-90%.

You will have to open the flash video in a new window, and play around with the window size, until you find a good compromise performance-wise. Then just leave that size as your regular window size (not maximized), and open the flash video in a new window.

To open the flash video in a new window just copy the code of the video thats after "watch?v=". It a bunch of letters and numbers. Then open a new browser window and paste the video code after the youtube url and /v/   
or delete everything until just the youtube url is there ending in .com, then type /v/ and paste the video code, minimize and you're done! so...

The video you want to watch in new window is
[http://www.youtube.com/watch?v=ABCDEFG](http://www.youtube.com/watch?v=ABCDEFG)

you copy the ABCDEFG, open new window.

then
[http://www.youtube.com/v/ABCDEFG](http://www.youtube.com/v/ABCDEFG)

simple as that

The video will open in a new window and you can resize according to your needs, whether CPU reasons, or whether you just want a bigger video than the original, but dont want to go full screen

---

