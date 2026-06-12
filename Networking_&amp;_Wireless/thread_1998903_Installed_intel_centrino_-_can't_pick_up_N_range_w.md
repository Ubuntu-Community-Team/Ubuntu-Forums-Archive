---
title: "Installed intel centrino - can't pick up N range wireless"
date: 2012-06-07
forum: Networking &amp; Wireless
---

### Post by rurodrig on 2012-06-07
I'm using Ubuntu 12.04 on a Dell Vostro.  The old wireless card could not pick up my N network, so I installed an Intel Centrino N1000 card, which is supposed to pick up N.  It picked up G out of the box, but doesn't see the N though.  Any one have any ideas?

---

### Post by chili555 on 2012-06-07
Yes, the Intel cards are notorious for not doing N speeds at all. Search this forum for 11n_disable and you'll see dozens of examples.

---

### Post by rurodrig on 2012-06-07
Thanks for the 11n-disable tip.  That helped me zone in on other forums with similar issues.  

I tried setting 11n_disable to 0, and 1 by following the instructions here: [http://ubuntuforums.org/showthread.php?p=11993562](http://ubuntuforums.org/showthread.php?p=11993562)

None of that worked.  Are you thinking it's a hardware issue?  It picks up B/G just fine.

---

### Post by chili555 on 2012-06-07
It should be set to 11n_disable=1. Did you unload and reload the driver afterwards? Reboot?

It's not going to do N in the foreseeable future until Intel fixes the driver. Sorry.

---

### Post by rurodrig on 2012-06-07
> **chili555 said:**
> It should be set to 11n_disable=1. Did you unload and reload the driver afterwards? Reboot?

It's not going to do N in the foreseeable future until Intel fixes the driver. Sorry.

How do I unload and reload?  I did the reboot.

---

### Post by chili555 on 2012-06-07
> I did the reboot.Then you're all set. I'm sorry, I know of no way currently to get Intel Centrino chipsets to do N speeds.

---

### Post by rurodrig on 2012-06-07
> **chili555 said:**
> Then you're all set. I'm sorry, I know of no way currently to get Intel Centrino chipsets to do N speeds.

Oh well.  I'll stay slower.  Thanks for your help though.

---

