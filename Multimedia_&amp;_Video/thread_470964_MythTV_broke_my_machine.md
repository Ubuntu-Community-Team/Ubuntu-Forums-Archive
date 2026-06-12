---
title: "MythTV broke my machine?"
date: 2007-06-11
forum: Multimedia &amp; Video
---

### Post by jaw1959 on 2007-06-11
I installed MythTV today using synaptic package manager and rebooted the machine (x86, 7.04).  The machine began to start normally, but fails to display the login screen.  I've had this machine set to login automatically, but I turned that off just prior to the reboot (mythtv seemed to have added a new user and I wanted to see what was up with that).  Now the machine sits with a black screen with a "busy" indicator.   Does this happen with MythTV? If anyone has any idea for how I can simply get to my login screen I'd be happy to figure it out from there.   Does anyone have any ideas?

---

### Post by barney_1 on 2007-06-11
Hmm... that's odd.  

To start trouble shooting this I would suggest you reboot and from the grub menu choose to boot into recovery mode.  Then you get to the console, take a look at your logs and see if you can find the reason your system wasn't running.   I believe the pertinent logs would be:
```
/var/log/Xorg.0.log
/var/log/syslog
```

If you can't figure anything out from that you could try uninstalling mythtv and see if that fixes it. I'm not sure that it will, I really need more info to diagnose the problem.

Uninstall from the console:
```
sudo apt-get remove mythtv
```

---

### Post by jaw1959 on 2007-06-11
I've watch the machine boot from recovery mode, and the only error I see is where the machine fails to mount my external hard drive (which I have intentionally detached) but it seem to handle the error fine.  The problem seems to be centered with the welcome screen.  I had this machine setup to login automatically, but then I turned that off.  At the time I made that change, I also changed the welcome screen it would use from "blubuntu" to the default welcome screen.  When it gets to the point where it would normally load the welcome screen, it changes screen modes, displays what looks like a clock (or something, it's something along the lines of a rotating hour glass, or the pinwheel from mac...some kind of "busy" indicator....I don't know what other terms to use).  The screen shows this "busy indicator" for a few seconds, then changes screen modes again, and then it finally hangs there.  I've had a stable xorg.conf for a long time, but just to be safe, I switched that to use the default driver, and then back,  and then I ran the dpkg config program, and nothing seems to have changed.  My guess is that the welcome screen I chose is the culprit. There must be a way to change the welcome screen theme from the command line, right?  Either that, or to simply go back to the automatic login would satisfy me.  Any tips are appreciated.

If this post is in the wrong section, please feel free to move it to a more appropriate thread (anyone with the power to do so, that is...)

---

