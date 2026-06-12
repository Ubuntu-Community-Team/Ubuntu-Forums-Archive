---
title: "Atheros A9285 terribly slow on Ubuntu 10.04"
date: 2012-02-06
forum: Networking &amp; Wireless
---

### Post by adashiu on 2012-02-06
I made a decision to switch to Ubuntu completely. I am let's say a bit familiar with Ubuntu. After few hours spent on configuring NVIDIA drivers and brightness, now I have another problem with my Sony Vaio VPCCW21FX.

With my Ahtheros A9285 my wireless connection is terribly slow and there are packet loss. Speedtest.net gives me 6Mbps whereas in Wind 7 it is 16Mbs.

What Can I do with it ? I cannot find a solution. Please help me.

```

02:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
	Subsystem: Foxconn International, Inc. Device e017
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at e7a00000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: [40] Power Management version 3
	Capabilities: [50] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
	Capabilities: [60] Express Legacy Endpoint, MSI 00
	Capabilities: [100] Advanced Error Reporting <?>
	Capabilities: [140] Virtual Channel <?>
	Capabilities: [160] Device Serial Number 12-14-24-ff-ff-17-15-00
	Capabilities: [170] Power Budgeting <?>
	Kernel driver in use: ath9k
	Kernel modules: ath9k

```

```
adam@adam-laptop:~$ lspci | grep "9285"
02:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)

```

---

### Post by praseodym on 2012-02-06
Hi,

you can update the driver via

```
sudo apt-get install linux-backports-modules-wireless-$(uname -r)
```
and reboot. If the system is up-to-date you should install the metapackage instead/additionally:

```
sudo apt-get install linux-backports-modules-wireless-lucid-generic
```

---

### Post by adashiu on 2012-02-06
Thanks for reply !

```

adam@adam-laptop:~$ sudo apt-get install linux-backports-modules-wireless-$(uname -r)
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-backports-modules-wireless-2.6.39-020639-generic

```

I've got something like this.
Another line worked well. Internet works better but still it is very slow for example in Ubuntu Software Center. Any Ideas?

---

### Post by praseodym on 2012-02-07
So you installed a mainline-kernel?! This is why the 1st command didnt work. Reboot, hold the SHIFT-button pressed and chose the latest kernel except 2.6.39. Which one is that? Check

> uname -a

---

### Post by adashiu on 2012-02-08
Yes, that is right. I installed another version of kernel because one of the guys on this forum advised to install it to have better connection. 

**Could you tell me what is the disadvantage of having it installed? I am totally green in this subject**

My internet connection works well now, after executing a command :
```
sudo apt-get install linux-backports-modules-wireless-lucid-generic
```

---

### Post by adashiu on 2012-02-08
?

---

### Post by praseodym on 2012-02-08
A mainline kernel brings some new features and drivers, but sometimes it doesnt fit as well as the "native" one because of some dependencies. You can install the package **startupmanager** to choose the "other one"

---

