---
title: "Youtube Freezes Full Screen"
date: 2012-10-16
forum: Multimedia Software
---

### Post by scpatl4now on 2012-10-16
I have been having a problem with YouTube videos freezing up my system when I'm in full screen...the only option is to Alt+sysrq+k to get out of it.  I'd like to try and trouble shoot it, because its a real pain to have to go back to the log on screen and sign in again.  It only happens full screen.

Nvidia driver ver 304.43
GeForce 7600 GS
Linux ver 12.04

---

### Post by md2020 on 2012-10-31
I had a similar issue with VLC and Ubuntu 12.04 that I was able to resolve:  [http://ubuntuforums.org/showpost.php?p=12328809&postcount=19]("http://ubuntuforums.org/showpost.php?p=12328809&postcount=19")

---

### Post by rectec794613 on 2012-11-01
> **scpatl4now said:**
> I have been having a problem with YouTube videos freezing up my system when I'm in full screen...the only option is to Alt+sysrq+k to get out of it.  I'd like to try and trouble shoot it, because its a real pain to have to go back to the log on screen and sign in again.  It only happens full screen.

Nvidia driver ver 304.43
GeForce 7600 GS
Linux ver 12.04

I'm having the same problem! I blame Adobe Flash Player. It seems Adobe don't pay too much attention to Linux and as a result, Flash is a bit buggy. 

When it freezes on me - as it seems to do about 50% of the time - I just move to a different workspace and kill plugin-container with a task manager. It's a real pain and I'd gladly use an open source alternative like Gnash or Lightspark, if only they were up to date and less buggy.

I'm running the proprietary ATI drivers, over here. After it freezes, if I want to watch the video in a larger size, I'm forced to run Firefox in fullscreen, enlarging the video size and zooming in the page. It's definitely not optimal. I'd much rather be able to watch in fullscreen than that.

If the community could focus a little more on developing the open source flash players, our Flash experience could be *so* much better.

I've tried all sorts of configurations with FlashAid. Both beta and stable with/without GPU validation overridden, npviewer fix, etc. All give the same problem with the fullscreen freezing. If anyone has a possible fix, I'm sure many of us would welcome it.

---

### Post by evilsoup on 2012-11-01
For what it's worth, VLC can take youtube.com links and play the video (you can select your preferred resolution in VLC's preferences). So if it's a flash problem, you can try that (this is my preferred method of watching flash videos on my netbook, combined with the firefox add-on '[open with]("http://www.darktrojan.net/software/addons/openwith")').

---

### Post by Champlin93 on 2012-11-01
Have you tried right click>settings>display(first tab on the left)>check/uncheck hardware acceleration?

---

