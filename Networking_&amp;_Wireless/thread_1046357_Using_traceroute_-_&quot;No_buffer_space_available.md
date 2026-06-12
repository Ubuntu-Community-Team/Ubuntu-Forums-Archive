---
title: "Using traceroute - &quot;No buffer space available&quot;"
date: 2009-01-21
forum: Networking &amp; Wireless
---

### Post by basil_croutons on 2009-01-21
Hi, can anyone help?

I'm trying to test my mobile broadband connection and keep getting the following readout :

traceroute to bbc.co.uk <212.58.224.138>, 30 hops max, 40 byte packets
send: No buffer space available

I can ping ok, I'm wondering if my problem is with the modem, or with my machine/OS setup. I don't have a wired broadband connection available here, so I don't know if I'd get the same problem then too.  

My system is :
Xubuntu 8.04 (hardy)

hp pavillion ze4801ea laptop
mobile AMD athlon XP2500+
439MB ram, lots of disk space

huawei E160G mbb on the 3 network, connecting via GnomePPP

cheers
bc

---

### Post by jonobr on 2009-01-21
HEllo

You should take a look at the launch pad, this has beenr reported before in a few places,
check out this link

[https://bugs.launchpad.net/ubuntu/+source/traceroute/+bug/290145](https://bugs.launchpad.net/ubuntu/+source/traceroute/+bug/290145)

---

### Post by basil_croutons on 2009-01-21
Thanks for that, Jonobr,

Working like a dream! And now I know about the launchpad.... so much new stuff to get lost in.....

Thanks again

bc

---

### Post by jonobr on 2009-01-21
Tee hee.........
If your having trouble sleeping at night, launchpad is the right place:-)
REcommend you mark this thread solved.


Cheers and good luck

---

### Post by kcode on 2009-12-29
Hi,
I am having this same problem on ubuntu 8.04. But the above link provided appears to be broken. Moreover, I haven't updated the computer since long time. If bug can be fixed by an update then please specify it, as I'm right now not in a position to go for a system update. 

thanks

---

### Post by GregIthaca on 2010-01-05
Only affects people who are going out through PPP interface, from what I have seen.
Add "-N 7" before the host you are trying to reach as a workaround.
It is a bug in the package, affecting multiple distros, and no sign that it has been fixed in 8.04.x from what I saw on Launchpad.

---

### Post by amoun on 2010-03-30
As there is no update for traceroute in my 8.04 I removed it completely and installed tcptraceroute via the packet manager.

All is now ok

---

