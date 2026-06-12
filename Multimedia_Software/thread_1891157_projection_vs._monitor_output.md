---
title: "projection vs. monitor output"
date: 2011-12-05
forum: Multimedia Software
---

### Post by ricardisimo on 2011-12-05
Let's suppose i want to project a video out onto a screen for folks to see, but I do not want them to see my file browser, my mouse pointer, the window frame of whatever media player I happen to be using, etc., etc. I just want them to see the movie itself. Let's assume I have either two HDMI outputs, or one HDMI and one DVI-D... not sure that it matters one way or the other.

What media player should I be using? And how do I guarantee that whatever goes out of output A gives me everything my monitor would normally give me, and whatever goes out of output B shows ONLY (absolutely, positively) the video in question?

I thank you in advance for any help you can give.

---

### Post by mips on 2011-12-05
I watch tv like that. Got nvidia twinview setup and for the tv I have a tv test pattern setup as a wallpaper (you can leave it blank/black), I open vlc on the tv in fullscreen mode. You don't see anything else.

---

### Post by aeiah on 2011-12-05
the easiest thing to do would be just to set up both screens, and set a rule for mplayer to only play on monitor 2, in fullscreen. control it with the keyboard.

or do you need to see the video on your own screen at the same time?

---

### Post by ricardisimo on 2011-12-06
> **aeiah said:**
> the easiest thing to do would be just to set up both screens, and set a rule for mplayer to only play on monitor 2, in fullscreen. control it with the keyboard.

or do you need to see the video on your own screen at the same time?

Ideally I would see menus, counters, levels and such on my monitor, so as to be able to troubleshoot if need be. Only straight video out of the projector.

---

### Post by ricardisimo on 2011-12-12
Anyone? I'm more than willing to share results once I've gotten some guidance. Thanks.

---

### Post by RealityMaster on 2011-12-12
I would use VLC in minimal view and full-screen on your tv/projector.  Then you can drag the controls to the other screen, and have your playlist and controls on the display you look at and nothing else will show on the tv/projector except what you have playing in VLC.

---

### Post by ricardisimo on 2011-12-14
Interesting. OK, I'll give it a shot and report back. Thanks!

---

### Post by ricardisimo on 2012-01-23
OK... new problem. I have an nvidia G92 [GeForce GTS 250] graphics card, with two DVI-D outputs (surprisingly no HDMI, which is just weird.) I can't seem to have both of them active at the same time. In honesty, I can't get the other slot to work at all, so I'm not really sure if it's about getting them to work simultaneously, or if it's about a bad port.

How do I check? And what does it mean to enable SLI? The little bit of checking I have done this tidbit popped up.

---

### Post by ricardisimo on 2012-01-23
Alright, so I got into nvidia settings and enabled twinview, but the projector will only display my desktop background. I can't get anything else out of it. My Acer monitor is listed as "DFP-0 on GPU-0" and the projector is "DFP-1 on GPU-0". Both are listed as connection link "dual". What gives?

---

### Post by ricardisimo on 2012-01-24
OK. I have kind of got it going. Not sure how, except a WHOLE LOT of tweaking and toying with both the VLC settings and the nvidia X server settings. I will try to recreate it for anyone who is interested, but only after my projection gig tomorrow. Wish me luck!

---

### Post by ricardisimo on 2012-08-21
So, I'm back to this question of how to perfect this process. I can kind of make this work if I'm there in person to work it, but I'd like very much to be able to load files onto a server and have them run out of the projector based on a given schedule. If I should want to log in remotely (or show up in person in the projection booth) I want my session only on the monitor, NOT on screen.

So, in other words, only two options out of the projector: black screen, or the video file. The monitor should be able to see everything. Any ideas?

---

### Post by ricardisimo on 2012-08-25
Anyone? I've also posted in the [VLC Forum]("http://forum.videolan.org/viewtopic.php?f=13&t=103740") and elsewhere, and if I get this worked out I'll post a Howto.

By the way, I've determined that nvidia is just too buggy lately, so the Twinview solution (which I never really got worked out completely anyway) is no longer an option. Most likely ATI from here on out.

---

### Post by ricardisimo on 2012-08-27
Wait a second... wouldn't I just solve my problem with a second VGA adapter? Or the onboard (for monitor) and a PCI graphics card (for the projector)? Linux can run two graphics cards at once, correct?

---

### Post by ricardisimo on 2012-09-05
Once again, can Ubuntu run two graphics cards at once? Thanks.

---

