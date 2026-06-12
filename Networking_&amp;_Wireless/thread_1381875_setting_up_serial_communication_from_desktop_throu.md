---
title: "setting up serial communication from desktop through USB  port in linux terminal"
date: 2010-01-15
forum: Networking &amp; Wireless
---

### Post by abhinav.p on 2010-01-15
I am new to linux terminal programming and all but i want to set up a simple serial communication from my desktop through USB port. The actual idea to to write some data in the terminal and build a terminal program that sends the data to the usb port with a fixed baud rate. are there ready made terminal programs available for this simple communication?or atleast any Graphical tools which could help me build and design such a terminal in ubuntu 9.04?

---

### Post by =not4prophet= on 2010-01-15
you might try minicom.  It's available through the repos and works with any tty device including USB serial port adapters.  It's what I use for configuring any hardware that is configured through a serial connection, i.e. routers, switches, and firewalls.

---

### Post by abhinav.p on 2010-01-15
this minicom is grahical interface? hope i dont have to spend more time on it understanding configuring and all. i want to connect the USB to RS232 interface on a board for embedded programming.

---

### Post by buster2209 on 2010-01-15
> **abhinav.p said:**
> this minicom is grahical interface? hope i dont have to spend more time on it understanding configuring and all. i want to connect the USB to RS232 interface on a board for embedded programming.

If you don't like minicom, check out pyserial.  You need to download the pyserial files from the repo but setting up a RS232 connection via the terminal window will take you about 5 minutes to understand.

[This]("http://pyserial.sourceforge.net/shortintro.html") page helps if you decide to use this route.

Have you also managed to connect your USB to RS232 adaptor to Linux?

Also, in case you haven't discovered it yet, [PIKLAB]("http://piklab.sourceforge.net/") is an awesome embedded systems IDE available in the repo too.

---

### Post by ddane on 2012-09-24
I have problem with similar purpose. I want to configure a router through USB port on my desktop and to Serial port on router.

I learned how to configure my serial port using terminal on my Ubuntu (10.04 LTS) but problem is:

- When I disconnect from terminal, Ubuntu looses information about which  USB port is mapped to Serial port and I need to reconfigure it all the time. I saved my configuration as default but it still keeps change, once is USB0 and next time I have to set USB1.

This is printout from terminal window:

[I]A -    Serial Device      : [COLOR="Red"]/dev/ttyUSB0[/COLOR]
B - Lockfile Location     : /var/lock
C -   Callin Program      :
D -  Callout Program      :
E -    Bps/Par/Bits       : 9600 8N1
F - Hardware Flow Control : No
G - Software Flow Control : No

Change which setting?[/I]

---

