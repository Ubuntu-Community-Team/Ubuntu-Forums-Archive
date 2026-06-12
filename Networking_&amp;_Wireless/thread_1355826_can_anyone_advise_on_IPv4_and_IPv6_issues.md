---
title: "can anyone advise on IPv4 and IPv6 issues"
date: 2009-12-15
forum: Networking &amp; Wireless
---

### Post by Jethro_uk on 2009-12-15
I'm having problems with slow ssh file transfers on my internal network.

I've read some hints that Linux using IPv6 can be slow.

1) How can I tell what protocol is being used by an interface ?
2) How can I tell Ubunutu to not use IPv6 for internal addresses.

FWIW I am using IPv4 address formats to connect my machines ...

Downstairs : 192.168.1.102
Upstairs : 192.168.1.98

the upstairs machine has a 2nd interface, set to 192.168.0.2

so when I connect from downstairs to upstairs, it's ssh myname@192.168.1.98

---

### Post by ApEkV2 on 2009-12-15
From my understanding IPv6 isn't even being used widespread at all yet.
I know ubuntu supports IPv6, but it won't use it unless manually specified.

Chances are no, you are not using IPv6.  
If you seriously want to check, use ifconfig in the terminal.
If eth0 (or whatever interface you use) has an IPv4 address, (192.168.1.100 etc) then you are using IPv4

Wireshark will also show what protocols are used.

---

