---
title: "Compiz and video display messed up after kernel upgrade"
date: 2006-09-20
forum: Multimedia &amp; Video
---

### Post by redpants on 2006-09-20
After an update a little less than a week ago, my wireless card suddenly stopped working (hardware not recognized).  I had an almost identical problem before and I followed the troubleshooting steps I used before to get it working, but it was to no avail.  So, right before I was about to give up, I got an "updates available" notice, so I ran the full set up updates for my system.  It apparently installed the latest kernel, 2.6.15-27-686, and upon rebooting to the new kernel, my wireless was working flawlessly again.  However, none of my compiz effects are working at all, and all of the video transitions (i.e., maximizing a window, minimizing, etc.) are very choppy.  

I assumed that I needed to reinstall the video driver, so I followed the instructions listed here:  [http://www.ubuntuforums.org/showthread.php?t=204910](http://www.ubuntuforums.org/showthread.php?t=204910) , except I used the latest version of the ATI driver, 8.28.8.  I used that version because a while back I had already downloaded it to my hard drive, and for some reason I couldn't ever download the 8.27.10 version listed in the howto (it kept timing out around 10%).  I didn't receive any errors while doing the steps in the howto, but I'm still experiencing the same issues.

I ran fglrxinfo in terminal and received the following error:

Error:  unable to open display :0

I have no idea what to do.  I'm trying my best to learn linux but continue to get frustrated because every time I run into an issue (which seems to be every time I run an update) I have no idea where to start to troubleshoot the issue.  Does my problem have something to do with compiz?  With my video driver?  Is this punishment for not learning linux years ago in college when I had the chance?

Could someone please help me troubleshoot this?  I really like what I've seen with Ubuntu so far, but having a new problem with every "update" is starting to really wear on me.

---

### Post by redpants on 2006-09-20
Perhaps also worth mentioning:  After the kernel upgrade I could still log onto the old kernel and the compiz features would still work fine...however, after running the driver install, I have the same video problems on the old kernel.

---

### Post by redpants on 2006-09-22
Got it working.  Had to remove all the settings I made for XGL/Compiz, reinstall the video driver, then I reinstalled XGL/Compiz...except I used method 2 instead of method 1 found here:  [http://www.compiz.net/viewtopic.php?id=389](http://www.compiz.net/viewtopic.php?id=389) 

For some reason the original method would no longer work for me.  Still can't figure out why, but at least it's all working now :)

---

