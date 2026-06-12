---
title: "Warning re Realtek wireless cards &amp; WEP"
date: 2010-06-13
forum: Networking &amp; Wireless
---

### Post by williamblue on 2010-06-13
I recently purchased two MSI Windtop AE2220's. One for my home which uses a router with WPA2 protection and one for my office where I use WEP encryption.

The Realtek internal wireless card will not connect to a WEP router if you are running Ubuntu Lucid Lynx 10.04.  I have exhausted all suggestions on this site and all drivers found at Realtek's site.

I have been using Ubuntu since Hardy Heron, but sadly, painfully, I have had to install Windows 7 on my office machine until I find a wireless card compatible with the MSI Windtop AE2220, Lucid and WEP.

---

### Post by williamblue on 2010-06-13
Also, the Realtek wireless card will connect to WEP if you are running Windows.

---

### Post by tonyps on 2010-06-14
Afternoon,

I am using: Realtek 8192e wireless on my Toshiba and connect to a NetGear router at home, using WEP, with out any issues.
Well, maybe one, I cannot use the higher 128 pass phrase, however the 40/128 bit key works fine.
Are you using ndsiwarapper driver or Linux driver?

Tony ...

---

### Post by williamblue on 2010-06-14
We have tried using both.  No real luck with either one. Lucid has a nasty habit of not seeing the wireless card at random (mostly inconvenient) times as well. Intitally we had the issue of the wireless card working fine, other than not being able to connect to our 128 phrase.

---

### Post by pdk on 2010-06-26
Same problem using ndiswrapper with rta2500. Have to disable WEP to get a connection on lucid.

---

### Post by v.d.merwe@gmail.com on 2010-07-12
All worked fine and then stopped working all of a sudden.

I can Scan the network, find the AP but cannot connect to it. Anyone know where I can check logs i.r.o. Wireless Ethernet?

---

