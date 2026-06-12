---
title: "Broken hardware wifi switch"
date: 2013-06-01
forum: Networking &amp; Wireless
---

### Post by ugm6hr on 2013-06-01
Posting this in case anyone else struggles to fix their wifi (with a mini PCI-E / PCI Express card).

Situation:
Wireless working one minute, then stops working. Network Manager claims wifi card is disabled by hardware switch. Confirmed on CLI:
```
$ rfkill list all
0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
2: hci1: Bluetooth
	Soft blocked: no
	Hard blocked: no

```

Note this is "Hard" not "Soft" blocked... (for the latter, other forums suggest trying "sudo rfkill unblock all")

Solution:
Firstly, try the simple things:
[LIST=1]
[*]Check that the external / physical hardware switch for wifi radio is turned on.
[*]Check the BIOS for any controls relating to wifi - some laptops can disable the hardware switch from BIOS (apparently).
[*]Turn off laptop, remove battery, press power button a few times, power back on.
[/LIST]

[[img]http://s24.postimg.org/6zlq6obmp/33athxe.jpg[/img]](http://postimg.org/image/6zlq6obmp/)

If all fails, try this:
[LIST=1]
[*]Remove wifi card (usually under an easily accessible trapdoor on bottom of laptop)
[*]Place a 1mm x 5mm piece of sticky tape (I used medical micropore, but insulation tape should work) over pin 20 connector to insulate the pin from the connector (see image - image is taken with "chip" and antenna connectors etc facing away from camera - is basically 2nd connector on the wider side from notch on underside of wifi card)
[*]Replace wifi card
[/LIST]

This disables the hardware switch, and leaves wifi on always. Though I don't have a software switch shortcut on my laptop, it apparently does not affect that at all. Hope this helps a few ubuntuforums visitors (and googlers), as the original did me.

See reference thread for further details (including equivalent mini PCI card fix).

Reference:
[LIST]
[*][http://www.notebookforums.com/t/225429/broken-wireless-hardware-switch-fix/60#post_3379692](http://www.notebookforums.com/t/225429/broken-wireless-hardware-switch-fix/60#post_3379692)
[*][http://www.notebookforums.com/t/225429/broken-wireless-hardware-switch-fix](http://www.notebookforums.com/t/225429/broken-wireless-hardware-switch-fix)
[/LIST]

---

