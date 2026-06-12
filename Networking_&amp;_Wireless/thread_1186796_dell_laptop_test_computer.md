---
title: "dell laptop test computer"
date: 2009-06-13
forum: Networking &amp; Wireless
---

### Post by andrea000 on 2009-06-13
Hello

I have bought a dell c500 or c600 i am not sure its one of the two.I am
trying to install ubuntu on it for two days now but the broad com wireless
card will not pick up and the wired one is not recognize.Can anyone help
me please

---

### Post by synapsys on 2009-06-13
Open up a terminal and type:

```
lspci | grep Ethernet
```

so we can help you

---

### Post by andrea000 on 2009-06-14
This is all it out puts and it doesn't show my wireless card
i have found that the wireless card is a broadcom 43xx card
and it is blacklisted from the info i can get 


andrea@andrea-laptop:~$ lspci | grep Ethernet
02:00.0 Ethernet controller: 3Com Corporation 3c905C-TX/TX-M [Tornado] (rev 78)

---

### Post by overdrank on 2009-06-14
Moved to  Networking & Wireless

---

### Post by superprash2003 on 2009-06-15
post output of ifconfig from the terminal
also post output of
1)lshw -C network
2)iwconfig
3)sudo iwlist scanning

---

