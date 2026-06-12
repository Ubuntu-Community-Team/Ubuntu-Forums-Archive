---
title: "Dialup USB Serial to Faxmodem"
date: 2012-02-19
forum: Networking &amp; Wireless
---

### Post by borgward on 2012-02-19
I need to connect laptop to serialport of USR Faxmodem's serial port, so I can dialout.

USB to serial adaptor:

lsusb
Bus 005 Device 002: ID 067b:2303 Prolific Technology, Inc. PL2303 Serial Port

Dell Inspiron 1520 
Ubuntu 10.04

I did have my LAN connected to dialup:
Linksys WRT54G to DLink DI-704 w/serial port to USR External Faxmodem. The DLink is now defunct.

I connected the USB/serial adaptor to the Faxmodem, but do not know how to start the dialup process.

I am considering replacing the DLink w/Cisco E2100L or DLink ADSL 2+ Modem. Both have 4 ethernet ports and a USB port which I could use a USB/Serial connector to connect to the USR Faxmodem.

---

### Post by Perkins on 2012-02-21
GnomePPP is a good graphical modem dialler and PPP initiator.  wvdial is the almost-always-installed command-line modem dialler and PPP initiator.  Both programs have online help either in the Gnome help files or under man wvdial.

Most USB-serial adapters will show up as /dev/ttyUSB*.  Put that in for the modem device in either program and it usually just works.  You may need to adjust other settings based on your adapter and your modem, but see how far just telling it to go gets you.

Post back any further questions and I'll see what I can do to help.

---

