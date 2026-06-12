---
title: "Network config changes at random"
date: 2009-01-15
forum: Networking &amp; Wireless
---

### Post by sand0z on 2009-01-15
I'm using 8.10 desktop and have 2 users, one the first default user and another set up by me. The second user has limited privileges, but does not get a network connection even though it's allowed under Account Properties -> User Privileges. I tried check and unchecking the box, but can't seem get the network icon to appear when the user logs in. This worked fine for the last few days and being new, I haven't made any changes outside of the GUI tools. Also, I use static addresses for this host, but if still searches for a DHCP server on bootup. As a result, I've had to disable my DHCP server on the home network. 

I hope that someone can help me with this. Thanks in advance

---

### Post by superprash2003 on 2009-01-15
post output of cat /etc/network/interfaces .. you could try entering your ip information in the interfaces file manually.

---

### Post by sand0z on 2009-01-15
There isn't much to see here.

itoc@Ubuntu810desktop:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

I did go back to User Preferences for that account and checked and unchecked the network box a few times and the system seems to be stable. However, after a reboot, I noticed that my GUI network config shows eth0 and eth1 in auto, with another eth0 set up with a static. I deleted those auto interfaces, but they insist on reappearing. 

Thanks for the response. I may post here again as I get this box set up for live use.

---

