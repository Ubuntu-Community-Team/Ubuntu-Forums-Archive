---
title: "customising network initialisation at bootup time (lynx)"
date: 2010-10-20
forum: Networking &amp; Wireless
---

### Post by kirol on 2010-10-20
Under 8.04 I had inserted a little script as
/etc/rcS.d/S38_ether_switch in order to customise
the /etc/network/interface file before eth0 got up.
I need this because sometimes I'll start the regular
ubuntu, and sometimes it'll run under windows with
the help of the wonderful colinux. This is not working
anymore since I updgraded to 10.04. Well in a sense it
still does, as I see the correct version of the file is
being activated at boot time, but probably the new
startup system (not sysv anymore) starts the network
before my hook has had a chance to establish an alternate
interface file. Can someone suggest how to adapt the logic?
Note that virtual networking from colinux still works fine,
I just need to "ifdown eth0; ifup eth0" which is cumbersome.

---

### Post by kirol on 2010-11-14
anyone knowledgeable in the newer boot logic with a suggestion ?

---

### Post by uncaspi on 2010-11-14
You can put the commands in /etc/rc.local

---

### Post by kirol on 2010-11-14
> **uncaspi said:**
> You can put the commands in /etc/rc.local
Thanks for your reply. I believe rcS.d/S* (mono-user) is actually executed before rc.local (multi-user). I tried your suggestion anyway. In both cases, by the time I get to login and check /etc/network/interface, it has indeed been overwritten by the correct version. Yet networking does not seem to take this into account. Either the file is now being ignored or (more likely I believe), networking is initialised even earlier by upstart...

---

