---
title: "Computer loses network connection"
date: 2012-04-27
forum: Networking &amp; Wireless
---

### Post by rozo on 2012-04-27
Hello,

I have a really critical problem with 2 systems that work as servers (we have our own server application on them that continously transfer data to a client) and are 500 km away from me. The problem is they lose network connection about once in a week (not both at once, sometimes only one) and they have to be rebooted many! times before they can be accessed again. In a system log from reboot I have:
Apr 24 10:58:14 cam1-desktop kernel: [   13.115602] ADDRCONF(NETDEV_UP): eth1: link is not ready 
I have some questions, I hope they can be answered:
- is it only hardware problem or can it be also software that somehow makes the network connection disable/crash/... (I mean our application, not doing ifconfig)?
- is there a way to fix it automatically on the system, for e.g. by starting a script each 1-2 minutes that does ifconfig?
- can I find something else in the system logs, what should I search for?
- do you have any ideas what can be the reason and how can I solve it?

---

### Post by KevinDoyleIE on 2012-04-27
Sorry to hijack you thread but I've upgraded to 12.04 this morning and now my machine won't connect to the network.
My eth0 set up looks the same as it was before.

Any help on how to get the connection fixed would be greatly appreciated.

---

