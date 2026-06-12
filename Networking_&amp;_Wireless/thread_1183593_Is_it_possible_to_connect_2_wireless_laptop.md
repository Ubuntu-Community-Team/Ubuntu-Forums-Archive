---
title: "Is it possible to connect 2 wireless laptop?"
date: 2009-06-10
forum: Networking &amp; Wireless
---

### Post by luciferleo on 2009-06-10
Hello buddies~ :p

I have two laptops both running ubuntu intrepid.
I know that we can connect a laptop to a router by typing command like

$ iwlist wlan0 scan
$ iwconfig wlan0 essid <AcessPoint> key <Key>


But I wonder what commands are necessary to connect 2 wireless laptop together without a router :KS

---

### Post by puppywhacker on 2009-06-10
when you run iwconfig you will see that the interface is in Access Point mode (Infrastructure) instead you can also put them in Ad Hoc-mode. You could also make one laptop to operate as AP, but I think you need extra software for that. I didn't try any myself so goodluck

---

### Post by superprash2003 on 2009-06-10
ad hoc mode is the best way to go..[https://help.ubuntu.com/community/WifiDocs/Adhoc](https://help.ubuntu.com/community/WifiDocs/Adhoc)

---

