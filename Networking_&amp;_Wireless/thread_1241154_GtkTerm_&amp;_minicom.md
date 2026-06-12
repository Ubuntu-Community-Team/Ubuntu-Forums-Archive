---
title: "GtkTerm &amp; minicom"
date: 2009-08-15
forum: Networking &amp; Wireless
---

### Post by trentoncain on 2009-08-15
I'm trying to console into a Cisco router using a USB to Serial cable. When I run "dmesg | grep tty" I get "[ 7226.573142] usb 5-1: pl2303 converter now attached to ttyUSB0".

When I fire up GtkTerm and under configuration/port and change it to the /dev/ttyUSB0 all I get is a blank screen. I've saved it as the default and restarted but still a blank screen. After configuring minicom as per the instructions at [https://help.ubuntu.com/community/CiscoConsole](https://help.ubuntu.com/community/CiscoConsole) I get the same blank screen as I did for GtkTerm.

Any ideas? It works fine under XP/Vista with putty. This is for Ubuntu 9.04 all updated.

Thanks in advance!

---

### Post by trentoncain on 2009-08-15
NVM, it worked after a computer restart. ???

---

