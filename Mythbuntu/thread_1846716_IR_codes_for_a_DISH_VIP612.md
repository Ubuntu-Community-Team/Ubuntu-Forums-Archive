---
title: "IR codes for a DISH VIP612"
date: 2011-09-19
forum: Mythbuntu
---

### Post by romanyiv on 2011-09-19
Been trying to get my STB working via MCE USB interface.   The IR transmitter flashes - but so far my box is not seeing it.  The LIRC setup has DISH selected - I'm doing the IRSEND -d /etc/lircd command from CLI to test with (I'm at work - don't recall the exact syntac at the moment).   Does the 612 use some other kind of codes?

---

### Post by azmyth on 2011-09-21
Did you see this thread. May want to try those codes.

[http://www.mythtv.org/pipermail/mythtv-users/2011-January/306934.html](http://www.mythtv.org/pipermail/mythtv-users/2011-January/306934.html)

Also, do you have a frequency set in your lirc.conf file. You may need this per the other thread. I'm using a different STB but I needed this as well as it wouldn't change without it.

frequency    40000

---

