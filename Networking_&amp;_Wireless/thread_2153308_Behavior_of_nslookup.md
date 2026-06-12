---
title: "Behavior of nslookup"
date: 2013-06-10
forum: Networking &amp; Wireless
---

### Post by duke.tim on 2013-06-10
So I was playing with nslookup on some bogus addresses, for a script.
and I ended up getting some unexpected behavior.

```
IP="192.168.1.1"
nslookup $IP
```
> Lookup failedServer:         A_vaild_address*
Address:        A_vaild_address


** server can't find 1.1.168.192.in-addr.arpa.: NXDOMAIN




The IP used in the NXDOMAIN field is backwards. Is this the normal convention for looking up domain names from IP's?

*same results on different DNS servers

---

### Post by Vitsliputsli on 2013-06-11
It's normal. "in-addr.arpa" is special domain for reverse DNS, in the syntax field must be backwards. 
[http://en.wikipedia.org/wiki/In-addr.arpa](http://en.wikipedia.org/wiki/In-addr.arpa)

---

### Post by duke.tim on 2013-06-11
Thank you for the help.

---

### Post by Lars Noodén on 2013-06-11
If you haven't seen it yet, there is also [dig](http://manpages.ubuntu.com/manpages/quantal/en/man1/dig.1.html).  It can do a lot more but is also good for basic lookups.

---

