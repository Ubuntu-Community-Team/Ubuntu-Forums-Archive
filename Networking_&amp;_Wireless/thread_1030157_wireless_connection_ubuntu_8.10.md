---
title: "wireless connection ubuntu 8.10"
date: 2009-01-04
forum: Networking &amp; Wireless
---

### Post by azedddine on 2009-01-04
good morning everybody

running ubuntu 8.10 on a notebook and live mode (not installed yet), i can't get the wifi connection. i have (Realtek RTL8187B Wireless 802.11b/g 54Mbps USB 2.0 Network Adapter) as network card.
is it normal? i mean, ubuntu 8.10 must be installed to get the wireless connection or there is a problem with the network card (driver)

thank you

---

### Post by Tim Sharitt on 2009-01-04
Your wireless card ip probably missing a driver and/or driver firmware. 
Post the output of 
```
lshw -C network
```
and 
```
lsusb
```

---

### Post by azedddine on 2009-01-04
he detect networks but when i open mozila, i can't enter or navigate.

---

### Post by riddz on 2009-01-04
oops sorry wrong place

---

### Post by wkuace on 2009-01-04
i got mine to work in live and i have the same card. i'm using a gateway t-1628 laptop. However i'm now using wubi it worked good for a few days and my internet stoped working just a few hours ago. it couldn't connect to internet(i also still detected signal strength). I switched to vista and had the same problem. went back to ubuntu and internet worked?? I downloaded the windows wifi card driver onto a flash drive and went back to windows and reinstalled. after a reboot. internet works in windows but ubuntu won't boot now because of some error with the usb (where the wireless is installed). i think i can fix mine with a wubi reinstall.

if you've still got windows or whatever my guess would be try the driver reboot and then the live cd after windows has restarted and shutdown. however i'm still new to ubuntu so i'm just going with my personal experince and i'm still not fixed yet.just to late at night to reinstall wubi.

if you have 8+ free gigs of hd you can try wubi its faster then the live cd and you can download flash for a better internet, personalize, etc.

---

