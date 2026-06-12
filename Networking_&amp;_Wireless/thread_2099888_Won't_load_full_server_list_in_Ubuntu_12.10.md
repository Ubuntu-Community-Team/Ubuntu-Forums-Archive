---
title: "Won't load full server list in Ubuntu 12.10"
date: 2012-12-30
forum: Networking &amp; Wireless
---

### Post by cirelosborn on 2012-12-30
I have 5 machines that run ubuntu 12.10 and a router with usb network drives.  They all can see each other over the wifi network except for one vaio netbook.  No computer can see the vaio and the vaio can only see itself and the router.  
I did a fresh install of samba on all computers, checked all workgroup names, and went through dozens of threads.  I've reconfigured the smb.conf global settings on all computers.  Everything worked fine until today and I have no idea what happened.
Any help at all would be appreciated.

---

### Post by 2F4U on 2012-12-31
Some questions that come to my mind:
- Is there a firewall on the Vaio?
- Are messages such as ping blocked on the Vaio?
- Can you ping the IP adresses of the other machines from the Vaio?
- Are all machines in the same network segment?

---

### Post by cirelosborn on 2012-12-31
Thanks for your reply.

- Is there a firewall on the Vaio?
The Vaio has no firewall

- Are messages such as ping blocked on the Vaio?
No

- Can you ping the IP adresses of the other machines from the Vaio?
Vaio can't ping any machine, error "unreachable"

- Are all machines in the same network segment?
After looking, all my machines are on the same segment except the vaio which doesn't show a ip under ifconfig

So, why did my vaio lose it's ip? and, how do I get it back?

---

### Post by rnerwein on 2012-12-31
> **cirelosborn said:**
> Thanks for your reply.

- Is there a firewall on the Vaio?
The Vaio has no firewall

- Are messages such as ping blocked on the Vaio?
No

- Can you ping the IP adresses of the other machines from the Vaio?
Vaio can't ping any machine, error "unreachable"

- Are all machines in the same network segment?
After looking, all my machines are on the same segment except the vaio which doesn't show a ip under ifconfig

So, why did my vaio lose it's ip? and, how do I get it back?
hi
how does other boxes can ping the vaio when ifconfig shows no ip. may be it's
possible to post a ifconfig of the vaio and of a other box.
same with route.
cheers

---

### Post by cirelosborn on 2012-12-31
Removed

---

### Post by cirelosborn on 2012-12-31
Problem solved.  I auto connected to a supplemental network and never realized it.  I'm sorry for wasting your time.

---

