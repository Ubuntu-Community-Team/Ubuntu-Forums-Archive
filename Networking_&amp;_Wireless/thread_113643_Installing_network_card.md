---
title: "Installing network card"
date: 2006-01-06
forum: Networking &amp; Wireless
---

### Post by hockeyk242 on 2006-01-06
Im new with Ubuntu and i was wondering how to install a Linksys wireless G notebook adapter.

---

### Post by healychan on 2006-01-06
What is your card model ?? Some wireless card work fine without any configuration, however, most of the card need some work......

---

### Post by hockeyk242 on 2006-01-08
my model number is WPC54G

---

### Post by Lambert on 2006-01-08
You need to use an app called ndiswrapper which basically makes the windows drivers work in linux.

See link for ndiswrapper in my signature.

---

### Post by hockeyk242 on 2006-01-09
thanks for the help

---

### Post by hockeyk242 on 2006-01-10
i tried following the directions on the link that u provided, but i couldn't get it to work, everytime that i tried to check to see if the driver was installed, it said that it wasn't there and i followed all of the steps.

---

### Post by healychan on 2006-01-10
Your card is WPC54G but which version???? What is the chipset???? Made in which country???? All these information are needed to identify your card.

We cannot help without those information...........

please post result of
```
lspci | grep Ethenet
```

---

### Post by hockeyk242 on 2006-01-10
the version is v.1, chipset is Broadcom BCM94306 and was made in taiwan. is that all that u need or anything else?

---

### Post by healychan on 2006-01-10
I find your card in the ndiswrapper list and ndiswrapper does support your card. Just to confirm one thing is the pclid. Do this
```
lspci | grep 14E4:4320
```
If you can see your card, then you will be OK. Let me know the result.

Have you install ndiswrapper?? Get it if you haven't.

---

