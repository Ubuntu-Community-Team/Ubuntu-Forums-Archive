---
title: "cant find wireless   on asus laptop  (9.04)"
date: 2009-11-12
forum: Networking &amp; Wireless
---

### Post by Kubaki on 2009-11-12
I cant find any wireless on my asus laptop. the network card is Atheros AR928X Wireless Network Adapter and it finds wireless fine in windows 7 but not in unbuntu.    I've tried installing a the driver on linux side and using mad-wifi hack.  My friends and I are totally clueless on what to do. Any suggestions?

---

### Post by Bunnybugs on 2009-11-12
There supposed to be a swich or button to enable WiFi... make sure that it's on when you boot up your PC... I have the switch next to the laptop lid button, and sometimes it switches of in the movement... then it takes hours to find WiFi again...

But when I boot up with the switch on, it finds WiFi in no-time... didn't even had to install a driver

---

### Post by Kubaki on 2009-11-12
> **Bunnybugs said:**
> There supposed to be a swich or button to enable WiFi... make sure that it's on when you boot up your PC... 




i've double checked this multiple times.

---

### Post by phishie on 2009-11-12
> **Kubaki said:**
> I cant find any wireless on my asus laptop. the network card is Atheros AR928X Wireless Network Adapter and it finds wireless fine in windows 7 but not in unbuntu.    I've tried installing a the driver on linux side and using mad-wifi hack.  My friends and I are totally clueless on what to do. Any suggestions?

Try using the drivers from the backports. I am using ASUS laptop as well. I had the same problem as you, this helped me:

*sudo apt-get install linux-backports-modules-jaunty*
[I] 
Reboot and retry.
[/I]

---

### Post by Bunnybugs on 2009-11-12
> **Kubaki said:**
> i've double checked this multiple times.

Weird...

Have you pressed right button on the WiFi in your system tray to enable WiFi

---

### Post by Bunnybugs on 2009-11-12
> **phishie said:**
> Try using the drivers from the backports. I am using ASUS laptop as well. I had the same problem as you, this helped me:

[I]sudo apt-get install linux-backports-modules-karmic

Reboot and retry.
[/I]


Tht's supposed to be
```
sudo apt-get install linux-backports-module-jaunty
```

At least, I guess... cause he says that he uses jaunty (9.04)

---

### Post by phishie on 2009-11-12
> **Bunnybugs said:**
> Tht's supposed to be
```
sudo apt-get install linux-backports-module-jaunty
```At least, I guess... cause he says that he uses jaunty (9.04)

Yeap, wasn't able to change it in time before you lol

---

### Post by Bunnybugs on 2009-11-12
lol, doesn't matter.... happens to everybody:P

They could make it easier for us to just call them all the same, but download it from a different repository:P

---

### Post by Kubaki on 2009-11-12
```
sudo apt-get install linux-backports-module-jaunty
```Responded with   
INVALID OPERATION install linux-backports-module-jaunty



eh well I'm healding  to bed i'll post in the morning if any new suggestions pop up.
its an Asus netbook G72gx

---

### Post by Bunnybugs on 2009-11-12
> **Kubaki said:**
> ```
sudo apt-get install linux-backports-module-jaunty
```Responded with   
INVALID OPERATION install linux-backports-module-jaunty



eh well I'm healding  to bed i'll post in the morning if any new suggestions pop up.
its an Asus netbook G72gx


Ah, been looking on the net... and found this: [http://linuxwireless.org/en/users/Download](http://linuxwireless.org/en/users/Download)

```
sudo apt-get install linux-backports-modules
```

---

