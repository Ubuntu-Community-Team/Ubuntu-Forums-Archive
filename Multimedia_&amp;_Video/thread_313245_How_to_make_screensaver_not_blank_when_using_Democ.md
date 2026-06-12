---
title: "How to make screensaver not blank when using Democracy Player?"
date: 2006-12-05
forum: Multimedia &amp; Video
---

### Post by capran on 2006-12-05
I'd like to know how to make the screensaver not blank the screen when using Democracy Player in fullscreen mode.

I checked System/Preferences/Screensaver and I don't see any advanced options, such as "don't blank when application X is running."

The system doesn't blank when I have other media players, like Mplayer or VLC, running.

I'm using my Ubuntu 6.10 system (was previously on kubuntu 6.06, same behavior) as a HTPC so this is important.

---

### Post by capran on 2006-12-13
bump.

Also, after using Automatix to install media codecs, for some reason Democracy 0.9.2 hangs then crashes when trying to play any video. I tried uninstalling it, and using apt to reinstall, but that downgraded to 0.9.0 or something, which isn't as nice as the newer one (can't rename the RSS channels I add that I get from TVrss, and no options for bittorrent port.)

Ideas?

---

### Post by aidanr on 2006-12-13
yeah i also get a crash when trying to play videos with 0.9.2, i posted a link to 0.9.1 [here]("http://www.getdemocracy.com/news/2006/12/democracy-092-for-debian-and-ubuntu-available/#postcomment"), theres a fix for the crash [here]("http://forum.getdemocracy.com/viewtopic.php?id=882"), but i haven't tried it yet

as for the screensaver issue, i'm not sure about that, i also have all powersaving and screensaver options turned off, yet still sometimes the monitor goes into standby after about 10 minutes, it's kinda irregular though, some days it doesn't do it at all and some days it does, i'm not sure whats going on there

---

### Post by capran on 2006-12-15
> **aidanr said:**
> [here]("http://forum.getdemocracy.com/viewtopic.php?id=882"), but i haven't tried it yet


Thanks! That seems to have fixed it! But now I have to rebuild my RSS feeds/channels.

Off topic slightly, does anyone know of any good TV feeds for PBS/TLC/Discovery/History Channel type programs?

---

### Post by aidanr on 2006-12-16
you'll probably find some on tvrss.net, about the problem i was having with the monitor going into standby, i'm not sure if it's the exact same problem as you're having but if it is then i got it fixed by removing the "option dpms" line from the monitor section of /etc/X11/xorg.conf

---

### Post by moon2js on 2007-04-03
> **aidanr said:**
> about the problem i was having with the monitor going into standby, i'm not sure if it's the exact same problem as you're having but if it is then i got it fixed by removing the "option dpms" line from the monitor section of /etc/X11/xorg.conf

Does that disable the monitor *ever* going in standby?

I have the same problem with the screen blanking during democracyplayer fullscreen play. I want the monitor to turn off when idle, but I don't want fullscreen video to count as idle.

Is there a way to do this?

I'm running fluxbox. Does the idle fullscreen blanking kick in in Xfce or Gnome, too?

---

