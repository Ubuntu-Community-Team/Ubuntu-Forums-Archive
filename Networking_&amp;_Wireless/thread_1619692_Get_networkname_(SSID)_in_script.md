---
title: "Get networkname (SSID) in script"
date: 2010-11-12
forum: Networking &amp; Wireless
---

### Post by qsecofer on 2010-11-12
I am writing some scripts to synchronise directories between systems.
But depending on which network (SSID) I am connected I want to run different parts of the script. 
Todo this in need the SSID I am connected to. How do I get this name into my script

Thx

---

### Post by ankith13 on 2010-11-12
just try this command....

$iwconfig <wireless interface name> | awk '/ESSID/ { print $4 }'

Let me know if you have further problems...

Cheers!!

---

### Post by qsecofer on 2010-11-12
Thx ankith13 that did the trick.

---

