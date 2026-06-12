---
title: "How do i switch off wlan0 (internal wireless-lappy)"
date: 2011-11-19
forum: Networking &amp; Wireless
---

### Post by dooper on 2011-11-19
Toshiba A210-12U lappy...

Have been running Ubuntu 10.04 LTS for a while with no issues.

Ran the upgrade to the latest Ubuntu 11.10? and now find that the internal Atheros pci card cannot be pursuaded to work properly. I have followed all the similar threads to no avail. My present solution is to use a plug in USB Zdas wirless dongle which works perfectly.

The only trouble is that the atheros connection dialogue pops up periodically asking for password etc but it doesnt really matter as it doesnt work anyway.

The internal PCI card is wlan0 and the usb dongle which works fine is wlan1.

How can i switch wlan0 off so that it stops pestering me ?

Ta

---

### Post by mikewhatever on 2011-11-20
Just blacklist the module by adding it to /etc/modprobe.d/blacklist.conf. To find out what the module is, run 'lsmod'.

---

### Post by chili555 on 2011-11-20
> the internal Atheros pci card cannot be pursuaded to work properly.The driver is probably either ath5k or ath9k. Add this line to the file /etc/modprobe.d/blacklist.conf:```
blacklist ath5k
```...or whichever it is.

---

### Post by dooper on 2011-11-23
Thanks..i blacklisted the ath5k module as suggested but it didnt work. I still have a situation in which the zydas and the atheros both try to connect. I then have to go to network manager and physically disconnect the atheros. Sometimes on the rare occasion that the atheros does connect, i then have limited or no throughput as they both fight with eachother !

It is a mystery to me that as soon as i upgraded to 11.10.i lost my wireless which worked fine before and that i keep getting the update manager with lots of updates and yet it seems like there are no fixes for one of the biggest problems with ubuntu..i.e that so many people are having big issues with wireless..

---

### Post by dooper on 2011-11-24
Final solution...i have flipped out the keyboard and removed the Atheros wireless module so that the only wifi hardware is now the Zydas usb dongle. Hopefully in a future realease of Ubuntu ,i will again be able to use the inbuilt wireless card as i am fed up of trying to fix it now.

---

### Post by dooper on 2011-11-25
Further...even though i have removed the wireless card,network manager still tries to connect to it for a period,gives up then connects using the Zydas usb modem. Originally the internal modem was wlan0 and the usb modem was wlan1.

Can i make the usb wlan0 so that the system will look for it first now that the internal card is missing?

---

