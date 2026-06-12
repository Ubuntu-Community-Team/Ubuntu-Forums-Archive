---
title: "Auto run script whenever interface connection state changes"
date: 2010-08-14
forum: Networking &amp; Wireless
---

### Post by bsgcic on 2010-08-14
Upon boot of my system, I auto run a script that customizes the routing table (i.e., route -n).
However, after the system is already booted up and has been running, if a network connection is dropped and re-added, like if one of the several network cables to the machine is temporarily disconnected or other, then the routing table is modified -- I assume by network manager. Presently, I need to manually re-run my script to re-customize the routing table.

I would like to have the script just run whenever there is any change to the connection state of interfaces. Anyone know how to tie in some kind of event trigger that can execute a script upon change in interfaces connection state (i.e., detect change in connection state and run the script)?

Thanks!!

---

### Post by chopinhauer on 2010-08-15
> **bsgcic said:**
> 
I would like to have the script just run whenever there is any change to the connection state of interfaces. Anyone know how to tie in some kind of event trigger that can execute a script upon change in interfaces connection state (i.e., detect change in connection state and run the script)?


The scripts in */etc/network/if-up.d* and *if-pre-up.d* are run whenever an interface goes up. When NetworkManager fiddles with interfaces, the scripts in */etc/NetworkManager/dispatcher.d* are also executed (and there is one script to assure ifupdown compatibility).

---

### Post by bsgcic on 2010-08-15
chopinhauer - thanks a bunch!!

---

