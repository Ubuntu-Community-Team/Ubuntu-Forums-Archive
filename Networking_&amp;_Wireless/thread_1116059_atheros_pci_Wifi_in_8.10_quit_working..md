---
title: "atheros pci Wifi in 8.10 quit working."
date: 2009-04-04
forum: Networking &amp; Wireless
---

### Post by dnpate on 2009-04-04
Wifi was working in 8.10 and stopped for ?.  I have searched forums and tried various things including using a older kernel with no results.  I considered reinstalling, but I have video/audio changes that take a lot of time to do.  So, is there a way to remove all of just the networking files and reinstalling those only?  the device is a atheros pci card in a desktop.
TX
David

---

### Post by dnpate on 2009-04-04
I went to System -> hardware and clicked with the following message about the atheros.  "This driver has been disabled but is still in use".  Clicking on the activate button makes it look as though changes are being made but the message "this driver ..." remains.  Does this mean anything?
David

---

### Post by bgerlich on 2009-04-04
try ```
dmesg | grep ath
``` to find out what is exactly wrong.

---

### Post by dnpate on 2009-04-04
no output from the code at all.

---

### Post by dnpate on 2009-04-05
Got my wifi by plugging in a linksys usb wifi dongle.

A "Device Manager" program such that Windows has would be helpful.  (I cannot write it).

---

### Post by bgerlich on 2009-04-05
"lshw" (entire hardware info) and "lspci" (pci psecific info) and "lsusb" (usb devices info).

Post the result of the first and last command on forum to give us more details about your equipment.

---

### Post by bolingobuntu on 2009-04-07
Hello there.  I am fairly new to ubuntu and encountered a similar as dnpate with the atheros wifi running ubuntu 8.10 with Gnome 2.24.1. I am using an eeepc 1000h netbook and was hoping to find some help here.  A friend of mine was so kind and installed ubuntu for me and everything worked perfectly.  Until recently when wireless connection stopped working.
I looked for help on eeepc forums as well as here and nothing helped.  I typed in the command Bgerlich suggested into Terminal and here's what I received: 

dmesg | grep ath
[   19.279416] ath_hal: module license 'Proprietary' taints kernel.
[   19.374994] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[   20.217780] ath_pci: 0.9.4
[   20.219022] ath_pci 0000:01:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[   20.219046] ath_pci 0000:01:00.0: setting latency timer to 64
[   20.267379] ath_pci 0000:01:00.0: PCI INT A disabled


Can someone help me understand what this means and how I could perhaps resolve the wifi problem?  That way I could unshackle my eeepc from the ethernet cable.  Thanks in advance!

-Bolingobuntu):P

---

