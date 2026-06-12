---
title: "Mouse freezes randomly"
date: 2010-09-26
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by Neo40 on 2010-09-26
Hello,

I have installed Ubuntu 10.10 Beta yesterday. I then updated some packages (more 280 I think?) and I installed Nvidia driver.
After playing with it, suddenly my mouse has stopped moving. Fortunately, my keyboard still works. It happenned twice yesterday and this morning too. If I reboot my machine, my mouse will work fine...but for how long...?
Where should have check first to see where is the problem? 
I know my hardware is good because I was using Debian/Squeeze for several months without problem.

Thanks.

---

### Post by FishRCynic on 2010-09-26
ps2 mouse?
usb mouse?

&/or wireless?

model # & manufacturer of mouse would be somewhat helpful.

(i have had issues with low batteries in wireless mice doing just that)

if usb if you unplug it and plug it back in does it start working again?

---

### Post by Neo40 on 2010-09-26
> **FishRCynic said:**
> ps2 mouse?
usb mouse?

&/or wireless?

model # & manufacturer of mouse would be somewhat helpful.

(i have had issues with low batteries in wireless mice doing just that)

if usb if you unplug it and plug it back in does it start working again?


This is an usb mouse. But like I said, the problem is not hardware!!!

---

### Post by cariboo on 2010-09-26
Just to cover all the bases, does your mouse still show up when you run **lsusb**? It should look something like this:

```
Bus 002 Device 004: ID 045e:008c Microsoft Corp. Wireless Intellimouse Explorer 2.0
```

and is there any thing in dmesg?

```
[    2.697490] input: Microsoft Microsoft Wireless Optical Mouse® 1.0A as /devices/pci0000:00/0000:00:02.0/usb2/2-4/2-4:1.0/input/input2
[    2.697593] generic-usb 0003:045E:008C.0004: input,hidraw1: USB HID v1.11 Mouse [Microsoft Microsoft Wireless Optical Mouse® 1.0A] on usb-0000:00:02.0-4/input0
```

---

### Post by FishRCynic on 2010-09-26
use cariboo907 he beat me to it lol

obviously it is hardware related.
(the symptom is the mouse stops)

something in the beta's driver(s) must not like your mice
(you must have tried more than one by now)
which may be a usb controller issue 

check dmesg and see what &/or why it stops.


my mouse in dmesg for example is
[   69.476323] logitech 0003:046D:C517.0002: input,hiddev96,hidraw1: USB HID v1.10 Mouse [Logitech USB Receiver] on usb-0000:00:02.0-1/input1

a wireless logitech

if i had your issue i would check to see if it is the mouse or the usb that stops working and/or there may be other issues

that fact that it works in another distro does mean its not mucked up in this [B]beta
[/B]

and if you are lucking you may have found a bug and get to file a bug report

---

