---
title: "how can I allow my lan traffic into ubuntu?"
date: 2013-01-07
forum: Networking &amp; Wireless
---

### Post by sdowney717 on 2013-01-07
Right now some traffic is being blocked on the lan which runs thru my ubuntu pc.


I want to let it all in, everything.
firestarter was able to do it just once, but it has serious bug.
[https://bugs.launchpad.net/ubuntu/+source/firestarter/+bug/43784](https://bugs.launchpad.net/ubuntu/+source/firestarter/+bug/43784)

---

### Post by sdowney717 on 2013-01-07
I turned off gufw.
Even doing this allow command did not work.??

[http://serverfault.com/questions/74023/ufw-on-ubuntu-to-allow-all-traffic-on-lan](http://serverfault.com/questions/74023/ufw-on-ubuntu-to-allow-all-traffic-on-lan)

I then reinstalled firestarter
And it works, I can have lan traffic again coming in.

Likely I will have to uninstall and reinstall on every boot to make it work.

Or is trying the bug link fix something worth doing or will it brake something else even worse.?

---

### Post by oldos2er on 2013-01-07
Moved to Networking & Wireless.

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

