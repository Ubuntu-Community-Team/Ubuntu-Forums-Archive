---
title: "Ubuntu cannot find my network after disconnect"
date: 2012-11-02
forum: Networking &amp; Wireless
---

### Post by dimitars on 2012-11-02
Hey guys. Let me try to explain the problem.

Whenever my laptop shuts down because of battery, or if we loose power, of the router is restarted for some reason, my laptop cannot find my wireless. It finds other wireless networks just fine, but mine it can not.

I have d-link router(I don't think it is router's fault cause on windows it works just fine for me and 3 other roommates).

I have: 
```
01:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM57780 Gigabit Ethernet PCIe [14e4:1692] (rev 01)
02:00.0 Network controller [0280]: Broadcom Corporation BCM43225 802.11b/g/n [14e4:4357] (rev 01)


```

Till today(since 11.10) I was able to fix this somehow with several repeats of : Disable Network then Enable Network.. sometimes restart and it was somehow working aggain.

But today I can't. I spent 2 hours doing that and restarts, and iwlist scanning and just can't find my network(which still works just fine on windows machines).

I have Broadcom STA proprietary driver activated.

Please help me fix this problem. 2 years I've been dealing with this.

---

### Post by gerowen on 2012-11-02
Have you tried using a different program to connect to it like Wifi Radar?  You could also try deleting the network profile for your wireless and reconnecting as if it's the first time again.

---

### Post by dimitars on 2012-11-02
> **gerowen said:**
> Have you tried using a different program to connect to it like Wifi Radar?  You could also try deleting the network profile for your wireless and reconnecting as if it's the first time again.

Ah i forgot to mention, i tried both of those things.
Although for radar i knew it wouldn't work because iwlist scan wasn't showing my network either.

---

### Post by Hadaka on 2012-11-02
Hi, please post the output of...

```
lsmod | grep -E 'brcmsmac|bcma' 
``````
grep 'blacklist' /etc/modprobe.d/blacklist.conf 
```thanks

---

### Post by dimitars on 2012-11-02
Here it is: 

> 
deemeetar@deemeetar:~$ grep 'blacklist' /etc/modprobe.d/blacklist.conf
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac
deemeetar@deemeetar:~$ lsmod | grep -E 'brcmsmac|bcma'
deemeetar@deemeetar:~$ 


---

### Post by Hadaka on 2012-11-02
ok, nothing jumping out there, please post..

```
lspci -nnk | grep -A4 Wireless 
```

```
cat /etc/modules
```

---

### Post by dimitars on 2012-11-02
> # /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp

The other one is empty.

Looks like nothing here too :(

---

### Post by Hadaka on 2012-11-02
exactly..and there should be..
but first..you forgot to post..
```
lspci -nnk | grep -A4 Wireless 
```

---

### Post by dimitars on 2012-11-02
It doesn't print anything.

---

### Post by Hadaka on 2012-11-02
empty?..thats your wireless card lspci dump..hmmm
try this

```
lspci -nnk |grep -iA5 net
```

---

### Post by Hadaka on 2012-11-02
ok...well, you have the sta driver/...correct?

---

### Post by dimitars on 2012-11-02
Yes i have STA driver.

> 
Ethernet controller [0200]: Broadcom Corporation NetLink BCM57780 Gigabit Ethernet PCIe [14e4:1692] (rev 01)
	Subsystem: Acer Incorporated [ALI] Device [1025:036d]
	Kernel driver in use: tg3
	Kernel modules: tg3
02:00.0 Network controller [0280]: Broadcom Corporation BCM43225 802.11b/g/n [14e4:4357] (rev 01)
	Subsystem: Broadcom Corporation Device [14e4:04da]
	Kernel driver in use: wl
	Kernel modules: wl, bcma, brcmsmac
ff:00.0 Host bridge [0600]: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers [8086:2c62] (rev 02)
	Subsystem: Acer Incorporated [ALI] Device [1025:036d]
Ethernet controller [0200]: Broadcom Corporation NetLink BCM57780 Gigabit Ethernet PCIe [14e4:1692] (rev 01)
	Subsystem: Acer Incorporated [ALI] Device [1025:036d]
	Kernel driver in use: tg3
	Kernel modules: tg3
02:00.0 Network controller [0280]: Broadcom Corporation BCM43225 802.11b/g/n [14e4:4357] (rev 01)
	Subsystem: Broadcom Corporation Device [14e4:04da]
	Kernel driver in use: wl
	Kernel modules: wl, bcma, brcmsmac
ff:00.0 Host bridge [0600]: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers [8086:2c62] (rev 02)
	Subsystem: Acer Incorporated [ALI] Device [1025:036d]



This one gives results

---

### Post by Hadaka on 2012-11-02
whew...thanks, this should fix you up.

```
sudo echo 'wl' >> /etc/modules 
```

this will load your diver on start up, so run the command
boot, let the computer connect to your router, then go yank
the power from the router ...plug it back...find the cable connection
and the computer should reconnect to YOUR ssid.   please let me know
if this worked for you

thank

---

### Post by Hadaka on 2012-11-02
Looks like you also need to toss a couple items into the blacklist pool

```
echo "blacklist brcmsmac" | sudo tee -a /etc/modprobe.d/blacklist.conf 
```

```
echo "blacklist bcma" | sudo tee -a /etc/modprobe.d/blacklist.conf 
```

that should help.

---

### Post by dimitars on 2012-11-03
Yay it worked. 

Though i haven't done the blacklist thing. Should i do it now that the first thing worked?
Btw finally after 2 years i have normal wifi.
Thank you a lot!

---

### Post by Hadaka on 2012-11-03
Great!  yes..do the blacklist thing...test it the same way with the
power reset...come back..to let me know how it went and to mark the 
thread SOLVED

---

### Post by dimitars on 2012-11-03
Works well again.
Thank you so much!

---

### Post by Hadaka on 2012-11-03
great..glad all is well, please dont forget to use...thread tools
and mark this solved

---

