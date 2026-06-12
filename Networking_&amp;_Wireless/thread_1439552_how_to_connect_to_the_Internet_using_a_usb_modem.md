---
title: "how to connect to the Internet using a usb modem"
date: 2010-03-26
forum: Networking &amp; Wireless
---

### Post by fxlovers on 2010-03-26
I want to share about "how to use the usb modem in Ubuntu"

1. install usb modeswitch
2. install wvdial
-----When all was installed in our ubuntu----
1. plug your usb modem, wait until the modem legible, appears the modem icon on the desktop.
2. right click on the icon, select "eject"
3. open a terminal, type

[quote]
fxlovers @ fxlovers-laptop: ~ $ lsusb
Bus 005 Device 001: ID 1d6b: 0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b: 0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b: 0001 Linux Foundation 1.1 root hub
Bus 002 Device 007: ID 2015:0001 <==== see this section, this is information about the modem that we use
Bus 002 Device 001: ID 1d6b: 0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b: 0001 Linux Foundation 1.1 root hub
[/ quote]

4. type
fxlovers @ fxlovers-laptop: ~ $ sudo modprobe usbserial vendor = 0x2015 product = 0x0001

[quote]
vendor = 0x2015 product = 0x0001 <=== change value in accordance with your modem information
[/ quote]

5. type

[quote]
fxlovers @ fxlovers-laptop: ~ $ sudo gedit / etc / wvdial.conf
[/ quote]
setting according to the operators used

6. type
[quote]
fxlovers @ fxlovers-laptop: ~ $ sudo wvdial
[/ quote]

done.
:popcorn:

---

