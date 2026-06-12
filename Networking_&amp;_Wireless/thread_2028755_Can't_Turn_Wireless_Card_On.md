---
title: "Can't Turn Wireless Card On"
date: 2012-07-18
forum: Networking &amp; Wireless
---

### Post by oryza on 2012-07-18
I am trying to use 32 bit ubuntu 10.04.4 LTS which was installed using wubi. Upon starting up my wireless card powers off as indicated by an LED on my keyboard and I am unable to turn it back on. I previously installed a 64 bit version but ran into the same problem. I have a Realtek RTL8188CE Wireless LAN 802.11n COMBO PCI-E NIC.

The physical key combination has no effect and it appears that ubuntu is unable to detect any wireless card. Can anyone help with this?


Edit: I cannot use 12.04 because it overheats my computer seconds after I log in and the program I need ubuntu to run only supports 10.04.4

Edit2: I've never used linux before today so I'm generally unfamiliar with it

---

### Post by robtygart on 2012-07-18
Go to System Settings> Additional Drivers, see if its on the list.

Welcom to Ubuntu Forums!

---

### Post by oryza on 2012-07-18
I can't find System Settings > Additional Drivers.

The closest thing I can get to is System > Administration > Hardware Drivers, which first gives me an error for not having access to the internet then gives empty boxes.

---

### Post by oryza on 2012-07-19
bump

---

### Post by oryza on 2012-07-19
i can't be the only person having this problem

does anyone know how to fix it?

---

### Post by steeldriver on 2012-07-19
Hi unfortunately there are lots of things that can break wireless

Can you open a terminal and type the following and post back the results

```

rfkill list

lshw -c network

lspci -nn

iwconfig

```

---

