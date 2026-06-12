---
title: "Terratec T3 Remote Control does not seem to work"
date: 2011-03-13
forum: Mythbuntu
---

### Post by alanmace on 2011-03-13
Hi all,

I'm currently using Mythbuntu 10.10 with a usb Terratec T3 DVB receiver.
It comes with a simple remote control I'm trying to use with lirc.
But it doesn't seem to read any input.
I mean when I use the irw command I don't see anything when pressing buttons.

My main reference is from [linuxtv]("http://www.linuxtv.org/wiki/index.php/TerraTec_Cinergy_T_USB_XXS#Using_LIRC").

This is an extract of my /etc/lirc/hardware.conf
```
#Chosen Remote Control
REMOTE="Linux input layer (/dev/input/eventX)"
REMOTE_MODULES=""
REMOTE_DRIVER="devinput"
REMOTE_DEVICE="/dev/input/by-path/pci-0000:00:1d.7-event-ir"
REMOTE_SOCKET=""
REMOTE_LIRCD_CONF="/etc/lirc/lircd.conf"
REMOTE_LIRCD_ARGS=""
```
I've also tried with the device /dev/input/event4 according to /proc/bus/input/devices :

```
I: Bus=0003 Vendor=0ccd Product=10a0 Version=0100
N: Name="IR-receiver inside an USB DVB receiver"
P: Phys=usb-0000:00:1d.7-7/ir0
S: Sysfs=/devices/pci0000:00/0000:00:1d.7/usb1/1-7/input/input4
U: Uniq=
H: Handlers=kbd event4 
B: EV=3
B: KEY=14afc336 294284f00000000 0 480158000 219040000801 9e96c000000000 90024010004ffc
```Does anybody have some clues ?

---

### Post by newlinux on 2011-03-14
I'm not familiar with that remote/IR receiver. What is in your lircd.conf file?

---

### Post by alanmace on 2011-03-16
> **newlinux said:**
> I'm not familiar with that remote/IR receiver. What is in your lircd.conf file?
In my lircd.conf : 
```
include "/usr/share/lirc/remotes/devinput/lircd.conf.devinput"
```
And the lircd.conf.devinput seems fine, but I don't see any events from the remote.

---

### Post by wajda on 2011-08-09
I have bought  Terratec T3 as well. And I also have the same issue of IrDA. The system recognizes it correctly, the input file is created (/dev/input/by-path/pci-0000:00:1d.7-event-ir), but I can't see any data in it. I try cat /dev/input/by-path/pci-0000:00:1d.7-event-ir and nothing happens.

Can anybody shed more light on this topic, please? Probably I just misunderstand something or looking into the wrong place.

Thank you.

---

