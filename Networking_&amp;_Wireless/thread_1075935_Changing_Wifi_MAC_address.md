---
title: "Changing Wifi MAC address"
date: 2009-02-20
forum: Networking &amp; Wireless
---

### Post by spliffeh on 2009-02-20
I'm trying to change my wifi's MAC address using commands like:

[B]ifconfig eth0 down hw ether 00:80:48:BA:A1:20
ifconfig eth0 hw ether 00:00:00:00:00:01[/B]

etc etc... Regardless of what mac address I use, the response I get is:
**SIOCSIFHWADDR: Invalid Argument**

From what I can figure out, this Wifi card (INTEL Wireless 2915ABG) does not support mac address changes. Could anyone confirm?

Is there another way I can get this done? Note I'm using Sabayon Linux right now, but a year or so ago using Ubuntu I seem to remember a command like 'wlanconfig' that would allow me to create logical copies of eth0 called wifi0 wifi1 etc etc and assign different mac addresses to them. My memory is foggy though, could anyone refresh me?

Is there a way to spoof my mac address if my wifi card/drivers do not support this function?


Thanks in advance.

---

### Post by kevdog on 2009-02-21
There is a program known as macchanger. Its in the repositories:

sudo aptitude install macchanger

---

