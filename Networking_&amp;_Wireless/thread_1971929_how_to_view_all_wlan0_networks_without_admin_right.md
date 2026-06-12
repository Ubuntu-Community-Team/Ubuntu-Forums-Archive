---
title: "how to view all wlan0 networks without admin rights?"
date: 2012-05-03
forum: Networking &amp; Wireless
---

### Post by cdaringe on 2012-05-03
Hi all,

Similar to an old post of mine, i'm curious how I can view all visible networks to my wifi device.

```
iwlist wlan0 scan(ning)
```
returns only the last queried result, and only 1 network.  I want to see everything wlan0 sees!

How would you do it?

Also, for context, i am piping a command to a terminal from python, then pulling the results back in.

Hopefully one of you gurus has some wisdom for me. :)

---

### Post by jualin on 2012-05-03
I am pretty sure you can just use iwlist without specifying the network interface to show all the networks from all network interfaces. ```
iwlist scan
```

Or you can specify the interface ```
iwlist wlan0 scan
```

---

### Post by cdaringe on 2012-05-03
nah, unfortunately that doesn't do it. 

confirmed both by the docs (see link below) and many, many failed attempts!

[http://linux.die.net/man/8/iwlist](http://linux.die.net/man/8/iwlist) see the scanning section.  :(

---

