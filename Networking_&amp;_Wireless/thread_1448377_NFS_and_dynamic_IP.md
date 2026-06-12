---
title: "NFS and dynamic IP"
date: 2010-04-06
forum: Networking &amp; Wireless
---

### Post by sabersong on 2010-04-06
I have two linux machines networked using NFS through a Dynex wireless router.  There is no way in the router to assign static IPs to the two computers, and I have three other devices also using the wireless router.  Sometimes, the power goes out, sometimes my wife turns off one or both of the linux machines, sometimes we have to reset the router. In all these cases, IP addresses are subject to change.  Is there any way to automatically mount an NFS share with a dynamic IP address?

---

### Post by netztier on 2010-04-06
> **sabersong said:**
> Is there any way to automatically mount an NFS share with a dynamic IP address?

Try mDNS resolution as provided by [avahi]("http://www.avahi.org/"). Machines in a common broadcast domain can refer to each other by "hostname**.local**" [1]. I've found this to work out-of-the-box with Ubuntu Desktop installations. Ubuntu Server might need the additional installation of the package **avahi-daemon**.

Avahi is a [Zeroconf]("http://http://en.wikipedia.org/wiki/Zeroconf") implementation - Apple Inc. call theirs "Bonjour".


For example, two of my machines are called blaze and cube:

```
marc@cube:~$ **ping blaze.local**
PING blaze.local (172.20.125.30) 56(84) bytes of data.
64 bytes from blaze.mydomain.com (172.20.125.30): icmp_seq=1 ttl=64 time=0.131 ms
64 bytes from blaze.mydomain.com (172.20.125.30): icmp_seq=2 ttl=64 time=0.128 ms
^C
--- blaze.local ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1001ms
rtt min/avg/max/mdev = 0.128/0.129/0.131/0.011 ms
```

and in the other direction:

```
marc@blaze:~$ **ping cube.local**
PING cube.local (172.20.125.31) 56(84) bytes of data.
64 bytes from cube.mydomain.com (172.20.125.31): icmp_seq=1 ttl=64 time=0.075 ms
64 bytes from cube.mydomain.com (172.20.125.31): icmp_seq=2 ttl=64 time=0.143 ms
...
^C
--- cube.local ping statistics ---
11 packets transmitted, 11 received, 0% packet loss, time 9999ms
rtt min/avg/max/mdev = 0.075/0.120/0.166/0.025 ms
```


Try using <hostname>.local in your /etc/fstab - it might just work.

regards

Marc


[1] note: if the DNS servers your systems are using (as per the content of /etc/resolv.conf) are considering themselves authoritative for the .local toplevel domain, avahi will detect this on startup and disable itself. You might want to involve the maintainer of your DNS in some discussions - I had to do the same with mine.

---

### Post by sabersong on 2010-04-06
Thank you!  That was exactly what I needed.

---

