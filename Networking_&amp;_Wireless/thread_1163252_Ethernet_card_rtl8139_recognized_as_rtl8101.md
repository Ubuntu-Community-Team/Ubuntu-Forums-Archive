---
title: "Ethernet card rtl8139 recognized as rtl8101"
date: 2009-05-18
forum: Networking &amp; Wireless
---

### Post by aglaxaphonia on 2009-05-18
Hi All,
I've installed Intrepid Ibex and am dual booting with windows vista, however I cannot use my ethernet card. The lights on the side of the computer are on, and the card functions in windows, however the card does not connect to the internet in intrepid, even with a manual ip addy.    In windows device manager the card is listed as rtl8139, but lspci in ubuntu lists the card as rtl8101.  How do I correct this?

I'm really new to ubuntu and would love to migrate, however I can't without ethernet....

Thanks All!

---

### Post by puppywhacker on 2009-05-18
lspci never lies. it produces the output based on what ID's the pci-bus returns ("lspci -n") and then maps the ID's using the file /usr/share/misc/pci.ids it's this file that gives you the human readable output. 

So your ID maps to an rtl8101 because realtek assigned the same ID to it.

anyway since the module you want is the "8139too" so unload any other driver. The following is a list of commands to find the driver which is loaded. then unload (remove from memory). then load the new driver, than update the dependency table. this should approximately get your interface running

lsmod | egrep "r8|rtl8"
modprobe -r r8101
modprobe 8139too
modprobe -a

---

