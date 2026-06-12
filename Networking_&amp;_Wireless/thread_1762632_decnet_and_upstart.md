---
title: "decnet and upstart"
date: 2011-05-19
forum: Networking &amp; Wireless
---

### Post by bnilsson on 2011-05-19
Hi!

I am trying to get decnet to work since it broke for me 10.04 -> 10.10.
I suspect it has something to do with upstart, since decnet the docs says it is required to be started BEFORE the tcpip networking. I currently have no control over this.

The startup script for decnet is /etc/init.d/decnet.

How do I make sure it is started before the tcpip networking?

I am not familiar with upstart, so I would need some help.



(The problem I have with decnet is:
root@ubuntu:# /etc/init.d/decnet start
Starting DECnet...RTNETLINK answers: Device or resource busy
done.
root@ubuntu:# dnlogin fyvax7
Cannot connect to fyvax7: Rejected by object)

---

### Post by bnilsson on 2011-06-17
I managed to get decnet working by

bnilsson@ubuntu:~$ sudo ifconfig eth0 down
bnilsson@ubuntu:~$ setether 57.5 eth0

Now I can access my old VAX computer:

bnilsson@ubuntu:~$ dnlogin 57.342

    Welcome to VAX/VMS V5.5-2H4 on node FYVAX7

Username: 




So I was right, it was the startup order.

Again, how can I make sure that the decnet startup procedure is performed before the tcpip? Is it not ANYBODY out there who knows?
Really, this is not a decnet question, it its about upstart!

---

### Post by Cheesehead on 2011-06-17
Take a look at /etc/init/ for the upstart confs.
Look at the start-on criteria, and see what looks promising.

For example, if you have Network Manager installed, you can simply add the setether command before the NM command in the listener.

If you don't have NM installed, then see what other network-related .confs you do have, and what they are listening for.

There are two types of events that Upstart listeners can use. One is an **emitted signal** (sudo initctl emit signalname) like local-filesystems or net-device-up. the second is Upstart's **service tracking** like 'dbus started' or 'dbus stopping'.

---

