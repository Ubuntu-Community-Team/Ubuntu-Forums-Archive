---
title: "Kubuntu 8.10 network problem"
date: 2009-04-04
forum: Networking &amp; Wireless
---

### Post by Baiter on 2009-04-04
I just upgraded from Kubuntu 8.07 to 8.10. My internet is from a home ethernet router and old versions just found the connection automatically. But this 8.10 apparently did not, and gives errors 'unknown host' in Konqueror. 
Network settings is 'connect to the internet directly' (default) and inserting the router URL in proxy settings did not help.
I am not a high-tech user (just turn on auto and use it!).
Any ideas?

---

### Post by chili555 on 2009-04-04
Are you connecting to the router by wired or wireless? Let's trubleshoot your connection. Open a terminal and type the following:```
sudo lshw -C network
```Give your password and then post the results here. We'll get it going!

---

### Post by Baiter on 2009-04-04
Hi Chili, 
It is a wired ethernet to a router, the hardware works because other PCs connect to the internet okay.
er....I don't see a command line in 8.10 ! Where do I type the   sudo lshw -C network   code?

):P

---

### Post by CyberMando on 2009-04-04
K->Applications->System->Konsole
Your ethernet should be configure in /etc/network/interfaces. It should show
auto lo eth0
iface lo inet loopback
iface eth0 inet dhcp

---

