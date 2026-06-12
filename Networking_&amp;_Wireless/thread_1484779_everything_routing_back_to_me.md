---
title: "everything routing back to me ?"
date: 2010-05-16
forum: Networking &amp; Wireless
---

### Post by cookednoodles on 2010-05-16
Since yesterday, out of the blue, I can no longer connect to my network.
Every ip on the 192.168.1.X range is for some reason pointing back to localhost.

The machine is dual boot, I have no such issues with windows, it's just my ubuntu (lucid)
Does anyone have any ideas ?

---

### Post by Iowan on 2010-05-16
Have you checked **resolv.conf**? (Maybe that's where your information came from.) Dunno your configuration, but could something in router have changed?

---

### Post by wirelessmonkey on 2010-05-16
```
 cat /etc/hosts 
```

How do you know or why do you think the whole subnet points back to your localhost?

---

### Post by Zorael on 2010-05-17
And it's not just listing destination host unreachable? I guess that gives the illusion that the ping is being routed to yourself.
```
$ ping 10.0.0.2
PING 10.0.0.2 (10.0.0.2) 56(84) bytes of data.
From 10.0.0.20 icmp_seq=1 Destination Host Unreachable
From 10.0.0.20 icmp_seq=2 Destination Host Unreachable
From 10.0.0.20 icmp_seq=3 Destination Host Unreachable
^C
--- 10.0.0.2 ping statistics ---
4 packets transmitted, 0 received, +3 errors, 100% packet loss, time 3016ms, pipe 3
```

---

