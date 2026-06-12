---
title: "Passwordless SCP?"
date: 2009-09-21
forum: Networking &amp; Wireless
---

### Post by ownaginatious on 2009-09-21
Well, I recently acquired a Linksys wrt54gl router and installed DD-WRT firmware on it. I figured out how to make the router save information regarding how much traffic each person on the network has been using and I would like the routers built in cron to automatically send me a file containing this information through SCP everyday.

Now the problem I'm having is that when using ssh from the router, it cannot enter a password nor can it retrieve an identity file off the router's disk (everything is saved in NV_RAM, so anything I save on the disk is gone on reboot).

So what I'm wondering is, can I setup my desktop computer to allow a certain file (i.e. less than a certain size and with a certain name) to be received from an "anonymous" source without a password?

Thanks,

Dillon

P.S. If anyone can think of a better solution to my problem, that's always welcome too :p

---

### Post by scorp123 on 2009-09-21
You need SSH keys.

[http://www.debian-administration.org/articles/152](http://www.debian-administration.org/articles/152)

---

### Post by ownaginatious on 2009-09-21
I don't think that will work since the router is unable to save anything to its disk between reboots. It also doesn't have the appropriate tools for making keys installed.

---

### Post by badger_fruit on 2009-09-21
> **ownaginatious said:**
> I don't think that will work since the router is unable to save anything to its disk between reboots. It also doesn't have the appropriate tools for making keys installed.

scorp123 is right, ssh keys are the only way but if the router looses information on each reboot then you're stuffed AFAIK; "consult the user guide of the manual or email the manufacturer" would be the only other thing I could suggest here.

---

### Post by ownaginatious on 2009-09-21
> **badger_fruit said:**
> scorp123 is right, ssh keys are the only way but if the router looses information on each reboot then you're stuffed AFAIK; "consult the user guide of the manual or email the manufacturer" would be the only other thing I could suggest here.

Ya, I'm asking on the DD-WRT forums now for help. Hopefully someone there has a solution to my problem.

Thanks anyway though guys.

---

