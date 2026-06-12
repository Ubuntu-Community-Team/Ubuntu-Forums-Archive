---
title: "Internet connection"
date: 2006-07-03
forum: Networking &amp; Wireless
---

### Post by fuzi on 2006-07-03
hello,
I am a new user in Linux, I installed Ubuntu 6.06 in my desktop.
I would like to connect to the Internet.
Network: Cable, by a Modem and a network card.
Provider: Netvision.
Thanks.

---

### Post by 5hane on 2006-07-03
Do you want to connect using the dial-up modem that is connected to your computer, or do you want to connect via another computer on your network that has internet?

---

### Post by fuzi on 2006-07-03
I don't have another computer. I got a modem from the network provider and it is connected to a network card in my computer.

---

### Post by verbatim210 on 2006-07-03
what is actually the problem?

---

### Post by fuzi on 2006-07-03
It is a cable modem.
The problem is: I have just installed Ubuntu 6.06 and I don't know how to connect to the Internet.

---

### Post by sethfc on 2006-07-03
i am in the same situation - i have installed older versions of ubuntu before, and the installation detected my networking hardware (the LAN port) and set everything up just fine so i could surf the net hot off installation - but this time this was not the case.

ifconfig i get.... (skipping down to "lo"):

lo       Link encap: Local Loopback
         inet addr: 127.0.0.1  Mask: 255.0.0.0
         inet6 addr:  ::1\128 Scope:Host
         UP LOOPBACK RUNNING   MTU:16436  Metric:1
then
all packets have 85 errors and nothing else.

so yea.... o_0

---

### Post by mziel on 2006-07-03
You could use pppoeconf - console program. Install it:
```
sudo aptitude install pppoeconf
```
and after this, if it doesn't start after installation, run it with pppoeconf. You have to know your user and pass obtained from ISP, proper ethernet card will be scanned automagically ;-)

---

