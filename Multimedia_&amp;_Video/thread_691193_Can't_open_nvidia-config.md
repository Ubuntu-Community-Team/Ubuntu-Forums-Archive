---
title: "Can't open nvidia-config"
date: 2008-02-08
forum: Multimedia &amp; Video
---

### Post by bjorn.haaland on 2008-02-08
Hello,

I wanted to set up dual-screens, and after some searching, I found out about the command:

gksudo nvidia-config

I was told that this was so simple, just open that one up and configure to your heart's desire! Great, so I did. I quickly found out how to run a dual monitor setup (not cloned). Awesome. Then I started getting a headache after a few minutes and checked my refresh rate. Really low, and something must be done about it. So I figured I'd open up nvidia-settings again, but now I can't - upon doing 'gksudo nvidia-config', I'm getting nothing - just a new blank cmd line.

In addition to this, the setup isn't really working. I'm finding that stuff is loading slower(!) now (I do it just fine in WXP, so it's not due to a low system spec) - and also, when opening Amarok or Firefox, the Close/Maximize/Minimize buttons are just -- gone. I don't think I'm happy about the dual-screen state of Ubuntu if this is what I'm getting. I'm spoiled :)

Anyway, the problem is of course to reset this now. And I can't do that without being able to enter nvidia-config. I've tried searching, but I can't seem to find a solution to this. Any help is appreciated.. I guess I'm on back on windows meanwhile.

---

### Post by xc3RnbFO8P on 2008-02-10
Make sure you got **Nvtv TV OUT** installed, it is in the Add/Remove (All Available Application)
If you cant start it in: Application>Sound & Video
Use Terminal: 
> nvidia-settings

---

