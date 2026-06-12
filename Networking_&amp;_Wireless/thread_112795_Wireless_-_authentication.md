---
title: "Wireless - authentication"
date: 2006-01-05
forum: Networking &amp; Wireless
---

### Post by iansyngin on 2006-01-05
Having some more problems with Wireless and looking for some assistance.
I have managed to connect to my router and browse the web etc ok but when enabling options for the authentication protocols such as wep i completely disconnects from router.
This means i have to wire from laptop to router and disable these protocols to get wireless back up and running. Obviously i can't keep doing this for security reasons not that i have anything to hide.
it's an xytel.
any ideas anyone?

---

### Post by Lambert on 2006-01-05
Post the output of these commands here

sudo lshw -C network

lspci -v | grep Eth

Need more information on the chipset and driver being used.

Also, what kind of wep settings are you trying to use? open or shared key? hexadecimal or ascii key format? Do you have an option to use different key numbers, if so which one are you trying to use?

---

