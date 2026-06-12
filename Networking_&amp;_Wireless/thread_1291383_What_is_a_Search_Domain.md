---
title: "What is a Search Domain?"
date: 2009-10-14
forum: Networking &amp; Wireless
---

### Post by deathrunner1 on 2009-10-14
Hello all. I am new new Linux and am really enjoying it.  I have something that I don't know what it is though.  I'm attempting to set up a static IP. In the Network Connections window under eth0, it has a field: Search Domain   .  I don't know what a Search Domain is though.  Everything else to fill out manually I know.  Any help would be greatly appreciated.  Or if anyone knows any Search Domain I can use, that would be helpful as well.

Thanks and have a good one.

Lynn

---

### Post by Bachstelze on 2009-10-14
The domains you add in search domains will be "searched" by your computer when you want to  lookup a non-canonical host name and it is not found. Here's an example:

```
firas@iori ~ % ping itsuki
ping: unknown host itsuki
```

Then if I add my domain (fkraiem.org) in the search domains:

```
firas@iori ~ % ping -c1 itsuki
PING itsuki.fkraiem.org (91.121.117.123) 56(84) bytes of data.
64 bytes from itsuki.fkraiem.org (91.121.117.123): icmp_seq=1 ttl=58 time=4.21 ms

--- itsuki.fkraiem.org ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 4.213/4.213/4.213/0.000 ms
```

Since itsuki is not a canonical hostname, the system will complete it using the domain name I put in my search domains, and blammo, it'll work.

---

### Post by deathrunner1 on 2009-10-14
Wow that was an excellent explanation!  Makes perfect sense and I will be using it since i'm setting up a local domain with the hosts file.

MUCH APPRECIATED!

and I hope you're having nice weather over there in France.:)



Lynn

---

