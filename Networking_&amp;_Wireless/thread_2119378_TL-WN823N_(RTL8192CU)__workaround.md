---
title: "TL-WN823N (RTL8192CU)  workaround"
date: 2013-02-23
forum: Networking &amp; Wireless
---

### Post by ecowan on 2013-02-23
Just so it's easier to find in case someone else is struggling...

I'm using it with Ubuntu 12.19.

sudo modprobe -r rtl8192cu
sudo modprobe rtl8192cu swenc=1

Now it works like a charm.
What does swenc=1 do?
Now to figure out how to make it part of the normal startup process.
Thanks, 'Wild Man'.

Post script:
Actually, swenc=1 worked for a few days. But then something changed (a system update?) and nothing seemed to work. The proper solution turned out to be
1. Add 'blacklist rtl8192cu' in /etc/modprobe.d/blacklist.conf
2. Install the Linux drivers found I found at [www.realtek.com](www.realtek.com)
Installation ('sudo bash install.sh') wasn't so scary as I feared, and now my TP-Link really does work like a charm.

---

### Post by ahallubuntu on 2013-02-23
~

---

### Post by ecowan on 2013-02-23
Yes, I did mean 12.10.

I forgot to say that I also used ndiswrapper to load the net8192cu.inf etc files that came on the CDs with the dongle (Windows XP version - the others wouldn't work)

The ndiswrapper gui dialogue complains that it can't find ndiswrapper, but it seems the driver gets installed nevertheless.

Thanks for the tip on how to make the modprobe permanent.

- Erny

---

### Post by ahallubuntu on 2013-02-23
~

---

### Post by mikewhatever on 2013-02-23
> **ahallubuntu said:**
> No luck for me.  I tried the swenc=1 option in Ubuntu 12.04.2 with the built-in driver and it was still unable to connect.  But, building the RTL8192CU driver from Realtek (which I've now done a dozen times or more on different installs) is quick and effective; tried it again just now, connected immediately.
Same here. Using the swenc=1 option made no difference. The driver from realtek.com works well on 12.04, that's probably why that bug has not been fixed. However, it is officially released for 3.0.8 and earlier kernel, and building it on Raring, 3.8 kernel, fails.

---

### Post by davidbaumann on 2013-04-18
Same problem here. Any news?

---

### Post by ahallubuntu on 2013-04-18
~

---

### Post by bradgy on 2013-04-25
Same problem here (can't compile the realtek driver in Raring 13.04). I've emailed realtek to see if they have plans to ensure compatibility with the linux 3.8 kernel. Hopefully something happens soon because it's not much fun having internet capped at 30 KB/s.

---

### Post by ivlivs on 2013-04-27
+1

---

### Post by ahallubuntu on 2013-04-27
~

---

