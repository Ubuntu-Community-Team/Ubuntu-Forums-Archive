---
title: "[SOLVED] External Modems Return Garbage from Remove Resource"
date: 2008-12-04
forum: Networking &amp; Wireless
---

### Post by user2037 on 2008-12-04
Installing the external, US Robotics V.92 modem is easy enough: plug in cables, open Minicom. However, I've noticed that actually communicating with another modem --after connecting-- scrabbles the remote party's response.

Instead of a clean view of their data I see the "`" character repeated. And once the remote party hangs up I see many "`" characters again (perhaps corresponding to the modem result code "NO CARRIER").

When using the same modem, cables, and configuration on a Centos machine I get no data from the remote host. I have also tried the same application configuration and environment with internal, PCI modems. They work as expected with few exceptions (one will not report result codes, but it may be a sloppy or incomplete driver).

The same modem and cables also work with Windows; though, only with much effort.

So it appears there is a problem with how Ubuntu, Centos, and or Minicom are interacting with the external modem.

[edit]Solved by lowering the serial port rate to more closely match the connection rate[/edit]

---

