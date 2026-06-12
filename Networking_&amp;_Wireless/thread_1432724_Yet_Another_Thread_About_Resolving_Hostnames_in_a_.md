---
title: "Yet Another Thread About Resolving Hostnames in a Mixed Ubuntu/Windows Environment."
date: 2010-03-18
forum: Networking &amp; Wireless
---

### Post by AlphaMack on 2010-03-18
I'm managing 10 XP Home workstations and using Ubuntu on my desktop to share a folder to those machines.  However, I cannot ping or VNC to those machines by hostname although IP addresses work.  Let me reword that:  SOME work.  I'll explain in a moment.

The router distributes dynamic IPs and leases them for 4 hours.  It is not feasible to switch to static IPs as the connection is shared with other workstations I do not manage.  Needless to say, it is a PITA in trying to identify IP addresses to each workstation without using Wireshark to filter BROWSER announcements.

Each of the XP workstations can see my share (this is important), find the printer share, and ping via hostname.  It's the reverse (Ubuntu to Windows) which is a problem.


Here is what I have done:

1.  Ensured that winbind is installed.

2.  Edited smb.conf and changed the following line:
```

	name resolve order = lmhosts wins bcast host

```

3.  Edited nsswitch.conf and changed the order of hosts:
```

hosts:          files mdns4_minimal [NOTFOUND=return] dns wins mdns4

```

I moved wins behind dns as Liferea broke as per [this bug](https://bugs.launchpad.net/ubuntu/+source/liferea/+bug/446649).

4.  Lastly, I installed dnsmasq and configured it as suggested [here](http://www.ubuntugeek.com/local-dns-cache-for-faster-browsing-on-ubuntu-machine.html).  As we use OpenDNS I modified the prepend line to include the two OpenDNS servers.

Now some of the workstations can be resolved by their hostnames, but others cannot, still requiring IP addresses to connect.  Additionally, I can see all of them by their hostnames under Network in Nautilus, but I cannot mount the shares.

Any ideas as to what I may be overlooking?

---

### Post by AlphaMack on 2010-03-25
I did some investigating into this and to make a long story short, Bonjour/Zeroconf was installed on the PCs I was able to access.

Installing Bonjour seemed to solve the issue with connecting by hostname but after reading many Launchpad bug reports and forum posts elsewhere it seems that there is a problem with (1) OpenDNS and to an extent other ISP hijacking and (2) nsswitch.conf containing "wins" in the hosts line.

It's solved on my end but it may not be for others, so I won't mark this thread solved.

The advice I have seen thrown around include (1) installing dnsmasq or bind in which the latter could be overkill, (2) switching to static IPs which may not be feasible, or (3) installing Bonjour/Zeroconf on Windows.

Maybe someone can provide further insight into this.

---

