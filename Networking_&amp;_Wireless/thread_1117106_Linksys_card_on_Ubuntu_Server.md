---
title: "Linksys card on Ubuntu Server"
date: 2009-04-05
forum: Networking &amp; Wireless
---

### Post by erat123 on 2009-04-05
Greetings!

I've been looking everywhere, but I can't find anything on this topic with Ubuntu Server Edition.  Only the Desktop edition with the nice interfaces ;)

I have a Linksys WMP54G V4 PCI card.  I'm trying to get it to work with Ubuntu 8.10 Server Edition.

I ran a lspci command and it says the card is recognized as a RaLink.

Any help is greatly appreciated!


For an update, I also have a WMP54G V4.1 if that would be easier to setup.

---

### Post by x22 on 2009-04-05
found a pretty good page at

[http://www-personal.umich.edu/~mejn/rt61.html](http://www-personal.umich.edu/~mejn/rt61.html)

using "compat-wireless-2009-03-04" on my ubuntu server
8.10 machine, I find an "rt61pci" driver

---

### Post by erat123 on 2009-04-05
Thanks for the quick response x22!  That site you sent is great!


I ended up finding another solution before you posted a response.  I disabled my wired connection by commenting out "auto eth0" from my /etc/network/interfaces file.

Then I reset my network via:

```
sudo /etc/init.d/networking restart
```

Turns out the RaLink driver worked when I configured some static settings in /etc/network/interfaces.

I'll remember that link you sent for future projects, I'm sure it'll be very helpful!

---

