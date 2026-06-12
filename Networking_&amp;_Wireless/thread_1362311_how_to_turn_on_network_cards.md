---
title: "how to turn on network cards?"
date: 2009-12-23
forum: Networking &amp; Wireless
---

### Post by sggin on 2009-12-23
hi,
fresh install studio 9.10, I have 2 network cards and was unable to get dhcp working on the install, how do i get permissions so i can use cmds w/ ifconfig, it will not let me turn the cards on, the auto eth0 doesnt work, the gui program doesn't do anything but recognize the cards.
 
thanks

---

### Post by Iowan on 2009-12-23
I haven't used Studio, so hopefully I won't misinform you...
**sudo** should help with the permissions.

---

### Post by sggin on 2009-12-23
i was hoping to get this goin but in my case it fells like linux 10 yrs ago, almost there but just can't do it. 

 i just hate goin back to windows cause a crappy eth0 card can't grab a dhcp address.

thanks for the help

---

### Post by Iowan on 2009-12-23
A couple of things to try (if you don't mind the command line):
Post results of **lshw -C network** and **ifconfig -a**. Network Manager generally manages only one interface at a time, but it should be possible to set up the other one via */etc/network/interfaces*. 

I can't guarantee success, but I'm (one of probably several) willing to try to help.

---

