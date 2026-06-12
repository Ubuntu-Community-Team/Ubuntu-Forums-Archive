---
title: "Flash 10: Video corruption on YouTube videos."
date: 2008-07-12
forum: Multimedia Software
---

### Post by Sslaxx on 2008-07-12
Ubuntu updates upgraded the version of Flash to 10. Now I'm experiencing trouble with video playback - there's corruption noticeable on the videos. [http://uk.youtube.com/watch?v=-PKL8LQH3rI](http://uk.youtube.com/watch?v=-PKL8LQH3rI) and [http://uk.youtube.com/watch?v=4nigRT2KmCE](http://uk.youtube.com/watch?v=4nigRT2KmCE) are examples. [http://www.vimeo.com/1311784?pg=embed&sec=1311784](http://www.vimeo.com/1311784?pg=embed&sec=1311784) is a non-YouTube example.

---

### Post by philstovell on 2008-07-12
I'm also having trouble. [This video]("http://news.bbc.co.uk/1/hi/7502968.stm") worked earlier before the upgrade and failed afterwards. I've uninstalled version 10, forced back to version 9 an pinned it. The video now works again.

---

### Post by Sslaxx on 2008-07-12
Yeah, I'm a bit miffed about having a problematic version of Flash made available. What was wrong with version 9, exactly, that required it to be replaced with an unstable version?

---

### Post by Tinono on 2008-07-12
> **Sslaxx said:**
> Yeah, I'm a bit miffed about having a problematic version of Flash made available. What was wrong with version 9, exactly, that required it to be replaced with an unstable version?

That's what backports do... Make unstable and problematic software from the development branch available to stable users. Get rid of the backports repo if such problems bother you. This repo is off by default, for a reason.

---

### Post by Melcar on 2008-07-12
Here too.

---

### Post by portach king on 2008-07-12
Yeah, I'm also having trouble. I also fond that Firefox use's much more CPU since I installed Flash 10 beta 2.

---

### Post by cmckdub on 2008-07-13
I also found that Flash version 10 was a problem. When I browsed to a page I wrote (which contained a Flash object), it forced Firefox to close without warning. I have noticed that according to [the Adobe site]("http://www.adobe.com/products/flashplayer/") the latest version of Flash is version 9.
[http://www.adobe.com/products/flashplayer/](http://www.adobe.com/products/flashplayer/) 
I suspect the update for version 10 is some kind of error. It may also be related to [the following article]("https://launchpad.net/ubuntu/hardy/+source/flashplugin-nonfree/10.0.1.218+10.0.0.525ubuntu1~hardy1+really9.0.124.0ubuntu2") which I could not understand...

[https://launchpad.net/ubuntu/hardy/+source/flashplugin-nonfree/10.0.1.218+10.0.0.525ubuntu1~hardy1+really9.0.124.0ubuntu2](https://launchpad.net/ubuntu/hardy/+source/flashplugin-nonfree/10.0.1.218+10.0.0.525ubuntu1~hardy1+really9.0.124.0ubuntu2)

When I removed Flash in Synaptic, all was well - flash then played fine, even though synaptic said it was not installed, and synaptic seemed to have nothing else installed that would play it.

Found the [bug related to this issue]("https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/239182"). Details are at:
[http://ubuntuforums.org/showthread.php?t=856764](http://ubuntuforums.org/showthread.php?t=856764)

---

