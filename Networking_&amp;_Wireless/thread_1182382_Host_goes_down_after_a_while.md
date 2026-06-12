---
title: "Host goes down after a while"
date: 2009-06-08
forum: Networking &amp; Wireless
---

### Post by maalls on 2009-06-08
Hello,

Please Help, I got the following issue:

I have a network with two computers: 
A ubuntu 9.04 server installed, and ssh
192.168.0.33 is a mac os machine

If I launch ssh service, I can connect from the mac to the server, but after a while of none activity, the connection get closed by the host. After that, I can not ssh ("Operation timed out") nor ping ("Host is down") the ubuntu machine.
But on the ubuntu machine side, I can still ping the mac os machine.

If I restart the network on the ubuntu machine, everything work fine again until host close the connection again in case of none activity...

Any idea on how I could keep the server always up on running? Ubuntu is freshly installed and I hadnt done any specific change on config files except network config.

Thanks for your help

---

### Post by superprash2003 on 2009-06-09
do you connect via ip or hostname?

---

### Post by Iowan on 2009-06-09
Although unlikely, the BIOS may have a power management setting that downs the NIC. (or ACPI might be naughty...)

---

### Post by maalls on 2009-06-09
@superprash2003 I connected via IP.

A strange thing is that when the host disconnect and cant be ping by client machine, the server can still ping client machine...I dont understand...

---

