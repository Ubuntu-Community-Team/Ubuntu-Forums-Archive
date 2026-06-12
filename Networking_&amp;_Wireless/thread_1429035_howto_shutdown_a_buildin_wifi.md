---
title: "howto shutdown a buildin wifi"
date: 2010-03-13
forum: Networking &amp; Wireless
---

### Post by PaulNL on 2010-03-13
I have a acer laptop with a buildin WiFi now i wan't to use a pcmania WiFi modem but when i connect it i get both modems who connect to the network.

One modem is wlan0 and the other one is wlan1

How do i shutown mu wlan0 permanent i can turn it off with iwconfig wlan0 down but when i start up it is up again

How do i shut is off

---

### Post by Iowan on 2010-03-14
Have you checked BIOS to see if wireless card can be disabled there?

---

### Post by PaulNL on 2010-03-14
I can't shut it down in the bios so i have to do it with Ubuntu I have a swith on the laptop but than both going off

---

### Post by jiggz88 on 2010-03-14
little dangerous but if you really and truly want to turn it off every time you start the laptop, you could put it in "/etc/.rc", and then it would run that "iwconfig wlan0 down" every time until you removed or commented it out in the file. But I'd wait for more advice before resorting to that.

---

### Post by Iowan on 2010-03-15
Another "dirty" option (quick/dirty - without the quick...) is to define it in */etc/network/interfaces* but leave out either the "auto" line or the "iface" line (or define it as "manual" instead of DHCP or static).

---

