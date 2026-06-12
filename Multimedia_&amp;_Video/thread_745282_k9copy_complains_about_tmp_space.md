---
title: "k9copy complains about tmp space"
date: 2008-04-04
forum: Multimedia &amp; Video
---

### Post by BetterSense on 2008-04-04
I'm glad that k9copy is working, so that I don't have to run dvdshrink with wine. But after every DVD, if I try to do another one it complains that there isn't enough space in /tmp/kde-chaz/k9copy/dvd or something.

 If I navigate there and rm -r * it will remove the AUDIO_TS and VIDEO_TS directories, and k9copy works again. I'm tire of doing this every time. What exactly is happening? Why doesn't k9copy delete them its own self, after it's done burning my ISO?

I understand that it's probably because my / partition is only 10GiB, but if there is enough space there to cache one DVDs worth of stuff, that's fine with me. Apparently, there is, because it works for one DVD. I don't see why it needs to store stuff from last time?

---

### Post by wolfen69 on 2008-04-04
see if there is a setting in k9copy to automatically delete the cached files.
also,```
sudo apt-get clean
```is another way to clean your /tmp

---

### Post by BetterSense on 2008-04-04
thanks, that's a lot faster than navigating there and removing it. I'll have to remember that. But I set k9copy to clear the output directory every time. Roxxorz.

---

### Post by VMan on 2008-04-04
I also set K9Copy to use a directory in my /home directory.  /tmp is on a partition with only 10G.  /home has a few hundred.  I also save the files for other uses.

---

