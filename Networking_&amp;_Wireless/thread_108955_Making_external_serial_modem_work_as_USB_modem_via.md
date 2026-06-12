---
title: "Making external serial modem work as USB modem via R232-usb adapter"
date: 2005-12-27
forum: Networking &amp; Wireless
---

### Post by maerky on 2005-12-27
I'm using Genius External serial modem for my PC Internet connection.  Since Ubuntu does not recognize my laptop's modem, I've decided to try and make my external serial modem work via a R232-usb adapter.  Thing is when I set it up in Gnome-PPP, it detects it as /dev/ttyUSB0, even in wvdial its detected as /dev/ttyUSB0, but when I dial up to my ISP its showing "Modem not responding".  I run the command "dmesg" and its showing the usbserial driver for my adapter and its showing connection to /dev/ttyUSB0.

Other than this, I am running out of ideas on how to initialize connection via this connection.

Help me guys, did I miss some commands to run?  :D 

It will be very appreciated.

---

