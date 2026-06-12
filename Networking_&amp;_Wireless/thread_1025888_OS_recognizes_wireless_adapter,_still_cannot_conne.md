---
title: "OS recognizes wireless adapter, still cannot connect"
date: 2008-12-30
forum: Networking &amp; Wireless
---

### Post by pennyb on 2008-12-30
I just started with linux today, I beg you, please bear with me.

Under my networking icon, Ubuntu is showing my wireless adapter (Intel Pro/Wireless 2011B 802.11b Adapter --ancient, I know). I've added the household wireless network.

I still cannot connect. I tried readding the drivers for the program and I am getting a "autorun cannot be found" or "an error occured while loading the archive (null) Command Line Output".

I am rather confused as to why it "sees" the adapter but cannot connect.
edit: I am running 8.10, the latest release.

---

### Post by Rohan Kapoor on 2008-12-30
> **pennyb said:**
> I just started with linux today, I beg you, please bear with me.

Under my networking icon, Ubuntu is showing my wireless adapter (Intel Pro/Wireless 2011B 802.11b Adapter --ancient, I know). I've added the household wireless network.

I still cannot connect. I tried readding the drivers for the program and I am getting a "autorun cannot be found" or "an error occured while loading the archive (null) Command Line Output".

I am rather confused as to why it "sees" the adapter but cannot connect.
edit: I am running 8.10, the latest release.
When you click on the network manager does it show a list of wifi networks in range?

---

### Post by pennyb on 2008-12-30
> **darth-vader said:**
> When you click on the network manager does it show a list of wifi networks in range?

No, it does not.

---

### Post by Rohan Kapoor on 2008-12-30
> **pennyb said:**
> No, it does not.
This means that the wireless adaptor is either not enabled (in Bios) or their are no drivers. Look in System->Administration->Hardware Drivers and install anything that comes up as not enabled.

Also check BIOS

---

