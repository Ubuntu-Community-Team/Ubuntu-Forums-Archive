---
title: "Networking problems, SVN and SSH connections broken."
date: 2012-02-22
forum: Networking &amp; Wireless
---

### Post by ka2rvo on 2012-02-22
I've been scouring Google for weeks with this and so far, lots of information, but no resolution.

When connecting to my Ubuntu 11.04 system from Windows via Putty or WinSCP, the connection freezes and drops after about 30 seconds. Most commonly, I see "Software caused connection abort."

Another problem I see, from a terminal window, doing an "svn update" frequently hangs after a few seconds.

This problem has come and gone, sometimes I'm good for a week, then it's broken for a few weeks.

Here is what works, Firefox. I can sit at this computer all day and surf the web without problems. The upgrade manager never fails me. Apt-get never has a problem.

This is a fairly clean system with very little on it beyond a stock install.

Our IT guys gave me a static IP address, thinking that might solve the problem, it didn't. Suspecting a conflict, I will try to ping the address a couple times a day when my system is turned off, nothing.

I occasionally dual-boot to Windows and networking always works fine there.

Anyone have some suggestions?

---

### Post by collisionystm on 2012-02-22
Do you have ufw or another firewall enabled?

---

### Post by ka2rvo on 2012-02-24
Nope, not the firewall.

---

