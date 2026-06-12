---
title: "Slow internet conection"
date: 2009-09-26
forum: Networking &amp; Wireless
---

### Post by mr.suchy on 2009-09-26
Hi,

I use wireless network to connect the internet. Right now I have 45% strength signal. When I run firefox I have to wait 15s to open a site. I check my connection to the internet and everything look good no loss package or something, ping ~25ms. Also I check 
```
top
```

```

Cpu(s): 10.3%us,  2.0%sy,  0.0%ni, 87.7%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   1026748k total,   768132k used,   258616k free,    37320k buffers
Swap:        0k total,        0k used,        0k free,   391796k cached

```

This problem I have from few days. On Windows XP internet is faster than Ubuntu. I forget, when I download from internet i have full speed. My problem is that I have to wait to see web page. Thanks for help.

---

### Post by spd106 on 2009-09-27
The usual suspects are:

* Slow DNS resolving - compare performance with openDNS.

* IPv6 - try turning IPv6 off [http://www.ubuntugeek.com/how-to-disable-ipv6-in-ubuntu.html](http://www.ubuntugeek.com/how-to-disable-ipv6-in-ubuntu.html)

If these don't work then it might be useful to try a different web browser such as Epiphany or Opera.

---

