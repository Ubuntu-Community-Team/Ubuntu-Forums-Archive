---
title: "madwifi patch"
date: 2005-12-30
forum: Networking &amp; Wireless
---

### Post by PeRy_SoY on 2005-12-30
Hi! i am trying install madwifi driver with patch for mode monitor in atheros chipset, but when i try modprobe ath_pci, this module no found.
Anybody can sayme a how to patch madwifi pls

Sorry for my lexic, my english isnt very well :p

thx 4 helps!!!

---

### Post by Lambert on 2005-12-30
I don't  believe you have to patch in breezy.

ubuntu uses madwifi-old driver so follow the instructions here under the old code section.

[http://madwifi.org/wiki/UserDocs/MonitorMode](http://madwifi.org/wiki/UserDocs/MonitorMode)

---

### Post by PeRy_SoY on 2005-12-30
hi! i have installed madwifi drivers with the wiki madwifi (ubuntu page) and when i do

sudo iwconfig ath0 mode monitor channel 02

Error for wireless request "Set Mode" (8B06) :
    SET failed on device ath0 ; Invalid argument.

thx 4 helps!

---

### Post by Lambert on 2005-12-30
did you try just entering 2 and not 02

---

### Post by PeRy_SoY on 2005-12-31
nothing.... 

sudo iwconfig ath0 mode monitor channel 2
Error for wireless request "Set Mode" (8B06) :
    SET failed on device ath0 ; No such device.


thx 4 helps!!!

---

### Post by Lambert on 2005-12-31
Reading those instructions on that link I'm wondering if the last line needs to be run first. It looks like the interface is not active/up so when the iwconfig command is run there's no interface that matches.

So try it in  this order.

```
sudo ifconfig ath0 up
```
```
sudo iwpriv ath0 mode 2
```
```
sudo iwconfig ath0 mode monitor channel 2
```

---

### Post by PeRy_SoY on 2005-12-31
I try in this order but nothing, thx all 4 helps.
I think that i need apply a patch for madwifi to monitor mode, but i tried patching madwifi, but when i did:

sudo iwconfig ath0 mode monitor

correcty but when:

sudo iwlist ath0 scan
(Error): segment violation

SOrry 4 my english, thereisnt well :p

thx 4 helps!!

---

### Post by Lambert on 2005-12-31
If you use irc go to irc.freenode.net and madwifi has a channel there

#madwifi

you can find help there.

---

