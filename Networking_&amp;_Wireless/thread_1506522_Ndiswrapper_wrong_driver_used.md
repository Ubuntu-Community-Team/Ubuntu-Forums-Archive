---
title: "Ndiswrapper wrong driver used"
date: 2010-06-10
forum: Networking &amp; Wireless
---

### Post by xefix on 2010-06-10
I am trying to get a USB device working in Ubuntu. It's a radio for which I have Windows drivers. When I connect it under Windows, the device appears in the output of ipcofig as an ethernet adapter local area connection and has an IP address. I have installed the same driver in Lucid using ndiswrapper without errors. When I connect the device and run ndiswrapper -l, I get the following output:

driver installed
device (0CAD:1021) present

However, the radio doesn't appear in the output of ifconfig. Additionally, the output of lsmod claims that ndiswrapper is used by 0 devices, and running tail /var/log/messages outputs the following line when I connect the device:
usb 4-1: new full speed USB device using uhci_hcd and address 2

Does this mean that Ubuntu is forcing the radio to use incorrect native drivers instead of ndiswrapper? Is this because of a fault with the Windows driver (I was told that this driver works fine with ndiswrapper in RHEL, but have not tested it myself)? Since uhci-hcd doesn't appear in the list output by lsmod, how can I blacklist it?

---

### Post by xefix on 2010-06-10
I have just moved my base of operations to Fedora 13 and everything works just fine - the driver installs with ndiswrapper. The radio appears as wlan0, has an IP address, and is pingable. I would still very much like to get this figured out on Ubuntu, so if anyone has insights, please let me know.

---

