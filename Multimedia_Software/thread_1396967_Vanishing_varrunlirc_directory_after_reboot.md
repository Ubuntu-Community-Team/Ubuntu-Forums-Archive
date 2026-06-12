---
title: "Vanishing /var/run/lirc directory after reboot"
date: 2010-02-02
forum: Multimedia Software
---

### Post by ffonz on 2010-02-02
Hi,

I managed to get lirc working on my system. First  I couldn't get it working with the standard lirc packages from ubuntu. So I removed the lirc package with synaptic, downloaded the sources from lirc.org and installed it as described over there (my hardware is described on their site).
When I ran irw I got sane values!

But after a reboot irw didn't work anymore.
When I tried
"sudo lircd -d /dev/lirc0"
I got the response
"lircd: can't open or create /var/run/lirc/lircd.pid
lircd: No such file or directory"
When I create the directory with "sudo mkdir /var/run/lirc" everything is OK again...
... until the next reboot. Then the problems start all over again.

I tried the solution here ([http://www.accentual.com/freemote/forum/viewtopic.php?f=3&t=4&start=10](http://www.accentual.com/freemote/forum/viewtopic.php?f=3&t=4&start=10)), but it didn't work for me.

Has anybody have an idea why my lirc directory is removed after every reboot? Or how can I create this dir before lirc is started?

---

