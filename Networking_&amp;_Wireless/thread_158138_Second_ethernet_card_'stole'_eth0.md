---
title: "Second ethernet card 'stole' eth0"
date: 2006-04-10
forum: Networking &amp; Wireless
---

### Post by Hypatia2 on 2006-04-10
Howdy,

I recently popped another ethernet card into my 5.10 Ubuntu box. After booting I noticed that the new card is eth0 and my onboard port is now eth1. How can I restore my original configuration with eth0 on the original port? 

I found nothing in the GUI, but I'd be satisfied editing /etc/network/interfaces if necessary.

Hypatia

---

### Post by hw-tph on 2006-04-12
What kernel module does your onboard use? Use a module alias to associate that module name with the eth0 name, and do the same for the PCI card. These are entered in /etc/modprobe.d/aliases.

Example: Say your onboard interface (which you want to be eth0) uses the e100 driver and your PCI card the 8139too driver. You could then add this to the end of /etc/modprobe.d/aliases:
```
alias eth0 e100
alias eth1 8139too
```


Håkan

---

