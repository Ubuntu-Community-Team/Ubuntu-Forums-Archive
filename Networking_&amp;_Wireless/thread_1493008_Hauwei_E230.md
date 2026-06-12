---
title: "Hauwei E230"
date: 2010-05-25
forum: Networking &amp; Wireless
---

### Post by Orions on 2010-05-25
Hi, I am newbie in linux based systems, so i need some experts help with hauwei E230 modem installing in ubuntu 10.04. 
Can u please post some steps how to do that, not links. (Because i hawe only that hauwei wireless data card internet connection, i need to copy text to document, restart windows and run ubuntu. So its quite a problem to learn something about ubuntu with out i-net)

---

### Post by alexfish on 2010-05-25
Hi

have a look here 

   	 	 	 	 	 	  [How To : Mobile Broadband Connections [ Ubuntu 10.04 : 9.10 : 9.04 ]]("http://ubuntuforums.org/showthread.php?t=1466490")
 

 lets us know how you get on

regards

alexfish

---

### Post by pdc on 2010-05-26
Hi Orions;

alex is the real expert on these, but have a read at half-way down this page

[http://www.pharscape.org/networkmanager-0.7.0-and-3g-wwan-modems.html](http://www.pharscape.org/networkmanager-0.7.0-and-3g-wwan-modems.html)

create a mobile broadband connection

is this any help?

---

### Post by HandeH on 2010-07-31
In Lucid Lynx, just install two packages usb-modeswitch-data and usb-modeswitch (in this order) and reboot! :)

Find the newest package of usb-modeswitch-data_xxxxxxxx-x_**all.deb** and the usb-modeswitch for your infrastructure (propably i386) at:
[http://ftp.fi.debian.org/debian/pool/main/u/usb-modeswitch-data/](http://ftp.fi.debian.org/debian/pool/main/u/usb-modeswitch-data/)
[http://ftp.fi.debian.org/debian/pool/main/u/usb-modeswitch/](http://ftp.fi.debian.org/debian/pool/main/u/usb-modeswitch/)
The ones in Ubuntu repositories did not give a desired result. 

Although, I find this connection is unstable (disconnections and occasional drop downs of speed) and unresponsive (does not download www pages, though data is uploaded).

---

