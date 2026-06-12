---
title: "wireless issue"
date: 2009-12-06
forum: Networking &amp; Wireless
---

### Post by Baconfatty on 2009-12-06
I was trying to install wireless drivers, (which I have to do for every new install of ubuntu) however this time, the power flickered and the computer shut off in the middle of installing.  Now both of the available wont install.  I get this message when I try.

"Sorry, installation of this driver failed.

Please have a look at the log file for details :/var/log/jockey.log"

I've looked over this log file.  I can post the whole thing if needed but the two entrys that caught my eye.

"2009-12-06 01:04:54,580 WARNING: /sys/module/wl/drivers does not exist, cannot rebind wl driver
2009-12-06 01:04:54,612 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted"

Anyone know how to fix this?

---

### Post by diablomarcus on 2009-12-12
I am having the same issue.

---

### Post by redlinethecar on 2009-12-29
Well i hope someone can figure this one out ive been looking and looking,  If i find something will be sure to update.

---

### Post by adam814 on 2009-12-29
Hmm...I wonder why those modules are blacklisted.  Maybe the rest of the log gives a hint.  You might try commenting out the entries that match those module names in /etc/modprobe.d/blacklist.conf (although then again they might be blacklisted for a reason, I haven't seen the whole log yet).

Have you tried this?
```
sudo modprobe bcm43xx
```
After that running dmesg would tell if there was an error loading the module.

---

