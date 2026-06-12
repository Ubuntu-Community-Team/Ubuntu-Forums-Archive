---
title: "bluetooth refuses to stay turned off"
date: 2010-08-24
forum: Networking &amp; Wireless
---

### Post by v1nsai on 2010-08-24
I was wondering if anyone knew of a way to keep my bluetooth from turning back on every time I resume from suspend or restart.  It doesn't seem to be playing very nicely with the gnome-bluetooth manager, because I'm not seeing an icon for it in notifications area like I did in karmic (now using lucid).  

Are there any scripts that are run with root privileges on boot/resume that I could just add "/etc/init.d/bluetooth stop" to?

---

### Post by utnubuuser on 2010-08-24
Maybe startup applications...

System>>Preferences>>Startup Applications

---

### Post by Blackbird_13 on 2010-08-24
Try this:

Install boot-up manager ("bum"). It will show a list of services - you can untick Bluetooth services ...

---

