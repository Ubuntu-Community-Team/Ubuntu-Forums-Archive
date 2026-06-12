---
title: "EEEPC 701 with 10.10, wireless not connecting"
date: 2011-02-05
forum: Networking &amp; Wireless
---

### Post by Samabula on 2011-02-05
The wireless on this machine worked fine with ubuntu-9.10-netbook-remix. With ubuntu-10.10-netbook, Maverick, the machine sees the wireless router but does not connect. (iwlist scan shows the router)I have tried:
  sudo apt-get install linux-backports-modules-wireless-maverick-generic
   
  Any other ideas?
   
  Eeepc701, Atheros AR5001 wireless network adapter.
  driver=ath5k driverversion=2.6.35-25-generic

---

### Post by jobdone on 2011-03-05
I'm unsure if you've fixed this , but I'm just about to try 10.10 on my 701 but I'm assuming that it might need nohwcrypt fix as it's atheros.

---

### Post by Frankiewizard on 2011-05-02
This happend to me once on a Éee-Pc 701 using 10.10 I found the problem it was in the BIOS the wireless conection was not activated.

I hope that this will be of help.
Regards..................

---

