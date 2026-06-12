---
title: "Dell Wireless 1505 Draft 802.11n WLAN Mini-Card"
date: 2009-02-18
forum: Networking &amp; Wireless
---

### Post by alias301 on 2009-02-18
So I just bought a new computer and it has the Dell Wireless 1505 Draft 802.11n WLAN Mini-Card and i know it works in Windows, but in Ubuntu even with the restricted driver it is painfully slow and cuts out ALL the time. Pages usually take 3-10 minutes to load and there is not network traffic during that time.

any help is very appreciated!

---

### Post by superprash2003 on 2009-02-18
post output of ifconfig from the terminal. you could try changing DNS servers to opendns - 208.67.222.222 and 208.67.220.220

For reference : [http://www.prash-babu.com/2008/04/how-to-configure-dns-servers-in-linux.html](http://www.prash-babu.com/2008/04/how-to-configure-dns-servers-in-linux.html)

---

### Post by alias301 on 2009-02-18
Already tried changing my DNS server and even tried making my address a static one using the same method that I do with all of my computers but nothing has changed I still can get internet that is even somewhat decent. In firefox it takes anywere from 3-10 minutes for the page to load and in that time there is no network traffic.

Please I need help!!!

---

### Post by smc18 on 2009-02-18
I bought a Dell Vostro 1500 almost a year ago.  I'm almost certain it included the Dell Wireless 1505 n card.

Running lspci,
```
lspci
```

lists my wireless device as

> 0c:00.0 Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 03)


Ubuntu 7.04, 7.1 and I believe 8.04 all required some additional setup to work.

However, I'm using 8.10 now, and it speeds seem to be normal even for 802.11g (as I don't have a n router yet) and I don't remember having to set anything up for my wireless to work.

What version Ubuntu are you using?

---

### Post by alias301 on 2009-02-18
8.10 
my problem is that it connects but when I am in Firefox (or any browser) it just takes minutes and minutes to get anywhere and I checked using the system monitor and I have no network traffic at that time. But in windows i get internet quick and easy no 5 minute page delays.

---

### Post by smc18 on 2009-02-18
hmmm I don't think I can provide much help. Sorry

I know you have a draft-n wireless card, are you connecting to a draft-n router?  That might somehow be the culprit.

I have the same wireless card however, I'm connected using g.

---

### Post by alias301 on 2009-02-18
well my router is supports b/g and draft n but still the connection just keeps dropping constantly :(

---

### Post by PinkFloyd102489 on 2009-02-19
You'll probably have to install it using ndiswrapper then. There's a guide around here somewhere to do so.

When I had Ubuntu installed, it worked fine under the wl driver for my BCM4328.

---

