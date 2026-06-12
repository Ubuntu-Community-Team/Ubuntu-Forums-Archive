---
title: "sound keeps getting muted"
date: 2009-06-02
forum: Multimedia Software
---

### Post by bcrowell on 2009-06-02
I'm running jaunty on x64.

When I cold boot my computer and the gdm login screen comes up, I get the ubuntu bongo sound through the speakers. Then I log in to a Gnome session, and during the login process, I hear the speakers making a "chk" sound. After I've finished logging in, the mixer applet shows that the master playback is muted, and the volume is down at 1/31. If I unmute it and raise the volume, I get sound. However, the next time I log in the same thing happens.

The problem seems to be that the mixer applet and gnome volume control have a fixed idea that I want my sound turned off all the time. The way I can tell is by doing the following:
```

amixer -- set Master playback 100% unmute
amixer contents | head
gnome-volume-control
amixer contents | head
```
The first line of code unmutes sound, and I can verify that sound actually does work, both by playing sound through the speakers and by using the second line to view the current settings in ALSA's mixer. The third line starts up Gnome Volume Control. As soon as Gnome Volume Control starts up, I hear a "chk" from the speakers, and in the GUI, my master volume is muted again. After I exit Gnome Volume Control, the final line of code verifies that ALSA's mixer knows its volume levels have been modified.

Supporting this interpretation that it's a problem with the mixer applet and gnome volume control, I find the following. I log in to a different window manager (fluxbox) instead of Gnome, and I use amixer to turn on sound. If then reboot and log back in to a fluxbox session, I have sound. However, if I log into a Gnome session (which has the side-effect of launching mixer_applet2), sound becomes muted.

This appears to be a per-user issue. I made a new user account, and when I logged into it, I found that sound worked.

As a fix, I tried putting the amixer command in my .login, but it seems to have no effect. Does Ubuntu not execute a user's .login file? It does seem to work if I put it in my .bashrc, but that's not a good solution, because I don't want my sound settings to be modified every time I start a shell.

At this point this is basically a manageable nuisance for me, but I would be glad to hear from anyone who has more insight into what's going on, or who can suggest a permanent fix.

-Ben

This may be the same as this bug: [https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/369822](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/369822)

---

