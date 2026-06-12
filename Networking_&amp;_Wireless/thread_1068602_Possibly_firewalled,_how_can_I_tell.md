---
title: "Possibly firewalled, how can I tell?"
date: 2009-02-13
forum: Networking &amp; Wireless
---

### Post by mortalic on 2009-02-13
I for some reason can't get to my ubuntu's VNC connection from work.  I can access my ftp server on it just fine.  I'm wondering if i'm firewalled but am not sure how to tell.  Can someone give me a quick overview on tracking this down?

---

### Post by kevdog on 2009-02-13
I'm assuming your home computer sits behind a router.  Have you forwarded the port?

I would also do a port scan from the work computer using nmap or such tool to confirm that port 5800 or 5900 (or whatever port you are using for vnc) is open.

As far as firewalls,
sudo iptables -L
lists your current ruleset for iptables/netfilter.

---

### Post by mortalic on 2009-02-16
My home computer acts as the firewall/router i'm using firestarter, and yes vnc 5900 is open.  I can get to it from other systems remotely, just not at work.

---

