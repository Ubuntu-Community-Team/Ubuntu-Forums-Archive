---
title: "Shared Printer Networking"
date: 2011-02-13
forum: Networking &amp; Wireless
---

### Post by Jalaska13 on 2011-02-13
I have printer hooked up to my Ubuntu box and set to be shared with the network.  Does anybody know how I can figure out what the url is for that printer?  I've been trying to print from PCs and macs on the network, and they don't recognize the printer, and won't accept the Ubuntu box's IP address as a legitimate printer address.  In the PC printer dialogue, it asks for an address of either of the two following forms:
\\server\printer
[http://server/myprinter/.printer](http://server/myprinter/.printer)
Does anybody know what either of these would be?

---

### Post by Slave2Metal on 2011-02-13
Just did this today.  But it took some doing and I'm not sure I can help.  Printer is connected to a laptop running ubuntu 10.10 that is connected via ethernet.  Desktop in different room running 10.04 and using a wireless usb adapter is the machine I wanted connected to printer.  Got it connected using 192.168.0.103:631.  Port 631 Description: Internet Printing Protocol.

---

### Post by cjhabs on 2011-02-13
I have mine working using:
[http://ip_of_cups_server:631](http://ip_of_cups_server:631)

---

