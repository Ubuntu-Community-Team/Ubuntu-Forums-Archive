---
title: "[SOLVED] No Sound - Blank Alsamixer and Errors - Intrepid 8.10"
date: 2008-11-05
forum: Multimedia Software
---

### Post by pyromanic123boom on 2008-11-05
**After upgrading to 8.10, all my sound is gone.  When I open alsamixer, it is just blank-**

[IMG]http://pyromanic.publichost.de/img1.png[/IMG]
[B]
When I try to open a video in Totem, it says this-[/B]

[IMG]http://pyromanic.publichost.de/img2.png[/IMG]

**When I double-click on the volume button, it gives me-**

[IMG]http://pyromanic.publichost.de/img3.png[/IMG]
[B]
So you can see my audio isn't muted or anything like that.[/B] 

I don't understand what is wrong, because I literally *just* had audio only a few days ago.  I really am regretting this upgrade, now that this seems to be a part of a continuing pattern of problems.  It's very frustrating because I need to work with some video editing, and can't listen to the audio.  If anyone can help me out with this, it would be great!

---

### Post by xdotx on 2008-11-05
Looks like a pulseaudio problem. There's many related posts on the forum.
[http://ubuntuforums.org/showthread.php?t=885437](http://ubuntuforums.org/showthread.php?t=885437) seems particularly helpful.

---

### Post by smlefo on 2008-11-05
I have the same problem, and it is really frustrating.  Especially since my sound worked just fine on 8.04 (except for applications that need JACK to work...).

I'm pretty infuriated right now.  I hope the Ubuntu folks fix all these sound issues they CONSTANTLY have every update.

EDIT: I just noticed you have HDA Intel.  So do I.  I wonder if it's related.

EDIT2: I fixed it by killing pulseaudio:

```
(17)[20:22] ~$ ps aux | grep pulse
sean      5674  0.0  0.0   3124   676 ?        S    19:46   0:00 /usr/bin/dbus-launch --exit-with-session /usr/bin/pulse-session /usr/bin/seahorse-agent --execute x-session-manager
sean      5678  0.1  0.1  21760  4012 ?        Ssl  19:46   0:03 /usr/bin/pulseaudio -D --log-target=syslog
sean      5680  0.0  0.1   7528  2552 ?        S    19:46   0:00 /usr/lib/pulseaudio/pulse/gconf-helper
sean     14352  0.0  0.0   3240   816 pts/0    S+   20:25   0:00 grep pulse
(18)[20:25] ~$ kill 5678
```

~Sean

---

### Post by pyromanic123boom on 2008-11-05
Well I tried this, and then restarted.  When I brought the list up, I noticed pulse audio was running in some other accounts as well.  It seems like it is a one-time thing, but if it happens again, I'll follow this! If someone has a launchpad account, they can post it there (it may be already).  Thanks for the fix Sean!

---

