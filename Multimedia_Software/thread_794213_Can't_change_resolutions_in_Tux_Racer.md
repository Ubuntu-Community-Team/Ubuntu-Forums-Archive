---
title: "Can't change resolutions in Tux Racer"
date: 2008-05-14
forum: Multimedia Software
---

### Post by timzak on 2008-05-14
I just installed a new monitor.  It's widescreen, 1440x900.  I used to use a CRT @ 1280x960.  I tried loading Tux Racer and it seems to only be able to run in 1440x900 windowed mode (I can see my top and bottom panels, so the resolution is actually a little lower--1436x850 or something like that).  When I try to change resolutions, it stays at current resolution.  With my previous CRT monitor, I had no problems running in any resolution from 640x480 to 1600x1200.  Now I seem to be stuck in one resolution.  Any ideas?

Edit:  also had a problem with Nexuiz, a 3D FPS, being stuck in a weird resolution and unable to change.  Is that just how widescreen monitors are, or should they be able to run any resolution?

---

### Post by timzak on 2008-05-14
Could this be related to the new xorg.conf file in Hardy not having discrete resolutions like it did in Gutsy?  I've looked into Hardy's xorg file and it's way simplified compared to previous Ubuntu versions.  Maybe I need to manually input all the lower resolutions in my xorg file?  Any help appreciated.

Thanks.

---

### Post by timzak on 2008-05-15
I think this issue is related to the new version of xorg that comes with Hardy.  I say this because I have similar issues with other 3D games that were not there with Gutsy.  My hardware has not changed since Gutsy.

It seems that when I select my monitor's native resolution in a 3D game, it has trouble going to full-screen mode, leaving my desktop panels showing above and below the game screen.  There is confusion between the desktop mouse and the in-game mouse and in some cases this prevents me from playing the game.  The solution, I've found, is to select a lower resolution.  For some crazy reason, when I do this, then it displays the game in 1440x900 full-screen!  Why it doesn't actually set the game to the lower resolution, I don't know.  Anyone have any ideas?

---

### Post by michaelzap on 2008-05-31
I'm having the same problem and would love to know how to resolve it.

---

### Post by timzak on 2008-06-02
> **michaelzap said:**
> I'm having the same problem and would love to know how to resolve it.

Hi, 

re-read my last post for my solution.  It may or may not work for you.  I'm not really a gamer, so I am not too bothered by this.  I was just testing to see how a few games looked on my new monitor.  Let me know if you find a better solution.

Thanks.

---

### Post by michaelzap on 2008-06-02
> **timzak said:**
> Hi, 

re-read my last post for my solution.  It may or may not work for you.  I'm not really a gamer, so I am not too bothered by this.  I was just testing to see how a few games looked on my new monitor.  Let me know if you find a better solution.

Thanks.

I've tried launching Urban Terror in 640x480 (and many other resolutions), but it won't work at all in full-screen mode.

---

### Post by michaelzap on 2008-06-04
> **michaelzap said:**
> I've tried launching Urban Terror in 640x480 (and many other resolutions), but it won't work at all in full-screen mode.

Hooray! In the last few days I've downloaded an nVidia update and the new kernal, and Urban Terror now works full-screen! I just tried it again and it worked.

---

