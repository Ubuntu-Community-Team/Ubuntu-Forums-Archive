---
title: "MAC Changer question"
date: 2012-09-04
forum: Networking &amp; Wireless
---

### Post by ShadowVegan on 2012-09-04
Sorry if this is the wrong forum.

I installed macchanger and I'm experimenting with it. I tried to enter ```
macchanger -r eth1
``` because in the examples people use eth1 but it says no such device cound. Then I tried ```
macchanger -r eth0
``` and it said I don't have permissions, so I entered sudo su and tried again and it worked. But why is it that I have to enter eth0 while other people enter eth1? Will my randomized address only be used for certain situations since I typed eth0, and my real address will be used for other situations? How can I make it random for all purposes?

Thanks.

---

### Post by Bachstelze on 2012-09-04
If you have only one network interface, it will be eth0. If you have two, they will be eth0 and eth1, etc. Typically you have one wired and one wireless interface, with the wired one being eth0 and the wireless one being eth1, but if you have only one wired (or wireless) interface, you will just have eth0. using macchanger on any interface will change the MAC address of the corresponding network card for all purposes.

---

### Post by ShadowVegan on 2012-09-04
Thanks for the fast and very clear response! I am currently tethered to my phone for Internet and have wireless turned off, I assume that is why I only had eth0? If I type ```
macchanger -r eth1
``` and it says 'set device name: No such device' does that mean I only have one network interface card? If I enter the command while connected to a wireless network will it work?

Also, question unrelated to macchanger: If I have eth0 and eth1, do they have separate MAC addresses?

---

### Post by Bachstelze on 2012-09-04
You can use [font=monospace]ifconfig[/font] to see a list of all your active interfaces (add the [font=monospace]-a[/font] flag to see a list of *all* interfaces, active and inactive).

For your second question, typically no. A MAC address is a hardware property, meaning each physical network card has its own MAC address (also, a card's MAC address does not change when you put it in another computer). Normally, one card = one interface, so the interfaces will have different MAC addresses.

---

### Post by sisco311 on 2012-09-04
EDIT: Bachstelze beat me to it. :)

Each network device has its own MAC address. 

To display the status of currently active interfaces, run:
```
ifconfig
```

*If memory serves, nowadays, usually, by convention or for any other reasons*, wireless devices will show up as wlan[0-9]+.

---

### Post by Bachstelze on 2012-09-04
> **sisco311 said:**
> 
*If memory serves, nowadays, usually, by convention or for any other reasons*, wireless devices will show up as wlan[0-9]+.

Mine is eth1, and I think the recent trend has been to unify them to use ethX, even though you still find wlanX ones occasionally. I could be wrong as well, though... Anyway, it doesn't really matter here, OP should just use ifconfig and use whatever it says. :p

---

### Post by sisco311 on 2012-09-04
> **Bachstelze said:**
> Mine is eth1, and I think the recent trend has been to unify them to use ethX, even though you still find wlanX ones occasionally. I could be wrong as well, though...


Was to lazy to google it, but

this reminds me the *hda -> sda > UUID* transition. In this light, it makes sense. 

> **Bachstelze said:**
> Anyway, it doesn't really matter here, OP should just use ifconfig and use whatever it says. :p

You're absolutely right.

---

### Post by ShadowVegan on 2012-09-05
I have wlan0 but no eth1. Is my wlan0 the same as someone else's eth1?

My active interfaces:
eth0
lo
usb0

My total interfaces:
eth0
lo
usb0
wlan0

The IP address for lo is all 0s and it won't let me change it. No idea what it is. It said Xerox.

```
root@shadowvegan-laptop:/home/shadowvegan# macchanger -r lo
Current MAC: 00:00:00:00:00:00 (Xerox Corporation)
ERROR: Can't change MAC: interface up or not permission: Operation not supported
```

---

### Post by Sergius14 on 2012-09-06
[LIST]
[*]**eth0 **is your physical Ethernet interface.
[*] **lo **is the local loopback (a kind of internal interface... don't worry about it and don't touch it).
[*] **usb0 **should be your thether connection.
[*] **wlan0 **is your WiFi.
[/LIST]

Why you need to change the MAC address? At what interface you need to change it?

---

### Post by ShadowVegan on 2012-09-06
Thanks. I've just been playing around with it and trying to get a better understanding in general. wlan0 on my computer is the equivilent of eth1 on other computers, correct?

Also, if I were to use a regular modem and router I would use wlan0 (and other people would use eth1) and if I connected directly to a modem via Ethernet cable I would use eth0, correct?

And yes, usb0 is because I tether my phone to my laptop for Internet. High speed isn't available here.

---

