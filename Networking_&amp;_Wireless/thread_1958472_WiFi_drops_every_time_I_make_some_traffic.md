---
title: "WiFi drops every time I make some traffic"
date: 2012-04-14
forum: Networking &amp; Wireless
---

### Post by iondoarion on 2012-04-14
Hello,

I've just installed a fresh Ubuntu 11.10 (32b) Oeniric on my Asus K72JT (Intel Core i5-480m, 2,66 Ghz, ATI Radeon 6370M, 4 GB RAM, Atheros AR9285 WiFi Network Adapter) and I have a problem when I try to access the Internet.
I've read some posts about similar problems and a good feedback I've seen on the solution is:

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install linux-backports-modules-jaunty
```

I couldn't try it because whenever I do, the internet connection drops and *this is where I am stuck*.

I've tried:
- a fresh re/install;
- Live CD;
- tried with WAN cable from the router (which connects and disconnects in a loop).

Are there other solutions that would not emply the usage of the internet connection?

TY

Ion

---

### Post by praseodym on 2012-04-14
Hi,

search for the deactivation of the hardware encryption for the driver "ath9k". "Backport-modules-jaunty" are for Ubuntu 9.04, which is outdated since 2010

---

### Post by iondoarion on 2012-04-16
> **praseodym said:**
> Hi,

search for the deactivation of the hardware encryption for the driver "ath9k". "Backport-modules-jaunty" are for Ubuntu 9.04, which is outdated since 2010

TY for your answer. I tried to do that but it seems that Ubuntu doesn't recognise any of the drivers, or at least when I try to look for it I just see the message about the fact that there are no proprietary drivers installed.
In the end I think I'll just install VMWare and learn Ubuntu this way. It's safer :)
So, I am going to mark this thread as un/solved :D

Thank you again for your help ;)

---

### Post by praseodym on 2012-04-16
Its just one line:

```
echo "options ath9k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9k.conf
```and reboot.

---

### Post by MarjaE on 2012-04-20
Okay, I was having the same problem. I used your suggested fix and now the connection's lighting-fast, but I'm wondering what issues might crop up? I assume that nohwcrypt is turning off some type of hardware cryptography?

---

### Post by praseodym on 2012-04-20
Its the hardware encryption of the driver. The software encryption (WPA/WPA2) is not affected by it.

---

### Post by MarjaE on 2012-04-26
I'm running into the same problem again.

---

### Post by praseodym on 2012-04-27
Check:
```

iwconfig
sudo iwlist scan
iwlist chan
dmesg | egrep 'ath|country'
```

---

