---
title: "Internet not working on Ubuntu"
date: 2010-03-07
forum: Networking &amp; Wireless
---

### Post by vikas_123 on 2010-03-07
I have cablenet connected on Windows XP. On windows it's working fine. On windows XP it alwasy ask me username and password and then it starts to work.
 
But same cablenet is not working on Ubuntu on same laptop. It shows "connection established" if cable is connected.
 
But I can not able to open website.
 
Please help me to come out of this..

---

### Post by dineshs on 2010-03-08
Do you have a modem? If so how this modem is connected to PC? Ethernet port or USB?

---

### Post by vikas_123 on 2010-03-08
No, I do not have modem..
 
Just connection of cable to RJ45 port..

---

### Post by dineshs on 2010-03-08
Open browser and try this site
64.233.189.104
What do you get?

---

### Post by vikas_123 on 2010-03-08
Yes you are right.  My laptop has inbuild modem of "HDAUDIO Soft Data Fax Modem with SmartCP". Driver for this modem has installed on XP. But I think this modem driver is not present on ubuntu. I have also searched it on net, but could not get it.
 
So what next I have to do?

---

### Post by sparky-steve on 2010-03-08
> **vikas_123 said:**
> No, I do not have modem..
 
Just connection of cable to RJ45 port..

What does the other end of the network cable connect to... a hub? cable modem??

Does your computer have an IP address?

---

### Post by marbertone on 2010-03-08
Try 
```

sudo pppoeconf

```
if I understood well, you should be using Ethernet cable. It should configure your provider. Then I suggest you to create a link to the following command:
```

gksudo pon dsl-provider

```
which will start pppoe manually (anyway, put 'connect on boot' in pppoeconf).
Hope this helps!
Cheers,
Mario Alberto

---

### Post by dineshs on 2010-03-08
> **vikas_123 said:**
> Yes you are right.  My laptop has inbuild modem of "HDAUDIO Soft Data Fax Modem with SmartCP". Driver for this modem has installed on XP. But I think this modem driver is not present on ubuntu. I have also searched it on net, but could not get it.
It is a dialup modem .But you are connecting to ethernet(You mentioned RJ45 and not RJ11)Please confirm

---

### Post by dineshs on 2010-03-09
For internal modems to work you must first use scanmodem tool
[https://help.ubuntu.com/community/DialupModemHowto/ScanModem](https://help.ubuntu.com/community/DialupModemHowto/ScanModem)

---

### Post by garvinrick4 on 2010-03-09
What does it say in cat /etc/resolv.conf

It should say who you are connected to.

If it is blank you are not getting through.

---

### Post by vikas_123 on 2010-03-10
Hi all,
 
My problem solved. I have configured DSL connection as per my requirement and internet is working fine on ubuntu.
 
Thanks for help

---

