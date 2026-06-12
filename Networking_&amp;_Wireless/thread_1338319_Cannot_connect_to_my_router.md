---
title: "Cannot connect to my router"
date: 2009-11-26
forum: Networking &amp; Wireless
---

### Post by drascus on 2009-11-26
So here is the story bare with me it's a bit long. 

So I installed a wireless tether program on my Android phone and have been using it with my laptop. But then I went to connect to my home network and I can no longer connect to it with my laptop's card. However if I use an external wireless device I can connect to my wireless router. Further more I can connect to my phone tether no problem. 

I tried to delete the the networks from my memory and did a restart and went through the whole process of entering in my network keys and such and still no connection with my laptops card.

Any help would be appreciated...
I am running ubuntu 9.10
output of lspci
```
 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)

```

---

### Post by Iowan on 2009-11-26
Did */etc/network/interfaces* get modified? It should have only two lines defining "lo"

---

