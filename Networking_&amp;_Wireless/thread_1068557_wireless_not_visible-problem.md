---
title: "wireless not visible-problem"
date: 2009-02-13
forum: Networking &amp; Wireless
---

### Post by hoboy on 2009-02-13
I have just install ubuntu 8.10 on my new AMILPI3620E01 Fujitsu computer
it has wireless, I have wireless at home where the computer is, and I am using wireless on the other computers I have, but it can not detect the wireless.

---

### Post by x33a on 2009-02-13
if you are sure that your wireless card is working, drivers loaded etc, then type "iwlist scan" in a terminal and see if it finds an active wireless signal.

---

### Post by hoboy on 2009-02-13
> **x33a said:**
> if you are sure that your wireless card is working, drivers loaded etc, then type "iwlist scan" in a terminal and see if it finds an active wireless signal.
I have tried your suggestion
the result
luc@ubuntu:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

pan0      Interface doesn't support scanning.

---

### Post by x33a on 2009-02-13
well you don't have a wireless connection configured yet.

it should be something like wlan0. pan0 is for bluetooth, so i assume you also have bluetooth on your machine.

first configure your wlan, then only can you read the signals.

[https://help.ubuntu.com/community/WifiDocs/WiFiHowTo](https://help.ubuntu.com/community/WifiDocs/WiFiHowTo)

---

