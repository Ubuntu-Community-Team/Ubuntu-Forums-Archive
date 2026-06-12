---
title: "Broadcom Wireless problems.  first time user, need help please."
date: 2009-01-20
forum: Networking &amp; Wireless
---

### Post by paulisorisrex on 2009-01-20
Hello World  ;)

I'm a first time Ubuntu user, I have version 8.04 on my laptop (HP Pavillion dv6000).

My problem is the Broadcom wireless card isn't compatible or something and I need help finding and installing the correct drivers.

I've tried using instructions from other forums and so far no luck.

help please!  I'm sick of sitting so close to my router.

---

### Post by tommynz1975 on 2009-01-20
Firstly welcome to ubuntu
People are always here ready to help.

please can you open a terminal and type in these commands and copy/paste us the results.
You can find 'terminal' under the menu [B]Applications => Accesories ==> Terminal

[/B]```
lshw -C network
```

```
iwconfig
```

```
ifconfig -a
```
```
ls /lib/firmware
```
```
dmesg | grep -e wlan -e adio
```
```
sudo iwlist scan
```
```
lspci -nn
```
```
sudo modprobe ndiswrapper
```

---

### Post by Ayuthia on 2009-01-21
> **paulisorisrex said:**
> Hello World  ;)

I'm a first time Ubuntu user, I have version 8.04 on my laptop (HP Pavillion dv6000).

My problem is the Broadcom wireless card isn't compatible or something and I need help finding and installing the correct drivers.

I've tried using instructions from other forums and so far no luck.

help please!  I'm sick of sitting so close to my router.

You can first check and see if there is an option available in System->Administration->Restricted Drivers/Hardware Drivers.  If it is not there, you can go into Synaptic and install b43-fwcutter.  You will need a working internet connection so that it can download a couple of files it needs to make your card work.  It will ask you if you want it to fetch the firmware for you.  Say yes if you have a working connection and then you can reboot.  Hopefully after that, it will work.

---

