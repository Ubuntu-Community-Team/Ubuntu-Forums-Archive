---
title: "Opening Media Sometimes Crashes 8.04 to Login"
date: 2008-05-28
forum: Multimedia Software
---

### Post by Scyron on 2008-05-28
Since I installed 8.04 (first by upgrade, then by clean overwrite) I've had trouble with session crashes when opening media. It happens I "switch" formats of media within a session. For example, if watch an H2.64 video and then, after closing, open an MP3, a crash might occur. Switching between same-container videos (MKV, AVI, etc) with different codec needs also occasionally leads to a crash. This is regardless of player (I use VLC and SMPlayer primarily), and whenever I experience a crash, I get a one-second flash of a GRUB screen that appears to say this:

```
* Starting anac(h)ronistic cron anacron
* Starting deferred execution scheduler atd [ok]
* Starting periodic command scheduler crond [ok]
* Checking battery state... [ok]
* Running local boot Scripts (/etc/rc.local) [ok]
```

And then I'm back to the login screen. I don't think my hardware is a problem, as it's worked fine on everything in 7.04 and 7.10. Does anyone have any ideas?

---

### Post by Scyron on 2008-05-29
Huge Update: It appears as if when this happens, my old session DOESN't crash. A new one is merely started. Once when an audio file sent me to the login screen, the song continued playing even when I re-logged in. I looked in my System Monitor, and a number of system functions were running multiple times according to how many times I'd crashed since startup. For example, I had 5 trackid's, 5 gvfsd's 6 dbus-daemon's, and 6 gnome-vfs-daemon's.

Does anyone know who this is possible?

---

### Post by rare HERO on 2008-11-18
I had a similar problem so I removed anacron.

via Synaptic Package Manager:
[INDENT]cron-like program that doesn't go by time 
Anacron (like `anac(h)ronistic') is a periodic command scheduler.  It
executes commands at intervals specified in days.  Unlike cron, it
does not assume that the system is running continuously.  It can
therefore be used to control the execution of daily, weekly and
monthly jobs (or anything with a period of n days), on systems that
don't run 24 hours a day.  When installed and configured properly,
Anacron will make sure that the commands are run at the specified
intervals as closely as machine-uptime permits.

This package is pre-configured to execute the daily jobs of the Debian
system. You should install this program if your system isn't powered on
24 hours a day to make sure the maintenance jobs of other Debian packages
are executed each day.
[/INDENT]
For some reason this kept killing gnome, and I couldn't use my computer (because I need GUI). So I removed Anacron by typing the following into terminal
```
$ sudo apt-get remove anacron
```

If someone knows what anacron is good for, let me know.

---

