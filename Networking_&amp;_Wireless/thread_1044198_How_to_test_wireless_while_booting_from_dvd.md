---
title: "How to test wireless while booting from dvd?"
date: 2009-01-19
forum: Networking &amp; Wireless
---

### Post by mid_life_crisis on 2009-01-19
I have a Gateway laptop currently running Vista Home Premium.  I don't think any of that really matters, but just in case...
I am trying to test Ubuntu by booting and running off of the dvd.
The problem is that I use a wireless connection at home and for the life of me I cannot get the thing working.  It appears (hard to tell, I don't know what I'm doing in Ubuntu) that there is no driver installed for my wireless adapter.  How can I install a driver when the OS is not writing to my hard drive?  I have a real Catch 22.  It appears that I cannot get the wireless to work without installing the OS, but I'm not going to install the OS if I cannot get the wireless to work.

---

### Post by Tim Sharitt on 2009-01-19
Do you know the chipset of your wireless card?

You may be able to fine out by opening a terminal (Applications->Accessories->Terminal) and entering:

```
lspci | grep Network
```

---

### Post by mid_life_crisis on 2009-01-19
> **Tim Sharitt said:**
> Do you know the chipset of your wireless card?

You may be able to fine out by opening a terminal (Applications->Accessories->Terminal) and entering:

```
lspci | grep Network
```

Unfortunately, I am at work now and my laptop is at home.  I'll check that this evening.

---

### Post by mid_life_crisis on 2009-01-19
> **Tim Sharitt said:**
> Do you know the chipset of your wireless card?

You may be able to fine out by opening a terminal (Applications->Accessories->Terminal) and entering:

```
lspci | grep Network
```

Broadcom 802.11g

---

### Post by mid_life_crisis on 2009-01-20
Broadcom BCM4311
It doesn't appear to be running. 
If I check network connections the panel does not search for available networks.

---

