---
title: "Vmware &amp; Firewall confusion."
date: 2009-04-08
forum: Networking &amp; Wireless
---

### Post by timZZ on 2009-04-08
Hi,

I am curious.  I realise this isn't a vmware forum but I wanted to send a question out.

I have my host (server running vmware) running 2 vms as guests (one of them being XP)

Would the firewall on the host protect my vms? being that even through they are 'bridged'. Firewalls don't work on IPs as such but on ports?

So turning off my XP firewall is safe?

---

### Post by Spider7 on 2009-04-09
For bridged networking, the packets to guest OS should be diverted before hitting the host firewall. So guests would need their own firewall.

---

### Post by timZZ on 2009-04-09
Thank you Spider7.

That's what I needed to know.

---

