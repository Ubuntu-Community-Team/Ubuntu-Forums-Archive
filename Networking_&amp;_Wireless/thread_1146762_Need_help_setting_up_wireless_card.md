---
title: "Need help setting up wireless card"
date: 2009-05-02
forum: Networking &amp; Wireless
---

### Post by kakarotman on 2009-05-02
I just installed ubuntu version 2.6.27-7-generic and i do not have access to the internet in any way from this computer however i can access the internet from another computer so if there is any thing i need to download it will have to be transfered via usb. more info:

computer: toshiba sattelite a215-s5837
wireless driver: Atheros Wireless LAN (802.11b/g) 


Thanks for your help!

---

### Post by Headbanger2510 on 2009-05-02
go to system -> administration -> hardware drivers and enable your wireless card

---

### Post by Headbanger2510 on 2009-05-02
if that doesn`t work then try with this file first type in the terminal:
sudo chmod +x madwifi.sh

the type:
sudo ./madwifi.sh

and that`s it.

---

### Post by kakarotman on 2009-05-02
I did what you said and got this:

josh@JoshW:~$ sudo chmod +x madwifi.sh
josh@JoshW:~$ sudo ./madwifi.sh
Found at least one Atheros device.
Checking build dependencies...
No packages found matching subversion.
Installing subversion...E: Couldn't find package subversion
josh@JoshW:~$

---

### Post by Headbanger2510 on 2009-05-03
seems like you don`t have all repos enabled, so go to synaptic, eneble all the repos, reload the package list and search for subversion in synaptic and install it, and then do again:
sudo ./madwifi.sh

---

