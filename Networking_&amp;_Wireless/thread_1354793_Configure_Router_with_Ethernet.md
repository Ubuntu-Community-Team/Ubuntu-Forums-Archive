---
title: "Configure Router with Ethernet"
date: 2009-12-14
forum: Networking &amp; Wireless
---

### Post by kakashi_12 on 2009-12-14
Can you configure a cisco router with a straight through or cross over ethernet, through the console port? Instead of using a com cable.
 
How would you talk to it? With HyperTerminal.

---

### Post by linux6994 on 2009-12-14
To connect via the serial management port:
You need a serial DB9 to RJ45 null 9600, 8, 1. Do you have a serial port on your PC most laptops today do not, in which case you need a USB to DB9.

On a net management port you would use telnet via a crosover cable to the ip management console.

Good Luck.

[http://www.petri.co.il/csc_how_to_use_hyperterminal_with_cisco_routers_and_switches.htm](http://www.petri.co.il/csc_how_to_use_hyperterminal_with_cisco_routers_and_switches.htm)

---

### Post by kakashi_12 on 2009-12-14
The serial cables we have won't reach the PC from the rack. So we want to make a long ethernet cable. crossover or straight through.

---

### Post by kakashi_12 on 2009-12-14
Or use an adapter from Console to USB. Would it be specified in Putty as COM1, COM2, USB, etc?

---

