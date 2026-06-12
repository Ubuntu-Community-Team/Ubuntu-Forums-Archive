---
title: "Accepting ssh connections"
date: 2009-04-24
forum: Networking &amp; Wireless
---

### Post by ufarmer on 2009-04-24
I am running Ubuntu 9.04 on my laptop and Debian 4.0 on my desktop (soon to be upgraded to Ubuntu).  I have ssh installed on both machines and the ssh agent is running on both machines.  However, when I try to ssh from one to the other (it doesn't matter which) I get an error message saying the connection was refused.  I checked and my router is not blocking port 22 (or any other ports) and I do not have a firewall (that I am aware of) on either machine.  I have googled the problem but I am already doing, or have already installed, every solution that I found.

Any advice is appreciated.

---

### Post by dox_drum on 2009-04-24
I've a very similar doubt.

At the university, since the machines have a fixed IP the ssh protocol works perfectly. However, at home I have a wireless router, and a couples of laptops (running Jaunty and OpenSUSE). Is it possible to use ssh and sftp protocols to backup ones file into the other HD?

Thanks for any help!

[CENTER]Enjoy![/CENTER]

---

### Post by JK3mp on 2009-04-25
> **dox_drum said:**
> I've a very similar doubt.

At the university, since the machines have a fixed IP the ssh protocol works perfectly. However, at home I have a wireless router, and a couples of laptops (running Jaunty and OpenSUSE). Is it possible to use ssh and sftp protocols to backup ones file into the other HD?

Thanks for any help!

[CENTER]Enjoy![/CENTER]

I believe you can configure most routers to assign a static IP to a machine. Just do so and then switch it back up to dhcp whenever you wish.  A pain.. but works.

---

### Post by dox_drum on 2009-04-25
> **JK3mp said:**
> I believe you can configure most routers to assign a static IP to a machine. Just do so and then switch it back up to dhcp whenever you wish.  A pain.. but works.

Thanks man! I'll try it right now.

---

### Post by ufarmer on 2009-04-25
But, even if the IP address has been assigned dynamically, the computer still has an IP address.  I am using the correct, current IP addresses of both of my computers so it seems that ssh should work.

---

