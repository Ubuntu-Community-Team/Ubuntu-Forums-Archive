---
title: "ndiswrapper only works when I load and unload the native drivers first"
date: 2010-01-05
forum: Networking &amp; Wireless
---

### Post by mbabauer on 2010-01-05
I recently received a used laptop that I was going to use for my kids, a Compaq Presario 2100.  Everything went fine on the install, however I could not get the WiFi to work.  The internal card, a Broadcom BCM4306, was attempting to use the b43legacy drivers, which I understand to be the native driver for this card, but would get all sorts of strange errors in 'dmesg', and would never get a solid connection.

After fiddling with this for 2 days, and reading countless troubleshooting guides, I finally gave up and decided to get it working with ndiswrapper.  Everything worked perfect, except I can only get it to work if I first load b43legacy, then load ndiswrapper, then unload b43legacy.  If I blacklist b43legacy, and just load ndiswrapper, iwconfig does not report a wlan0.

I ran across [this posting]("http://ubuntuforums.org/showthread.php?t=1042621"), and decided to try this, but it also did not work.  Plus, with this file in place, any attempt to use modprobe would complain about every line of that file.

I am not sure what to do now.  Can anyone help me get this blasted WiFi working?

---

### Post by mbabauer on 2010-01-06
Bump

---

### Post by mbabauer on 2010-01-10
Bump....

Still haven't figured out how to get ndis to work...

---

### Post by mbabauer on 2010-01-13
Bumpity bump bump....

Still no solution to this.  Is there no one that can explain why the ndiswrapper only works if I load the b43legacy drivers first and remove them?

---

