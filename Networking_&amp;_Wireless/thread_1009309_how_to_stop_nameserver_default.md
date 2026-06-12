---
title: "how to stop nameserver default"
date: 2008-12-12
forum: Networking &amp; Wireless
---

### Post by smd1280 on 2008-12-12
Hi I'm new to to ubunutu.  

I have installed ubunutu 8.10 i386

I need my dns servers to be permanently set to the following: 

I have edited my resolv.conf as follows

nameserver 4.2.2.2
nameserver 4.2.2.1


Everything works as expected after saving. However if I do a reboot it changes back to 

nameserver 192.168.1.1  

I need nameserver to stay at 4.2.2.2 & 4.2.2.1

I have tried adding some lines to dhcp3 according to bsd sites to no avail.  If somebody could help me resolv this issue I would greatly appreciate it.

---

### Post by smd1280 on 2008-12-13
bump my own thread,  I've tried the googling more today and can not seem to find the answer I am seeking.

---

### Post by Iowan on 2008-12-13
You can add servers via the **prepend** line in /etc/dhcp3/dhclient.conf.

---

### Post by smd1280 on 2008-12-13
Thank you looks like editing dhclient.conf did what I needed it to do.

---

