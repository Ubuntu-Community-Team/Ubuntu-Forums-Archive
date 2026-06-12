---
title: "Ethernet card not recognized during install"
date: 2006-04-14
forum: Networking &amp; Wireless
---

### Post by qw3rty on 2006-04-14
It is a Netgear EA201 ISA card.  I read that it is ne2000 compatible.

How do I install a driver for this card?

This is the first time I've really used linux, so I couldn't figure out the sticky at the top of this forum.

Thanks

---

### Post by qw3rty on 2006-04-15
During the installation when it couldn't find the network card it said I had a firewire card and asked if I want to use that.  I don't have a firewire card installed.

---

### Post by qw3rty on 2006-04-16
I know it is possible because Fugee was able to do it.

He first asked for help here:
[http://www.ubuntuforums.org/showthread.php?t=40289](http://www.ubuntuforums.org/showthread.php?t=40289)

And here he says he eventually figured it out:
[http://www.ubuntuforums.org/showpost.php?p=220675&postcount=18](http://www.ubuntuforums.org/showpost.php?p=220675&postcount=18)

---

### Post by joselin on 2006-04-16
I had the same trouble with my IBM T21 laptop, i had to add acpi=off as a kernel option in order to have network card working.

Hope that helps.
Regards

---

### Post by qw3rty on 2006-04-16
Well I figured it out.

I had to istall windows 98 on this computer to get the I/O address and IRQ of the NIC.

Then I typed ```
sudo modprobe ne io=0x340 irq=3

```

Then I was able to configure the card.

---

