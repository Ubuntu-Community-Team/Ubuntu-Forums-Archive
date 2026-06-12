---
title: "wifi not detected but was previously"
date: 2013-04-13
forum: Networking &amp; Wireless
---

### Post by slgtheindividual on 2013-04-13
for some reason my wifi has just stopped appearing altogether but wired connection works fine, ```
ifconfig -a
``` gives eth0 and lo but not wlan0,
I edited /etc/network/interfaces to:
```
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet dhcp
wpa-ssid mynetworkname
wpa-psk mypassphrase
```

also running ```
sudo ifdown wlan0 && sudo ifup wlan0
``` gives me an output of ```
~$ sudo ifdown wlan0 && sudo ifup wlan0
ifdown: interface wlan0 not configured
wpa_supplicant: /sbin/wpa_supplicant daemon failed to start
run-parts: /etc/network/if-pre-up.d/wpasupplicant exited with return code 1
Internet Systems Consortium DHCP Client 4.2.4
Copyright 2004-2012 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Cannot find device "wlan0"
Error getting hardware address for "wlan0": No such device
Failed to bring up wlan0.


```

and I do not know what else to do. Any help would be appreciated. Also wifi works fine using a live cd.

---

### Post by chili555 on 2013-04-13
It sounds like the wireless driver is not loading as expected. Let's find out which is needed and load it explicitly. Please run and post:```
lspci -nn | grep 0280
```I assume, since you have populated* /etc/network/interfaces*, that Network Manager is not running and , ideally, removed.

---

### Post by steeldriver on 2013-04-13
EDIT*: nevermind, chili55 has got it covered*

---

### Post by slgtheindividual on 2013-04-13
that gives me

```
03:00.0 Network controller [0280]: Atheros Communications Inc. AR9485 Wireless Network Adapter [168c:0032] (rev 01)

```

---

### Post by slgtheindividual on 2013-04-13
update: did a system reboot and now even my wired connection isn't working, also cannot access network manager it says "the system network services are not compatible with this version" however running all of the previous commands still gives me the same outputs

---

### Post by chili555 on 2013-04-13
First let's get your wireless driver working:```
sudo su
echo ath9k >> /etc/modules
modprobe ath9k
exit
```Let's check the position of the wireless switch or key:```
rfkill list all
```Let's restart the interface and see if we connect:```
sudo ifdown wlan0 && sudo ifup wlan0
```Are you connected?

---

### Post by slgtheindividual on 2013-04-14
echo ath9k >> etc/modules
 
gives me 

```
bash: etc/modules: No such file or directory
```

then 
modprobe ath9k

gives me 

```
libkmod: ERROR ../libkmod/libkmod.c:554 kmod_search_moddep: could not open moddep file '/lib/modules/3.8.0-18-generic/modules.dep.bin'
```

rfkill list all
gave me no output 

and then

sudo ifdown wlan0 && sudo ifup wlan0

gives

```
ifdown: interface wlan0 not configured
Ignoring unknown interface wlan0=wlan0.
```

thank you in advance for all of your help

---

### Post by slgtheindividual on 2013-04-14
I managed to fix this, apparently it was some iddue with my drivers, I added sudo add-apt-repository ppa:ubuntu-x-swat/x-updates and ran an update, rebooted and for some reason that fixed my wifi, thank you very much for all of your help, I really appreciate it.

---

### Post by chili555 on 2013-04-14
Glad it's working by whatever means.

---

