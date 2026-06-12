---
title: "Finding Bluetooth"
date: 2011-06-18
forum: Networking &amp; Wireless
---

### Post by jwaclawsky on 2011-06-18
I have a Dell XPS 7100 running Ubuntu 11.04. When I click on Bluetooth in system > preferences Ubuntu tells me "your computer does not have any Bluetooth adapters plugged in". I thought for sure the system had bluetooth running in 10.10 (It is a test machine and I hadn't been using it for a few months so I just installed 11.04). How can I tell if I my hardware has a bluetooth adapter installed. Is there a command that lists all the wireless adapters on my system?

---

### Post by nbound on 2011-06-18
firstly try lspci and lsusb to see if there are any bluetooth pci/usb devices

---

### Post by jwaclawsky on 2011-06-18
I found the packing slip for this machine a Dell Studio XPS 7100 Minitower. It lists item number: "430-0708 Dell Wireless 365 Bluetooth 2.1 Module". So now I am sure it was working before I installed 11.04. The output from lspci and lsusb is in the attachment. How should I proceed debugging this. BTW, the Dell originally came with Ubuntu 10.04. I left Microsoft a long time ago.

---

