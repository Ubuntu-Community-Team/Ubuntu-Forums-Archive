---
title: "the mystery of &quot;08&quot; and &quot;09&quot; in IP addresses"
date: 2010-02-22
forum: Networking &amp; Wireless
---

### Post by glubbdrubb on 2010-02-22
This is more of a general networking question. I have found this is also true on Windows hosts.

One can not use "08" or "09" in IP addresses. I have no idea why. I could probably find what I am looking for in some RFC but don't know where to start looking.

A quick Google brought up [this page]("http://www.perlmonks.org/?node_id=25584") but more specifically [this post]("http://www.perlmonks.org/?node_id=25599").

So it has something to do with the way C interprates the octal values of 08 and 09. Wierd.

Could someone else explain this?

This thread could be moved to the programmers forum, which is fine by me.

---

### Post by maweki on 2010-02-22
this is bogus. 08 and 09 are allowed. This just refers to checking whether an IP address is valid or not.

Most programming languages will take numbers with leading zeros as octal (base 8)-Numbers. This has no impact on 01 to 07 (and after 10 it is recognized as decimal - base 10), but 08 and 09 are invalid numbers in a base-8 number-system (like in base 10, only 0 to 9 and in base 16 only 0 to F is valid). The programming language (the regular expression-parser, usually) will throw an error or simply "false" which gives the impression of wrong input and therefore an invalid address, even if it is valid.

A programmer should check the manual in this situations.

An IP with 08 and 09 is valid. Only the way in which one checks for valid ip addresses could give false negatives.

---

### Post by glubbdrubb on 2010-02-22
Be that as it may, I still can't ping, ftp or ssh an ip address that contains 08 or 09, where as 8 and 9 work. Try it. You don't actually need to have those hosts on the network.

```
ping 192.168.08.1
ping: unknown host 192.168.08.1

ping 192.168.8.1
PING 192.168.8.1 (192.168.8.1) 56(84) bytes of data.
64 bytes from 192.168.8.1: icmp_seq=1 ttl=60 time=1886 ms
64 bytes from 192.168.8.1: icmp_seq=2 ttl=60 time=1077 ms
64 bytes from 192.168.8.1: icmp_seq=3 ttl=60 time=573 ms


```
The same is true for telnet and many other foundational applications on different platforms.

---

### Post by maweki on 2010-02-22
Because 08 gets interpreted as octal number.

There is really no expected behaviour in that case. The application could throw an error, it could just delete the leading zeroes.

of course is an ip-address with 08 invalid, if you take the leading zero as a sign for octal. It would also be ok to just delete those.



Or the rephrase that

**08 is not a valid number itself** if taken as octal, which many languages do because of the leading zeroes.

It has nothing whatsoever to do with whether it is an ip or not.

it would be like the binary number 120. There is just no "2" in the binary system as there is no "8" in the octal system.

---

### Post by glubbdrubb on 2010-02-22
I see.

It's just really irritating because it means in bash scripting I have to remove the 0's from 08 and 09 when reading in ip addresses from a file.

It's a pity bash didn't think of that for me...

But thanks anyway

---

