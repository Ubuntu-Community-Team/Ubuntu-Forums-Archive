---
title: "ubuntu 9.10 unstable network connection"
date: 2010-03-06
forum: Networking &amp; Wireless
---

### Post by golden_eye_ on 2010-03-06
Hello all ... 
I am using a PPPoE connection ...
My network connection is really unstable in ubuntu but it works fine with XP.

i have added this  lines in dsl-provider:

> 
pty "/usr/sbin/pppoe -I eth0 -T 80 -m 1452"
pty "/usr/sbin/pppoe -S 'big' -C 'UTC-2'"


here big is my service providers name.
it connects sometimes ,,,
though it shows the "plog" output correctly.....
trys to load a page for a long time ... and after that just stops

what can i do??
Thanks in advance.

---

