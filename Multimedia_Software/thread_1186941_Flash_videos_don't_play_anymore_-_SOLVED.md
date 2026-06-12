---
title: "Flash videos don't play anymore - SOLVED"
date: 2009-06-14
forum: Multimedia Software
---

### Post by kwilliam on 2009-06-14
I figured this out on my own, but the problem/solution was so unexpected I thought I'd share it.

A few days ago, after doing an apt-get upgrade, YouTube videos stopped working. I thought it was a problem with YouTube, but then found Pandora and lots of other sites would not play music or video. The rest of Flash worked fine. But at best, videos would play a split-second and then freeze. I assumed it was a problem caused by the upgrade, and was looking through /var/log/dpkg.log for changes to Flash, my video card driver, and my sound system.

But I finally found the problem - my / partition was 100% full! I went for two days like this, and Flash videos not playing was the only symptom, because my /home partition had plenty of room. Presumably, the Flash plugin uses some location (maybe in /var?) to buffer videos and music, and no longer had any room to do that. So I cleared out some space, and now it works fine again.

I figure only 1 out of a million Linux users who have trouble with Flash will experience the same problem I had, and while I'm laughing about it now, it was miserable for those few days spent searching the web - the top Google hits for Flash problems on Ubuntu are seriously outdated. So this post is for that one person who manages to be as clueless as me, and perceives a full hard drive as a Flash player problem, lol! 

Keywords: June 2009, Ubuntu 9.04, Flash problem, flashplugin-nonfree, flashplugin-installer, adobe-flashplugin, YouTube won't don't doesn't play video, Pandora won't play sound

---

