---
title: "amd a5300 - play video problems - have installed catalyst control center"
date: 2013-01-21
forum: Multimedia Software
---

### Post by sdpagent on 2013-01-21
Ok so i bought the amd5300 cpu with integrated graphics for my HTPC after reading that it can play 1080p video no sweat. I installed the drivers from the ati website (using the ubuntu drivers thing resulted in an 'unsupported watermark' which is now gone). 

I transferred the batman 1080p mp4 video to the machine and whenever I launch it vlc just freezes. I also seem to be unable to play any flash content. An image will load and it will just freeze, like it did with vlc.

Any ideas before I go and slap myself for buying a modern processor for linux? (should probably have just bought an older one that is more likely to be supported)

(machine is fully up to date).  Would it help if i installed 64bit ubuntu instead of 32 bit? I usually go 32 to be safe...

Stu

---

### Post by Bucky Ball on 2013-01-21
*Thread moved to **Multimedia & Video***

In future, to improve your chances of getting help, please use descriptive thread titles. 'amd a5300' is generic and gives no information whatsoever about your issue. Many will just move on.

---

### Post by sdpagent on 2013-01-21
> **Bucky Ball said:**
> *Thread moved to **Multimedia & Video***

In future, to improve your chances of getting help, please use descriptive thread titles. 'amd a5300' is generic and gives no information whatsoever about your issue. Many will just move on.
Sure thing - i have updated the title.

---

### Post by Bucky Ball on 2013-01-21
;) Good luck.

---

### Post by sdpagent on 2013-01-21
Ok so I tried out using 64 bit Ubuntu. The difference this makes compared to using 32 bit cannot be emphasized enough. The machine is lightning fast to what it was before. Definitely DO NOT use 32 bit linux with this processor. It plays 1080p movies and flash content no sweat. 

The only thing I don't like is the fact that I cant get 'ubuntu 3d' option at the login screen (stuck on 2d with crap effects and inability to drag windows between screens). I guess there is no opengl support on this chip or something? I am unable to run xbmc as It gave me an error message that I need 'hardware acceleration' enabled. I am now messing with the ubuntu drivers to see if installing those will enable it (and not get that really annoying amd unsupported hardware watermark)

----------
Update 
Tried installing fglrx and fglrx-updates, both resulted in screen tearing and the unsupported watermark (but allowed xbmc to be started, and seems really fast/smooth)
Uninstalling fglrx removed the unsupported watermark, and the screen tearing, and Xbmc will start now, when it wouldnt before? I guess a configuration setting got set and didn't get unset when I removed the drivers? Anyway problem solved.

---

### Post by Bucky Ball on 2013-01-21
Good news and nice figuring. Could you please mark the thread as Solved from Thread Tools at top right to help others. Cheers.

---

