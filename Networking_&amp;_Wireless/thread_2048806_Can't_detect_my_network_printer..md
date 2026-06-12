---
title: "Can't detect my network printer."
date: 2012-08-27
forum: Networking &amp; Wireless
---

### Post by december0123 on 2012-08-27
Hello everyone.

I have a TL-WR842ND router with a printer plugged into it via usb. How can I make my Xubuntu laptop detect it?
Printer is not listed on router's DHCP clients list.
I've tried using system-config-printer to add a printer, but I can't get it to work.
Any help will be very much appreciated.
Cheers.

---

### Post by december0123 on 2012-08-28
Bump...

---

### Post by drdos2006 on 2012-08-28
If your printer is not listed on your router's DHCP clients list then I doubt very much that you will be able to print to the printer while it is connected to your router, unless your router is designed as a printer server and the printing operation is switched off. 

Does your router offer print server capability ?
[edit]
Looks like it does printing. Check that the function is switched on inside your router setup.
[/edit]

regards

---

### Post by december0123 on 2012-08-29
Yes, i guess i should've mentioned that. My router has a print server on it and when i log into it, i can see that it is "online". Another thing, they give a windows program that when installed detects the printer and I can use it then, but nothing like that for Linux...I've even tried using it under wine, but it failed.

---

### Post by drdos2006 on 2012-08-29
So if Windoze can see it, can you get an IP address and a connection name of the printer ?

That may enable you to connect via Ubuntu with something like : ipp://<Ip_address_of_printer>/printer_name 
Unless of course unPlug-and-Play is what connects the printer to Windoze.

Check if switching uPnP on and off while using Windoze makes any difference to connecting to the printer.

regards

---

### Post by december0123 on 2012-08-30
I decided to contact TP-Link and this is their response: 
"[...]Bad news is that USB printer server function of TL-WR842ND can only work together with USB printer controller utility. It does not work by adding TCP/IP port on your system. Utility for lunix is not available now, as soon as it comes out, we will put it on the official website. Please pay close attention to our website."
...Damn.

---

### Post by drdos2006 on 2012-08-30
Shame about that. Looks like they are working on it for linux tho.

regards

---

### Post by december0123 on 2012-08-31
Anyway, thank you very much for your interest.

---

