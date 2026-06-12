---
title: "Network computers not accessible by host-name?"
date: 2010-08-16
forum: Networking &amp; Wireless
---

### Post by Tamalin on 2010-08-16
For some reason, all the computers on my network can't reach each other via their host names.  For example, the ping command doesn't recognize host names:
```

$ ping file-server

PING file-server (208.68.139.89) 56(84) bytes of data.
^C
--- file-server ping statistics ---
20 packets transmitted, 0 received, 100% packet loss, time 19152ms

```

However, ping works fine if I use IP addresses instead.  I would put the address for "file-server" in my /etc/hosts file, except for the fact that DHCP changes it's address occasionally.

I attempted changing the line
send host-name "<host-name>";
in /etc/dhcp3/dhclient.conf to 
send host-name "file-server";
but to no avail.  Does anyone know how to resolve this issue?

---

### Post by Iowan on 2010-08-16
I use DNSMasq for DNS/DHCP server - it lets me ping machines by name. One other option for you is to set up a static lease on your DHCP server - the machine would then get the same address each time.

---

### Post by Tamalin on 2010-08-17
Thank You, Iowan, for the input,
but I now see that the problem is not with the server, it is with my client laptop.  Strangely enough, though both the server and the client are running Ubuntu 10.04, they can't see each other's host names.  A simple test with Mac OS X promptly finds "file-server" on the network without a problem, so it appears the only computer that can't see the host name is the Ubuntu client.  Maybe I am missing an important package somewhere?

---

