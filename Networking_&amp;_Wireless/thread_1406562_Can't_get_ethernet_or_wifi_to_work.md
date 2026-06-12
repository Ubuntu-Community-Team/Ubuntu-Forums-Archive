---
title: "Can't get ethernet or wifi to work"
date: 2010-02-14
forum: Networking &amp; Wireless
---

### Post by ChrisML123 on 2010-02-14
I have an Asrock A330GC, with onboard ethernet, and an Engenius PCI card for wifi.

I installed ubuntu server 9.10 no problems, and it picked up my ethernet in the installation with no difficulties.

I couldn't get 9.10 to do what i wanted, so I tried installing 8.4 instead. This however didn't pick up any of the drivers, so i couldn't get online.

So i reinstalled 9.10, only to find that now it couldn't find network in the installation. Absolutely NOTHING has changed, the ethernet cable still plugged in, and if i plug same cable into my laptop, it works fine.

Any ideas people?
ifconfig doesn't mention any eth0, just lo, with an ip of 127.0.0.1 and amask of 255.0.0.0 which i'm fairly certain means its dead.

Bless,[URL="http://allaboutchris.co.uk"]
Chris Lowry[/URL]

---

### Post by chili555 on 2010-02-14
Let's find out what ethernet card you have. Please do:```
lspci -nn | grep Ethernet
```Once we know what driver it needs, we'll modprobe it and try to troubleshoot.

---

