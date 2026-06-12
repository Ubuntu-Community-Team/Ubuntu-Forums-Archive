---
title: "USB Wifi (Ndiswrapper) Must Be Reinstalled Each Boot"
date: 2009-01-09
forum: Networking &amp; Wireless
---

### Post by fasteddy86 on 2009-01-09
Hi,

I recently installed Kubuntu on an htpc (will be running xbmc), and used an SMCWUSBT-G usb wifi dongle to network it. I was able to get it running using ndiswrapper without too much fuss, but I am left with one last problem. Each time I reboot, I have to remove the dongle, reinsert it, uninstall the ndis driver, then reinstall it to get my wifi working. Not only is this annoying, the box will be more or less inaccessible once setup is complete, necessitating a permanent solution.

Upon a reboot, ndiswrapper -l shows the hardware and driver present, but knetwork manager shows only eth0, the onboard ethernet port. Once I go through the steps outlined above, wlan0 comes up and my network connects. Any ideas?

---

### Post by alan34 on 2009-01-09
Have you added ndiswrapper to /etc/modules ?

Not sure of the editor in Kubuntu so in a terminal

sudo nano /etc/modules

add **ndiswrapper** on a line on its own at the bottom of the file.

ctlx y and enter saves and exits the file then reboot.

good luck

---

### Post by fasteddy86 on 2009-01-12
> **alan34 said:**
> Have you added ndiswrapper to /etc/modules ?


Hi, 

Yes, ndiswrapper was added to modules already. Thanks for the help, but in the end I just bought a pci card. For $Cdn 16.95 I picked up a TP-LINK TL-WN353G. Not only was it the cheapest card I could find locally, but it also has native support (Realtek 8185).

---

