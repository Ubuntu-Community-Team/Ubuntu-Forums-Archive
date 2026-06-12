---
title: "ubuntu 9.04 beta - vlc in two windows"
date: 2009-04-14
forum: Multimedia Software
---

### Post by domagoj412 on 2009-04-14
Hello,
I have updated ubuntu 8.10 to 9.04 and now problem occured in vlc player...
Don't know is it because this is beta version or I did something...

When I start a video it needs two windows to play it. One of them is main window with Play/pause and second one is video itself in maximized window...

Anyone know what could be the problem?

---

### Post by darknightiso on 2009-04-16
And one says VLC (XVideo Output)?
I also have the same problem. 
where you able to fix it? because I sure haven't yet :[

---

### Post by vlovich on 2009-04-16
it seems embedded mode broke with the Jaunty update.  I've also tried 0.9.9a from the ppa, & still no luck.

---

### Post by mc4man on 2009-04-16
for jaunty you may try here
[http://ubuntuforums.org/showthread.php?t=1111272](http://ubuntuforums.org/showthread.php?t=1111272)

Whether or not it's suitable will depend on one's use.
The embedded is considered broken in 0.9.x, fixed in 1.0, but note that ALL 0.9.x and 1.0 versions are broken in some manner.
What's good for one won't be for someone else.

All 0.9.x versions can be patched to include the embedded before building, again for some it works fine, others not so.

I've found 0.9.9a fully patched to be the best of the lot for hardy and intrepid, but that's in relation to my use. (and actually for hardy 0.8.6 is worth keeping installed (run 0.9.9a or 1.0 from build folder

---

### Post by binbash on 2009-04-16
Install vlc from this repo, it is fixed there, i am using it : 

deb [http://ppa.launchpad.net/medigeek/ppa/ubuntu](http://ppa.launchpad.net/medigeek/ppa/ubuntu) jaunty main

---

### Post by giest on 2009-04-26
> **binbash said:**
> Install vlc from this repo, it is fixed there, i am using it : 

deb [http://ppa.launchpad.net/medigeek/ppa/ubuntu](http://ppa.launchpad.net/medigeek/ppa/ubuntu) jaunty main

that VLC bug going to be fixed in vlc1.0, but it seems to be fixed in 9.9a for me.
[http://forum.videolan.org/viewtopic.php?f=13&t=58405](http://forum.videolan.org/viewtopic.php?f=13&t=58405)

I can confirm that this repo fixes vlc on ubuntu64 with vlc9.9a.  Thanks binbash.

---

