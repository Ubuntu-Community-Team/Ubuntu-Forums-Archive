---
title: "WIFI is not working in ASUS 1005 PX- Ubuntu netbook Remix"
date: 2010-09-18
forum: Networking &amp; Wireless
---

### Post by basubunan on 2010-09-18
I've bought a Asus EEEpc 1005 PX and trired to install Ubuntu netbook. But I found that wifi is not working. It's not detecting the wifi cards.
I tried ifconfig, and it is showing me,

ETH0 and L0 only. 

When I tried LSPCI it's showing me
Ethernet controller: Atheros Communications Atheros AR8132/L1c Gigabit ethernet adapter (rev c0)
Network Controller: Atheros Communication inc. Device 002c (rev 01)

I'm a newbie here. Please tell me how can i set up the wifi here. 

(I tried with Meego, and Meego detected the wireless autometically..But I want to use Ubuntu)

---

### Post by basubunan on 2010-09-18
forgot to mention, i've installed ubuntu netbook remix 10.04

---

### Post by nixnotwin on 2010-09-19
Make sure you have access to internet and do this at the terminal

```
sudo apt-get update
sudo apt-get install linux-backports-modules-wireless-lucid-generic
sudo reboot
```

More fixes can be found here:

[https://help.ubuntu.com/community/EeePC/Fixes]("https://help.ubuntu.com/community/EeePC/Fixes")

---

### Post by basubunan on 2010-09-19
Thanks a lot...it's working... :)

---

### Post by basubunan on 2010-09-21
but the connection is poor...not stable i mean...
any solution for this?
thanks...

---

### Post by psychok7 on 2010-09-24
does this happen in ubuntu 10.10 netbook? i dont really have a ethernet cable to update

---

### Post by basubunan on 2010-09-24
yes 10.04 Lucid

---

### Post by anagor_lv on 2010-11-14
basubunan,
How did you install Ubuntu on Asus Eee PC 1005PX?
I have the same netbook.

This is what I did:
1) I downloaded the .iso image,
2) created a USB drive
3) Started ASUS boot manager, changed Boot Priority to 1) Removable dev. 2) ATAPI-CD (which I do not have) 3) HDD.
4) Disabled boot booster
5) Inserted USB
6) restarted

The system loaded WIndows 7

How do I get it to boot from USB?

---

### Post by anagor_lv on 2010-11-14
I have found out a way to boot from a USB stick:
[http://vip.asus.com/forum/view.aspx?board_id=20&model=Eee+PC+1000H/XP&id=20090507154557268&page=1&SLanguage=en-us](http://vip.asus.com/forum/view.aspx?board_id=20&model=Eee+PC+1000H/XP&id=20090507154557268&page=1&SLanguage=en-us)
I tried it on ASUS Eee PC 1005PX.
It works!

---

