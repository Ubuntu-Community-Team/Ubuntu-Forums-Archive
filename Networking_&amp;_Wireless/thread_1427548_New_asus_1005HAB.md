---
title: "New asus 1005HAB"
date: 2010-03-11
forum: Networking &amp; Wireless
---

### Post by tyeshacade20 on 2010-03-11
HOW DO YOU GET THE WIRELESS TO WORK? kEEP ASKING ABOUT A NETWORK SECURITY KEY.

---

### Post by The Toxic Mite on 2010-03-11
> **tyeshacade20 said:**
> How do you get the wireless to work? It keeps asking about a network security key.
 
Hey! First of all, can you go to Applications > Accessories > Terminal, and type in the following commands:
 
```

sudo lshw -c network
iwconfig
lspci -v
dmesg

```
 
Post the outputs here when done :-)
 
-TTM-

---

