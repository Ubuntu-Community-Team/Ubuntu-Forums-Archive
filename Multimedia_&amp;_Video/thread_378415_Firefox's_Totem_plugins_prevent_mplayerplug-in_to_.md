---
title: "Firefox's Totem plugins prevent mplayerplug-in to work"
date: 2007-03-07
forum: Multimedia &amp; Video
---

### Post by serge on 2007-03-07
Hi to all: 
Just installed Herd 5 and it's an ABSOLUTE GEM !!! Congratulations !:KS 
I'm especially interested to play video content on as many web sites as possible, and so far Herd5  looks impressive.
Just one question: It looks like the Firefox's Totem plugins are sort of overpowering, i.e., not allowing mplayerplug-in to load when a site wants to play the video. I know that I can go to the "plugins" directory and remove (manually) the plugins that are preventing mplayerplug-in to work. But is there another way, i.e., to keep them all?

Many thanks for a GREAT distro, and best regards to all,
serge.

---

### Post by bruenig on 2007-03-07
They serve the same role, you can't have both of them. That is like having gnash and adobe flash installed and wondering why one works and the other doesn't. Just sudo apt-get remove totem-mozilla and you should be fine.

---

### Post by serge on 2007-03-08
Thank you bruenig.  Yes, you completely answered my question.
Best regards,
serge.

---

### Post by frodon on 2007-03-08
Trust me if you are using firefox the sweetest solution for all embedded streams is the "media player connectivity" extension of firefox, it just open the stream with the player of your choice :
[https://addons.mozilla.org/firefox/446/](https://addons.mozilla.org/firefox/446/)

This extension just rocks :)

---

### Post by serge on 2007-03-08
Thanks frodon: WOW !!! You people are REALLY GREAT. I can see why UBUNTU is #1 on Distrowatch.
OK, I just installed the suggested extension, but have not had chance to try it. I need to "fix" all the plugins (the  ".so")  that I moved yesterday, when I was trying to see which one works with which stream. I will do that and report (if anyone is interested-hope I won't be wasting your forum's space) on my experience.
Many thanks,
serge.

---

