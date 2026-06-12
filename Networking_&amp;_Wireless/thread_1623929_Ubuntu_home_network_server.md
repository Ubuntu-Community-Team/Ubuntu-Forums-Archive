---
title: "Ubuntu home network server"
date: 2010-11-17
forum: Networking &amp; Wireless
---

### Post by wp.rauchholz on 2010-11-17
I am planning to setup a home network with Ubuntu.
the home network consists of ~3/4 computers; a mediaserver (reelbox) and 2 more PCs.

Can I setup the server as a DSL router and get rid of my modem/router I have right now?

---

### Post by jpl888 on 2010-11-17
You can use the RFC1483 functionality of your router so that it merely passes on data to your Linux box. You then use a PPPOE/A client on the Linux box and it becomes the router.

Alternatively you could purchase a cheap USB DSL modem which would do the same and wouldn't need a power supply. However I have yet to find one that supports newer DSL standards (like ADSL2+).

So to answer the original question no not really. You need to have some sort of external device to talk to the DSL line. How much you get the device to do is down to your preference though.

---

### Post by wp.rauchholz on 2010-11-18
Found this one. Maybe it works

[http://www.traverse.com.au/productview.php?product_id=115](http://www.traverse.com.au/productview.php?product_id=115)
[http://www.yawarra.com.au/pdfs/XC-P-ADSL2-V.pdf](http://www.yawarra.com.au/pdfs/XC-P-ADSL2-V.pdf)
[http://www.traverse.com.au/productview.php](http://www.traverse.com.au/productview.php)

Both dhould work, right?

---

### Post by jpl888 on 2010-11-18
That's interesting. In theory I can't see any reason why it shouldn't work.

It looks like the card is an integrated NIC and DSL CPE in one, thus sidestepping any need for a special driver.

Looks like getting one might be easier said than done though, did you find anywhere you could actually buy it online?

It is doing the same thing I discussed earlier about RFC1483 bridging just all on one card rather than with anything "outside the box" scuse the ironic pun.

---

