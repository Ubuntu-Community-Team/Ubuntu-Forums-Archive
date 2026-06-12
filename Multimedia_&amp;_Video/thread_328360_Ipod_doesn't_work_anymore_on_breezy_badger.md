---
title: "Ipod doesn't work anymore on breezy badger"
date: 2006-12-30
forum: Multimedia &amp; Video
---

### Post by django_xl on 2006-12-30
Hi peeps,

I have worked succesfully with gtkpod and my ipod on Ubuntu Breezy Badger on my amd64 system. That was THE reason Ubuntu could stay onto my primary pc because I didn't need Windows anymore.

However, I could not use this combination anymore because I didn't get the automatic gtkpod icon on my desktop anymore and the /media directory wasn't created anymore if I plugged in my ipod.

Dmesg gives this:
[ 3670.095241] usb 2-7: new high speed USB device using ehci_hcd and address 4
[ 3672.912407] usb 2-7: unable to read config index 0 descriptor/start
[ 3672.912414] usb 2-7: can't read configurations, error -110
[ 3672.946782] usb 2-7: new high speed USB device using ehci_hcd and address 5
[ 3675.765126] usb 2-7: can't set config #1, error -110
[ 3675.800593] usb 2-7: new high speed USB device using ehci_hcd and address 6
[ 3681.361016] usb 2-7: can't set config #1, error -110
[ 3681.395977] usb 2-7: new high speed USB device using ehci_hcd and address 7
[ 3684.199489] usb 2-7: can't set config #1, error -110
[ 3922.214597] usb 2-8: new high speed USB device using ehci_hcd and address 8

So, what is wrong here? And what could I do?

---

