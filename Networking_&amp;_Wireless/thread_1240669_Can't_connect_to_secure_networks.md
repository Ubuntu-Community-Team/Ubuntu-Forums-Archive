---
title: "Can't connect to secure networks"
date: 2009-08-14
forum: Networking &amp; Wireless
---

### Post by DoT. on 2009-08-14
I am running ubuntu 9.04. i am able to connect to unsecure networks but not secured WEP networks. i have searched and have found nothing except updating my firmware-iwlwifi?? what else can i do?

---

### Post by john stiles on 2009-08-15
There are many possible weak links with wireless. Double check the fundamentals with this check list first.

[WirelessTroubleShootingGuide]("https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide")

---

### Post by Wiebelhaus on 2009-08-15
Our amazing source for everything Ubuntu , Our Great friends over at Ubuntu Geek may be able to help you with [this awesome how to.]("http://www.ubuntugeek.com/how-to-troubleshoot-wireless-network-connection-in-ubuntu.html")

---

### Post by john stiles on 2009-08-15
After that move onto this

[https://help.ubuntu.com/community/WifiDocs/WiFiHowTo]("https://help.ubuntu.com/community/WifiDocs/WiFiHowTo")

and check out anything peculiar for your wireless chipset from here:

[WirelessCardsSupported]("https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported")

I hope you will have uncovered the source of your problem well before reading all that lot. Worst case scenario you will be qualified to write this note.

---

### Post by superprash2003 on 2009-08-15
what error do you face when connecting to WEP networks?? does it repeatedly ask for your WEP Key?

---

### Post by DoT. on 2009-08-15
> **superprash2003 said:**
> what error do you face when connecting to WEP networks?? does it repeatedly ask for your WEP Key?

yes yes

i'm running an atheros AR242x

---

### Post by DoT. on 2009-08-16
bump

---

### Post by w_1_n_d on 2009-08-16
Man same problem here. i'm also using an atheros 5006ex card, it keeps on asking for a wep key.

---

### Post by superprash2003 on 2009-08-17
when the password box pops up , have you tried all the various possible authentication types like 64bit, 128bit etc ?

---

### Post by DoT. on 2009-08-17
yes

---

### Post by Modie101 on 2009-09-20
Guys, has anybody solved this yet? I can't for the life of me connect to a my home network. I discovered three things so far:
1- Atheros cards suck for linux, 
2- Static IP configurations make knetworkmanager go nuts
3- WEP doesn't work for Atheros wireless cards (or even ethernet wired connections) while running Wicd or knetworkmanager

I need help. I know my card works because I can connect to a DHCP unsecured network, but the second I try to connect to my home network with my WEP key it fails after a few seconds. I even installed the madwifi Atheros driver for Wicd. 

It still doesn't work. Any ideas?

---

### Post by tyqre on 2009-09-20
I had the same problem but then i changed my security to WEP2 (AES) and i reset my router and i connected with no problem.

---

