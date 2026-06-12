---
title: "Internet Connectivity drops after a period of time but virtual OS still can connect!"
date: 2009-12-17
forum: Networking &amp; Wireless
---

### Post by cyberbeast on 2009-12-17
I use ZTE MF626 Mobile Broadband Modem with my Ubuntu 9.10 to access the internet. The modem works out of the box and browsing speeds seem much faster on Ubuntu than on Windows. But sometimes after a period of time, internet stops working! The page doesnt load at all in Firefox.
BUT, when I try to use firefox on Windows XP on VirtualBox at the same time the internet works!
How is it possible that there seems to be no internet connectivity on Ubuntu while there is perfect internet connection on the virtual OS, even though they are basically using the same MODEM and that the virtual OS is actually sharing internet with Ubuntu!!

Please help. thanks in advance. :)

---

### Post by happypup on 2009-12-26
I am having the same problem on both my computers both running karmic its the same for both wifi and eth but our sprint phone tethering works normal.

also things like Synaptic package manager and ubuntu software center, work with the internet with booth wifi and eth0

---

### Post by jjazz on 2010-01-02
Have either of you been able to resolve this? I am having the exact same issue and it is really frustrating. My Mac laptop, windows box, and windows Virtual Box vm can all connect while my ubuntu karmic systems are consistently inconsistent.

I've searched this for the last few weeks and have tried a few things that I've come across for similar symptoms: 
disabling ipv6
removed network-manager
but the problem still persists.

No exceptions in any logs so I really have no idea what could be causing the problem.

---

### Post by cyberbeast on 2010-01-10
I could not find any solutions till date either. Guess I just have to try disconnecting and re-connecting till I get a connection. Urgh! :-x

---

### Post by alexfish on 2010-01-11
hi

the problem lays with getting connection to the secondary server

note this from your log file viewer .. until there is an automated script to trap the connection or none connection to the secondary server then disconnecting and reconnecting manually is the only answer.. it's only two clicks away

---

