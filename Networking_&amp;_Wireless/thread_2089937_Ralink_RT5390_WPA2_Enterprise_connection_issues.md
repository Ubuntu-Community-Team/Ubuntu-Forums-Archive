---
title: "Ralink RT5390 WPA2 Enterprise connection issues"
date: 2012-11-30
forum: Networking &amp; Wireless
---

### Post by C0MM4NDER on 2012-11-30
Hi there,

I have a HP G62 with a Ralink 5390 wifi card. However i got few issues.

First one is that i cannot connect to my eduroam network at my school. Using the settings i get provided by eduroam NetworkManager just tries to connect and then de-auths me with the reason local choice 3. And then asks for password again and it keeps doing that round and round.

When it asks me about a certificate i just press ignore since I know that their network does not need it. However I tried their open un-encrypted network and i got issues connecting to it too with the same error. Retries 3 times then fails, times out and then the local choice 3 error.

I also got power issues with the card and running with power off setting in iwconfig. It also cannot connect to a network if it fails couple of times and i need to enable/disable with rfkill/button

Tried talking with the IT-Techs at the University but they have no idea why my card does what it does and im guesing this is a driver issue or a NetworkManager bug.

Im running latest Ubuntu 12.10, had this issue under Arch Linux aswell if that helps you something.


If you have any idea what i can do to fix this issue or atleast workaround it please tell. I also tried TP LINK nano usb wifi, it can connect to the open network at the school but only if i insert it after booting up and it will do it only once, any other tries it enters the endless loop of connecting/disconnected thing.

Best Regards

---

### Post by C0MM4NDER on 2012-12-03
not a soul?

---

### Post by biljkus on 2012-12-05
I have the same problem.

---

### Post by C0MM4NDER on 2013-02-01
Hm still nothing, lurked the webs and irc channels but still no solution to this...

---

### Post by kurt18947 on 2013-02-01
Have you tried WiCD  after uninstalling Network Manager?  That has worked for some people though I don't know specifically about the RT5390.  Will the RT5390 connect to an unsecured network?  Another thought though not optimum would be a USB adapter known to work.

---

