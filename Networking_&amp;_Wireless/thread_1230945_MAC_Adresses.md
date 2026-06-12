---
title: "MAC Adresses"
date: 2009-08-04
forum: Networking &amp; Wireless
---

### Post by stockley on 2009-08-04
I was wondering if there are any applications or shell scripts I could run to find MAC addresses of laptops on my wireless network.
Any help would be very much appreciated.
:)

---

### Post by wirelessmonkey on 2009-08-04
Your router will either log those, or list connected hosts....
Else you could use wireshark, and sniff traffic that has been authenticated,

---

### Post by cariboo on 2009-08-04
I use this to find mac and ip addresses of computers on my network:

```
sudo nmap -PR -sP 192.168.1.0/24
```

if you don't have nmap installed click the link.

[apt://nmap](apt://nmap)

---

### Post by stockley on 2009-08-04
Thanks guys,
I'll test them out next reboot. :)

---

