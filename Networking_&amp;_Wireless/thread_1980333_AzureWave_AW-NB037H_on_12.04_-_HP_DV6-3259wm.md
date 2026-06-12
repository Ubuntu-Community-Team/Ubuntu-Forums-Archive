---
title: "AzureWave AW-NB037H on 12.04 - HP DV6-3259wm"
date: 2012-05-15
forum: Networking &amp; Wireless
---

### Post by noahkeller on 2012-05-15
Hello, first off, sorry if this is a repost, couldn't find anything on Google, or forum search.

HP Pavilion DV6-3259wm
Ubuntu 12.04

So I bought an AzureWave AW-NB037H WiFi/BlueTooth combo card, to add BT capability to my laptop. The WiFi chipset in the card is AR-9285 and the BT chipset is AR-3011. When I connect the card, it lists the bluetooth chipset in lsusb, but does not list the WiFi card in lspci.

What is strange is, the current wifi card I am using has the AR-9285 chipset. Here is the lspci of with my old card (installed now):

> 
...
02:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
Again, it does not list anything with lspci with the AW-NB037H card installed, but lists the bt chipset under lsusb. Another strange thing, the current card has printed on it: AR-5B95, not AR-9285 which is what it shows as on the system (in both lspci, and when I click the wireless icon)

I don't know what I am doing (needless to say :P) so if anyone could point me in the right direction as to what to do next?

Thanks for the help.
-Noah

---

### Post by chili555 on 2012-05-16
I noticed this fell down an entire day with no answer and I've been reading your post with some confusion. First of all, I don't see what problem you're trying to solve. Are you trying to get the wireless part of the new card to work and disable the built-in? Or...what? > the current card has printed on it: AR-5B95, not AR-9285 which is what it shows as on the system (in both lspci, and when I click the wireless icon)That doesn't mean a thing. Lots of mysterious numbers get stamped on cards for various reasons at the factory. In some cases, although they are manufactured by Company A, the chip will be sold by a second party, for instance Company B (AR-5[COLOR="Red"]B[/COLOR]95??). In other cases, parts are marked differently for sale in foreign countries where wireless channel availability is different.

So what can we help you do? Please run and post:```
lspci -nn
lsusb
```

---

