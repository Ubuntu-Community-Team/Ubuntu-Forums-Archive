---
title: "DHCP cant start anymore after I installed firestarter"
date: 2013-01-07
forum: Networking &amp; Wireless
---

### Post by sdowney717 on 2013-01-07
It actually was all working for a few minutes.
Now it is busted.
I have 2 nics.
And I am kind of tired about this problem after working on it for days.

What is wrong with DHCP on eth0?
eth0 is sharing the connection to other computer.

DO I need to uninstall firestarter and reboot?

---

### Post by sdowney717 on 2013-01-07
Must be one of those will never fix bugs, see here from 2006
[https://bugs.launchpad.net/ubuntu/+source/firestarter/+bug/43784](https://bugs.launchpad.net/ubuntu/+source/firestarter/+bug/43784)

I uninstalled and rebooted and the lan is back to where it was, only half broken.

I tried gufw firewall, but that did nothing or it is too complex for me to figure out.
Firestarter worked only the one time. Turning it off and on killed everything.

Is there some other firewall to use? Or how can I configure gufw to allow samba sharing. I tried their preset but not working.

---

### Post by sdowney717 on 2013-01-08
Solved by installing webmin!!

I did get a certificate warning, log in anyway!

after you log in to webmin then on left side click
Networking then Linux firewall.

I got a message saying 2 rules had been entered that webmin could not deal with, so saved current iptables to a file.

The I reset the firewall.
And it worked, I can browse shared folders on all the computers. On first win7 pc, I have to map network drive since it is in a different subnet.

The webmin shows a very nice gui to the firewall configuration!


[IMG]https://lh4.googleusercontent.com/-JLN674cmEuc/UOx_lsKNoNI/AAAAAAAAEXo/GtGZ8LHzexA/s1440/fixedfirewall.png[/IMG]

---

