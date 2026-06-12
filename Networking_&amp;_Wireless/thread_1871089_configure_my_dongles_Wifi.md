---
title: "configure my dongles Wifi"
date: 2011-10-28
forum: Networking &amp; Wireless
---

### Post by jrev on 2011-10-28
Hi all,I have installed an operating WIFI connection to my internet provider "Free" via his Freebox.

I want now to connect my computer on it via an USB WIFI dongle.
Could you tell me the procedure ?

Thanks for your guidance ...

---

### Post by ajgreeny on 2011-10-28
It would be useful to know what make your wifi dongle is, ie the chipset it runs on, as that will need a driver.

Can you run ```
lspci
``` and ```
lsusb
``` in terminal and report the output back here as a starting point, please.

---

### Post by jrev on 2011-10-28
the lsusb command gives me one specific line :
Bus 002 Device 005: ID 050d:705c Belkin Components F5D7050 Wireless G Adapter v4000 [Zydas ZD1211B]
thanks for your ansver :P

---

### Post by ajgreeny on 2011-10-28
OK, this thread may help you as it seems that chipset should be supported in the latest kernels.
[http://ubuntuforums.org/showthread.php?t=1786570](http://ubuntuforums.org/showthread.php?t=1786570)

---

### Post by jrev on 2011-10-29
jean@jean:~$ sudo modprobe zd1211rw
[sudo] password for jean: 
FATAL: Error inserting zd1211rw (/lib/modules/2.6.32-34-generic/kernel/drivers/net/wireless/zd1211rw/zd1211rw.ko): Unknown symbol in module, or unknown parameter (see dmesg)
jean@jean:~$ modinfo zd1211rw | grep 705C
alias:          usb:v050Dp705Cd*dc*dsc*dp*ic*isc*ip*
jean@jean:~$ alias:          usb:v050Dp705Cd*dc*dsc*dp*ic*isc*ip*sudo modprobe zd1211rw
alias:*: commande introuvable
jean@jean:~$ sudo modprobe zd1211rw
FATAL: Error inserting zd1211rw (/lib/modules/2.6.32-34-generic/kernel/drivers/net/wireless/zd1211rw/zd1211rw.ko): Unknown symbol in module, or unknown parameter (see dmesg)
jean@jean:~$

---

### Post by jrev on 2011-10-29
I now typed :

sudo apt-get update 

then :

sudo apt-get install linux-backports-modules-wireless-3.0.0-lucid-generic

After reboot everything is OK 

Thanks for your attention

---

### Post by jrev on 2011-10-30
I am now configuring a new USB wifi adaptor on a new PC with Ubuntu 10.04 lucid

lsusb provides me with the adapter identity : [B]Bus 001 Device 004: ID 0846:9030 NetGear, Inc. 

what is the next step ?[/B]

the key is wireless NETGEAR N150 wna 1100

Thanks

---

