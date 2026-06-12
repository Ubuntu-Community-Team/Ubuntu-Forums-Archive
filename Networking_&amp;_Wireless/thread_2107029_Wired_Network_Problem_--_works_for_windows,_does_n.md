---
title: "Wired Network Problem -- works for windows, does not work for any breed of linux"
date: 2013-01-20
forum: Networking &amp; Wireless
---

### Post by locustmotives on 2013-01-20
I have a windows7/ubuntu12.10 install.  Yesterday, everything was fine with both.  Today, the internet only works on the windows side.  Ubuntu connects okay to the wired network (so it says) but I cannot ping anything and MOST of the time (49/50) no web page will load.  Though that 50th page WILL load, it loads very slowly.

Thinking something broke in the ubuntu install, I tried loading from the Ubuntu live DVD I originally installed from.  Same issue.  Then I tried Mint and Fedora, both from live CD's.  Exactly the same situation.  All of those live CDs used to connect to the internet with no issue.

Now I'm thinking hardware issue, but again, windows is working fine.

Any ideas?

---

### Post by ahallubuntu on 2013-01-20
Have you rebooted your router?

---

### Post by locustmotives on 2013-01-20
It's a university network.  I don't really have any control over it.  A laptop plugged into the same port and booting off of the same live CDs works fine.  

Does the network maybe hate my MAC?  Is there some possible hardware failure?

---

### Post by tgalati4 on 2013-01-21
That is strange.  Sounds like your IP address and/or MAC address got blacklisted by the router.  Does your campus network have monitoring that would do such blacklisting?  Were you running any services on the Ubuntu side that might cause such blacklisting?

---

### Post by sandsjh on 2013-01-21
Does the university require you to install a certificate to access their network? As in TLS, PEAP, LEAP, etc (aka 802.1Q).

---

