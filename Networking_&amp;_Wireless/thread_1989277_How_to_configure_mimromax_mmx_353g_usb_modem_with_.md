---
title: "How to configure mimromax mmx 353g usb modem with ubuntu 12.04 LTS"
date: 2012-05-28
forum: Networking &amp; Wireless
---

### Post by drsuhashis on 2012-05-28
Hello friends i am new to Ubuntu so it is difficult for me to know many things. Actually i am using Ubuntu 12.04 LTS in my Acer Aspire 5542 laptop, and i have a Micromax MMX 353G usb modem in which i use vodafone 2g sim to connect to internet with apn 'www' and isp 'vodafone mobile'. it is a plug and play device but when i connect it to Ubuntu it is not detected. Pls help me.

---

### Post by drsuhashis on 2012-05-28
pls guys some1 help me.

---

### Post by drsuhashis on 2012-05-28
Thanx ubuntu forum and especially raj,a member of ask ubuntu whose rpl to a question helped me too. this was his solution:-

I had the same problem too. if your usb modem doesnt not detect as usb mass storage,then try this. open terminal type lsusb

for example: $ lsusb

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Bus 001 Device 005: ID 1c9e:9605 OMEGA TECHNOLOGY

Note down the id of your device i.e from above example 1c9e:9605

and in terminal type sudo modprobe usbserial vendor=0x1c9e product=0x9605

it will ask for user passwd if required. then wait for some minutes

check the network manager applet if detect it will show the new mobilebroadband gsm or cdma,then click the new mobilebroadband. if not detected try to remove modem and connect it

type same cmd sudo modprobe usbserial vendor=0x1c9e product=0x9605

and wait for some minutes. and check network manager and i think you have to do this every time you reboot the system, till ubuntu team find solution for this.

---

### Post by drsuhashis on 2012-05-28
I don't know what is the problem but every time i boot Ubuntu i have to use the command
sudo modprobe usbserial vendor=0x1c9e product=0x9605
to detect my USB modem in the network applet.
Can anyone help.

---

### Post by alexfish on 2012-05-28
looks as if the device is not recognised by the kernel

can post the results of this command from the terminal
```
grep 1C9E /sys/bus/usb/devices/*/modalias
``` may be able to find a suitable driver , then make a rule to load the driver from the info

alexfish

---

### Post by itagomo on 2012-05-30
> **alexfish said:**
>  .. make a rule to load the driver from the info .. 

how do you do that?

---

### Post by keerthiramalingam on 2012-09-06
I am also facing the same issue..

Here is the output
```
kitty@ratch:~$ grep 1C9E /sys/bus/usb/devices/*/modalias
/sys/bus/usb/devices/1-1.1:1.0/modalias:usb:v1C9Ep9605d0000dc00dsc00dp00icFFiscFFipFF
/sys/bus/usb/devices/1-1.1:1.1/modalias:usb:v1C9Ep9605d0000dc00dsc00dp00icFFiscFFipFF
/sys/bus/usb/devices/1-1.1:1.2/modalias:usb:v1C9Ep9605d0000dc00dsc00dp00icFFiscFFipFF
/sys/bus/usb/devices/1-1.1:1.3/modalias:usb:v1C9Ep9605d0000dc00dsc00dp00icFFiscFFipFF
/sys/bus/usb/devices/1-1.1:1.4/modalias:usb:v1C9Ep9605d0000dc00dsc00dp00ic08isc06ip50

```

How to find suitable driver? 
Where should I make the rule to automatically load this driver?

Your help is much appreciated.

Any literature on the above operations would help me get my hands dirty
-

---

