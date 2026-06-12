---
title: "All ports are closed, although router has them forwarded"
date: 2009-02-05
forum: Networking &amp; Wireless
---

### Post by kabbage on 2009-02-05
Hey.

I'm running Ubuntu 8.10, connected directly to a Rotal RTA 1025W router.
I'm having problems downloading using BitTorrent clients, because ports seem to be closed even after I've had my router forward them to my machine's IP.
Ufw is disabled.

I'm dual-booting with Windows, and these issues don't exist there.

What gives?
Thanks.

---

### Post by hyper_ch on 2009-02-06
do you have torrent program runnning? what port is it listening to? do you have that port forwarded from the router? Are multiple ports involved?

---

### Post by Another Monkey on 2009-02-06
If your router is similar to mine, it will only forward to a fixed IP.  Is your Ubuntu session using the same IP as the Windows one?  If not, that could be your problem.  So you might want to use a different port for the Ubuntu session and have that port forwarded to its IP.

The website [PortForward ]("http://portforward.com/")has very clear guides and helped me when I was trying to set mine up.

---

### Post by superprash2003 on 2009-02-06
post output of sudo iptables -L .. you could try flushing your iptables [http://www.prash-babu.com/2008/10/how-to-flush-or-remove-all-iptables.html](http://www.prash-babu.com/2008/10/how-to-flush-or-remove-all-iptables.html) .. have you tried this online port scanner [http://www.t1shopper.com/tools/port-scanner/](http://www.t1shopper.com/tools/port-scanner/)

---

### Post by kabbage on 2009-02-07
Shortly after posting this I deleted the config dirs in my home directory (.config, .gconf, .gnome). After a reboot, the ports were open.

Thank you all for your help. :)

---

