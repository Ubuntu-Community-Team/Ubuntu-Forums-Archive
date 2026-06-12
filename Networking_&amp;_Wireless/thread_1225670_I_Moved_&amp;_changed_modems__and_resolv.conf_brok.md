---
title: "I Moved &amp; changed modems  and resolv.conf broke"
date: 2009-07-28
forum: Networking &amp; Wireless
---

### Post by SlothPaladin on 2009-07-28
I recently moved and have a different router and modem. I am running Ubuntu 8.10 Server, but I don't see why these problems would be specific to Ubuntu Server.

I have the Ubuntu Server box (its for PHP and mySQL testing) hooked up to a Windows XP computer which has that connection bridged with a with a wireless connection that has internet.  The server can ping both the router and the cable modem but 'cannot' connect to the internet. After a lot of Googling I discovered that I can connect to the internet but only if I use ip addresses.

When I ran **sudo apt-get update** it failed to connect, I would like to install drivers for a wireless card but Ubuntu seems impossible without connecting to the internet.

My resolv.conf looks like this
[i]domain gateway.2wire.net
search gateway.2wire.net
nameserver 192.168.2.1[/i]

The last modem I used was a 2wire, the modem address is 192.168.2.1 (I changed that myself) but I don't know what to put for domain and search.  My current modem is a Motorola SBG900.

I would be grateful for any help

---

### Post by Iowan on 2009-07-28
Is the modem set up to forward DNS requests? (I'd wonder about the XP machine, but I presume that hasn't changed from when it was working).

---

### Post by SlothPaladin on 2009-07-28
I don't see any options in the modem to set up forward DNS requests, I ran ipconfig on the XP box and got
```

Connection-specific DNS Suffix  . : hsd1.wa.comcast.net.
IP Address  . . . . . . . . . . . : 192.168.1.102
Subnet Mask . . . . . . . . . . . : 255.255.255.0
Default Gateway . . . . . . . . . : 192.168.1.1
```
so I tried replacing 'gateway.2wire.net' with 'hsd1.wa.comcast.net' and 'hsd1.wa.comcast.net.' but that did not seem to work.

then I tried replacing  '192.168.2.1' with '192.168.1.1' (routers address, not modems) and leaving 'hsd1.wa.comcast.net' in place and it WORKED!

Thanks for your post, it did make me look at the windows settings and helped me figure it out!

---

### Post by Iowan on 2009-07-29
Guess I was missing some of the details about how things were connected, but I'm glad the end result was success...

---

