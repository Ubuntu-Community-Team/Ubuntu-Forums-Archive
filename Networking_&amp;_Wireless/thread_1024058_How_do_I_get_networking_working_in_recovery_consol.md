---
title: "How do I get networking working in recovery console?"
date: 2008-12-28
forum: Networking &amp; Wireless
---

### Post by jakev383 on 2008-12-28
My machine died.:( I've got the drives in a new machine, and can boot into the recovery console.  How do I get networking working in the recovery console? I've tried 'ifconfig eth0 up' but I get a "eth0: ERROR while getting interface flags: No such device" error when I do that. I tried adding eth0 to the /etc/network/interfaces and booting back into the recovery console, but that also does not work....
Any help appreciated!

---

### Post by kevdog on 2008-12-28
Sounds like you are doing the right things.  When you are in recovery mode and you do a ifconfig, does any interface show up as working?

I assume you are working with a cabled connection.  Have you typed dmesg at the command line just to make sure that eth0 is up and active?  dmesg gives you a glimpse of the system log file.

---

### Post by jakev383 on 2008-12-28
I ended up disabling X11 and gdm (which was causing it to lock up when trying to boot normal) and got it to boot into the full system with the new NIC showing. I never could get either the onboard NIC or the extra one I plugged in to show in recovery.  Only thing that showed in recovery was lo, for obvious reasons.
I'm moving my data now, so I'll call it good for the night.
Thanks for the reply

---

