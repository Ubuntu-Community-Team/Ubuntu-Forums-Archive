---
title: "Configuring D-Link DP100 for Ubuntu"
date: 2013-01-06
forum: Networking &amp; Wireless
---

### Post by flosspike on 2013-01-06
Hi Forum users,
 Bit of a problem. I have a D-link DP100, spent most of the day getting it working with it's ADMIN software on winXP and now configured it to work on my network. The admin software works a treat, but I hate windows. I'm going to use this little printer server as a "Ethernet to serial" converter extracting data from a water treatment works control panel which is equipped with a serial port. I'm fairly confident Ubuntu 12.10 has found this device by attempting to install a network printer and entering it's IP address. So, how does one communicate with this printer server using a serial terminal program such as "serial port terminal" as from software centre. My aim is to configure a 24hr computer (Fit2pc) to automatically download the information, dissect it and then do something with the data, email warnings, populate a spreadsheet etc. I'm fairly new to linux but not a absolute beginner. To test I currently have the DP-100 plugged into my Cisco's console port.

---

### Post by fdrake on 2013-01-06
you have to install cups and  configure them:
[http://www.liberiangeek.net/2010/06/install-network-printers-cups-ubuntu-10-04-lucid-lynx/](http://www.liberiangeek.net/2010/06/install-network-printers-cups-ubuntu-10-04-lucid-lynx/)

[http://www.unixmen.com/install-cups-print-server-in-ubuntu/](http://www.unixmen.com/install-cups-print-server-in-ubuntu/)

---

### Post by flosspike on 2013-01-12
> **flosspike said:**
> Hi Forum users,
   I'm going to use this little printer server as a "Ethernet to serial" converter extracting data from a water treatment works control panel which is equipped with a serial port.

hmmm,
It appears so-far this isn't possible. I'm easily able to configure the DP100 as designed both in Linux (telnet) and Windows (PSadmin) although I have no printer to test. I believe the dp100 being a print server, the only return information is from certain HP printers on parallel ports to report printer status.

That so, if I was able to TX (ie print) instructions down the dp-100s 9102 port (serial) to my serial device, currently a cisco router, nothing would even get received back.

Think this makes this a dead thread, asking the impossible, unless of course someone knows different..

---

