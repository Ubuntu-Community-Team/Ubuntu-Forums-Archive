---
title: "Linksys N300 Model AE1200-NP"
date: 2013-05-21
forum: Networking &amp; Wireless
---

### Post by lmac009 on 2013-05-21
I just recently started using ubuntu and ever things going find except I cant get my wireless adapter to work its a Linksys N300 Model AE1200-NP im using it on a desktop and i can even get the install cd to work could some one please help.

---

### Post by chili555 on 2013-05-22
Please open a terminal Ctrl+Alt+t and run and post:```
lsusb
```Can you obtain a temporary wired ethernet connection if we need to download a few things?

---

### Post by lmac009 on 2013-05-23
ok and yes i can

---

### Post by chili555 on 2013-05-23
> **lmac009 said:**
> ok and yes i canMay we see the result of :```
lsusb
```We need that in order to proceed.

---

### Post by lmac009 on 2013-05-24
Bus 001 Device 002: ID 13b1:0039 Linksys AE1200 802.11bgn Wireless Adapter [Broadcom BCM43235]
Bus 001 Device 003: ID 054c:0439 Sony Corp. 
Bus 005 Device 002: ID 046d:c52e Logitech, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

---

### Post by lmac009 on 2013-05-24
sorry taking so took so long sharing wired connection with four others had to wait for spot to open up

---

### Post by praseodym on 2013-05-24
This device needs ndiswrapper and the respective cisco driver

[http://homesupport.cisco.com/en-us/support/adapters/AE1200](http://homesupport.cisco.com/en-us/support/adapters/AE1200)

You can download drivers for XP, Vista and W7 there.

---

### Post by lmac009 on 2013-05-25
ok thank you

---

### Post by chili555 on 2013-05-25
> **lmac009 said:**
> ok thank youNdiswrapper requires the *XP* driver.

---

### Post by lmac009 on 2013-05-27
i cant get ndiswrapper to work

---

### Post by chili555 on 2013-05-28
> **lmac009 said:**
> i cant get ndiswrapper to workWhat messages do we have?```
ndiswrapper -l
sudo modprobe ndiswrapper
dmesg | grep ndis
```

---

