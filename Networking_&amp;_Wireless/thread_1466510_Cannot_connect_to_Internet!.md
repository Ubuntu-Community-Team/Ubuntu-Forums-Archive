---
title: "Cannot connect to Internet!"
date: 2010-04-30
forum: Networking &amp; Wireless
---

### Post by police512 on 2010-04-30
Hi, i don't know if i should of put this in either Networking or Dell Forum. But here goes. I have a Dell Studio 1535 Laptop, and i have downloaded the new ubuntu 10.04

The problem is, is that i cannot get a internet connection. On my laptop there is a wifi sign that lights up if it works, and it didnt when i booted it. So i thought i have the driver downloaded and i tried to install it and it installed but after it crashes, so that failed. And then i tried via Ethernet and it does not connect when i connect it to the router!. It just says disconnected everytime :(.

I have tried to reboot, just incase it was a bad boot or something, and i stil get the same. It just will not connect to the internet :confused: Any Help? or anyone having this same problem...

---

### Post by NichoTL on 2010-04-30
> **police512 said:**
> Hi, i don't know if i should of put this in either Networking or Dell Forum. But here goes. I have a Dell Studio 1535 Laptop, and i have downloaded the new ubuntu 10.04
 
The problem is, is that i cannot get a internet connection. On my laptop there is a wifi sign that lights up if it works, and it didnt when i booted it. So i thought i have the driver downloaded and i tried to install it and it installed but after it crashes, so that failed. And then i tried via Ethernet and it does not connect when i connect it to the router!. It just says disconnected everytime :(.
 
I have tried to reboot, just incase it was a bad boot or something, and i stil get the same. It just will not connect to the internet :confused: Any Help? or anyone having this same problem...
 
Sorry for sounding silly but for most laptops, the wifi signs that lights up comes with a button to switch wifi on or off.
 
Otherwise you can start by running the lspci command (I am assuming it's a PCI card).

---

### Post by police512 on 2010-04-30
> **NichoTL said:**
> Sorry for sounding silly but for most laptops, the wifi signs that lights up comes with a button to switch wifi on or off.
 
Otherwise you can start by running the lspci command (I am assuming it's a PCI card).

Thanks for the reply, but the button is always switched on. Its a broadcom or something its the Dell Wlan 1397 mini card or something.

---

### Post by bkratz on 2010-04-30
> **police512 said:**
> Thanks for the reply, but the button is always switched on. Its a broadcom or something its the Dell Wlan 1397 mini card or something.

You might want to do the following:

```
lspci -vnn | grep 14e4
```

( that is LSPCI in lowercase)

and see which Broadcom device is used (probably pci-id 14e4:4315) then go to 

[http://linuxwireless.org/en/users/Drivers/b43#Known_PCI_devices](http://linuxwireless.org/en/users/Drivers/b43#Known_PCI_devices)

for instructions. See the section labeled "ubuntu/Debian"

---

### Post by police512 on 2010-04-30
> **bkratz said:**
> You might want to do the following:

```
lspci -vnn | grep 14e4
```

( that is LSPCI in lowercase)

and see which Broadcom device is used (probably pci-id 14e4:4315) then go to 

[http://linuxwireless.org/en/users/Drivers/b43#Known_PCI_devices](http://linuxwireless.org/en/users/Drivers/b43#Known_PCI_devices)

for instructions. See the section labeled "ubuntu/Debian"

Thanks for you'r help. I can't get internet even when i plug it into the router via ethernet ? i dont get it!.

I am just about to try that now. But i cannot get internet so whats the point in me trying to download it when i cant!:lolflag:

---

### Post by bkratz on 2010-04-30
> **police512 said:**
> Thanks for you'r help. I can't get internet even when i plug it into the router via ethernet ? i dont get it!.

I am just about to try that now. But i cannot get internet so whats the point in me trying to download it when i cant!:lolflag:




This one tells you how to do it, even with no wired connection.

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

Look about 2/3 the way down.

---

### Post by sathishkumaras on 2010-05-02
hi buddy,
                Yesterday i download new ubuntu 10.04.i install that install inside windows method.after that i cant connect to internet thru ethernet.so pls help me how to connect internet in ubuntu 10.04.waitin 4 ur reply...............

---

### Post by pdc on 2010-05-02
Hi sathishkumaras; welcome to ubuntu

the normal rules of forums like this are that you do NOT post on the end of someone else's message;

so you need to start your own post: then you will get better attention

---

