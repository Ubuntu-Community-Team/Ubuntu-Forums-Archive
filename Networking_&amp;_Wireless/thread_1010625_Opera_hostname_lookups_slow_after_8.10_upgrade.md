---
title: "Opera hostname lookups slow after 8.10 upgrade"
date: 2008-12-13
forum: Networking &amp; Wireless
---

### Post by geheimdienst on 2008-12-13
The upgrade to Ubuntu 8.10 made Opera 9.62 painfully slow. When opening a web page, I have a 20 sec pause with the message "Looking up hostname". Only then the page starts coming up. This did not happen with Ubuntu 8.04.

Wireshark shows this when Opera opens a website:

```

Seconds		Description
0.000000	DNS Standard query AAAA questionablecontent.net
5.003815	DNS Standard query AAAA questionablecontent.net
10.006886	DNS Standard query AAAA questionablecontent.net.Speedport
15.011791	DNS Standard query AAAA questionablecontent.net.Speedport
20.015267	DNS Standard query A questionablecontent.net
20.016927	DNS Standard query response A 64.131.83.210

```

The AAAA queries time out, while the "A" query works and is fast.

I think the problem is: The Ubuntu 8.10 upgrade made some network settings changes and those mislead Opera into trying IPv6 before IPv4. How do I undo these changes, or how do I disable IPv6?

Thanks in advance.

---

### Post by abscess on 2009-01-12
I have the exact same problem. Clean install of Ubuntu 8.10 and Opera 9.63.

Anyone know how to work this one out?

---

### Post by blazemore on 2009-01-12
```
cat /etc/hosts
```
Post output here in [code ] tags

---

### Post by superprash2003 on 2009-01-12
disabling ipv6 [http://www.ubuntuforums.org/showthread.php?t=87798](http://www.ubuntuforums.org/showthread.php?t=87798) .. you could also try using opendns servers [http://www.prash-babu.com/2008/04/how-to-configure-dns-servers-in-linux.html](http://www.prash-babu.com/2008/04/how-to-configure-dns-servers-in-linux.html)

---

