---
title: "Does ubuntu come with a firewall program by default???"
date: 2009-01-23
forum: Networking &amp; Wireless
---

### Post by philidox on 2009-01-23
Im trying to run a game that needs access to the internet and I need to rule out if a firewall is blocking t.  I need to know if ubuntu comes with a firewall by default.  I don't think I installed a firewall myself.  I looked at the system monitor and didn't see anything that looked liked a firewall.

---

### Post by DFord425 on 2009-01-23
yes it comes with a firewall, iptables. But the firewall is set to allow everything by default.

---

### Post by philidox on 2009-01-23
> **DFord425 said:**
> yes it comes with a firewall, iptables. But the firewall is set to allow everything by default.

How do you access it, and/or turn it off?

---

### Post by DFord425 on 2009-01-23
Im not sure if you can turn it off. But, unless you have changed any settings in it, it is set to allow everything. So unless you added some rules to iptables, its not blocking the game from the internet.

---

### Post by philidox on 2009-01-23
Ok thx

---

### Post by hyper_ch on 2009-01-23
it's integrated into the kernel, so turning it really off would require to recompile the kernel...

By default it lets everything pass (has no filtering rules setup) and that's good :)

---

### Post by philidox on 2009-01-23
how do you mark this thing as solved

---

### Post by hyper_ch on 2009-01-23
not sure if it's enabled again. But if it is, have a look at the "Thread Tools" drop down menu at the top.

---

