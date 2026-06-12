---
title: "Xubuntu failing to connect to wirelss network"
date: 2009-02-17
forum: Networking &amp; Wireless
---

### Post by darkvampire on 2009-02-17
I have two Xubuntu laptops and one Windows Vista laptop.

One of the Xubuntu laptops however when I try to connect displays a message saying "The network connection has been disconnected" before it even has chance to connect.

I know it is not my Internet because Vista & the other Xubuntu works fine.

Any idea on what the problem is?

Thank you for your help. ;)

---

### Post by GepettoBR on 2009-02-17
We need a little more information. What model is the wireless card? Is the netwrok password-protected? Is it WEP or WPA?

---

### Post by crazyness003 on 2009-02-18
actually, dont rule out the possibility that there is hardware damage. The un-connective laptop may be experiencing what I currently am. I have an HP Pavilion tx1308nr ("tablet" pos) that is currently having troubles with the mobo. Thus affecting my wifi. Sometimes my wirless card isint even recognized as an installed piece of hardware. (but that an entirely different story).

Also, drivers may be the culprit.

Have you been able to connect this laptop to your network in the past?
if so, what changes have been made (if any)?
and have you tried booting into another OS to see if the problem persists?

---

### Post by darkvampire on 2009-02-18
> **GepettoBR said:**
> We need a little more information. What model is the wireless card? Is the network password-protected? Is it WEP or WPA?
Model: Micronet SP908GK
No protection.

> **crazyness003 said:**
> actually, dont rule out the possibility that there is hardware damage. The un-connective laptop may be experiencing what I currently am. I have an HP Pavilion tx1308nr ("tablet" pos) that is currently having troubles with the mobo. Thus affecting my wifi. Sometimes my wirless card isint even recognized as an installed piece of hardware. (but that an entirely different story).

Also, drivers may be the culprit.

Have you been able to connect this laptop to your network in the past?
if so, what changes have been made (if any)?
and have you tried booting into another OS to see if the problem persists?

I have been able to.
Nothing, just stopped 20 minutes into a fresh install.
Vista was fine with it. 

Thank you ;)

---

### Post by GepettoBR on 2009-02-18
I Googled the chipset for your Micronet SP908GK and found a Ralink RT2500 chipset. That's good, because Ralink drivers work perfectly on Linux-based systems, but it seems that this chipset is only used on SP908GK V3 models. If you can figure out the version number, and it is V3, you can download the driver from [here](http://rt2x00.serialmonkey.com/wiki/index.php/Downloads).

I don't mean to say that your issue is certainly driver-related, but it might be, and if it is, this is the fix.

---

### Post by darkvampire on 2009-02-18
> **GepettoBR said:**
> I Googled the chipset for your Micronet SP908GK and found a Ralink RT2500 chipset. That's good, because Ralink drivers work perfectly on Linux-based systems, but it seems that this chipset is only used on SP908GK V3 models. If you can figure out the version number, and it is V3, you can download the driver from [here](http://rt2x00.serialmonkey.com/wiki/index.php/Downloads).

I don't mean to say that your issue is certainly driver-related, but it might be, and if it is, this is the fix.

How do I go about installing this? Thankyou.

---

### Post by darkvampire on 2009-02-18
> **GepettoBR said:**
> If you can figure out the version number,.

How would I do that too?

---

### Post by GepettoBR on 2009-02-18
> **darkvampire said:**
> How do I go about installing this? Thankyou.

> **darkvampire said:**
> How would I do that too?
The version number is usually written somewhere on the device. I'm sorry I can't help you with that, but it should be easy to find.

To install the driver, extract the archive you downloaded, navigate to its Modules/ directory in a terminal, and type ```
make
sudo make install
sudo modprobe rt2500
```

---

### Post by darkvampire on 2009-02-18
> **GepettoBR said:**
> The version number is usually written somewhere on the device. I'm sorry I can't help you with that, but it should be easy to find.

To install the driver, extract the archive you downloaded, navigate to its Modules/ directory in a terminal, and type ```
make
sudo make install
sudo modprobe rt2500
```

Thank you very much for your help & effort ;);
Although I discovered that it was not the drivers and when I removed another PCI device it connected.

I'm presuming there was some conflict :D

Thanks again :):)

---

