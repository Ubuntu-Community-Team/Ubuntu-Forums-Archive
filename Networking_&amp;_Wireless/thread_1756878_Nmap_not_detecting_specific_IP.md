---
title: "Nmap not detecting specific IP"
date: 2011-05-12
forum: Networking &amp; Wireless
---

### Post by EmporerD on 2011-05-12
I'm trying to detect all the IP addresses of devices on my LAN using Nmap.

I type in the command 
```

~$ nmap -sP 192.168.1.1-255
```

and it outputs
```

Starting Nmap 5.00 ( http://nmap.org ) at 2011-05-12 17:04 PDT
Host 192.168.1.2 is up (0.00073s latency).
Host 192.168.1.6 is up (0.0038s latency).
Host 192.168.1.148 is up (0.00026s latency).
Host 192.168.1.254 is up (0.0015s latency).
Nmap done: 255 IP addresses (4 hosts up) scanned in 3.01 seconds
```

It seems fine except that I know that the address 192.168.1.198 is up, I can even ping it with a reply, but for some reason Nmap won't detect it. 

Any ideas?

---

