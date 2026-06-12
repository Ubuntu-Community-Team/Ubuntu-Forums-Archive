---
title: "Telnet/SSH to UBUNTU workstation fails"
date: 2009-04-21
forum: Networking &amp; Wireless
---

### Post by malekana on 2009-04-21
i have installed UBUNTU on VMware and i'm trying to manage it with SMS 2003 using QMX.

when i try to connect to the UBUNTU workstation from Windows machine using either Telnet/SSH it says connection failed.

when i user Putty it says Fatal error : connection refused.

please can someone guide me on how to enable telnet/ssh to ubuntu workstation? 

i installed tennetd also but for no help .

---

### Post by Anthon on 2009-04-21
By default Ubuntu does not install the ssh deamon. You should make sure you do
  sudo apt-get openssh-server
Have you done so?

---

