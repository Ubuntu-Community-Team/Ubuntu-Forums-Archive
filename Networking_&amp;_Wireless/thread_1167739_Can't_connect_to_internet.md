---
title: "Can't connect to internet"
date: 2009-05-23
forum: Networking &amp; Wireless
---

### Post by gibbylinks on 2009-05-23
Hi,

I'm running Jaunty on a second hand Toshiba Tecra 9100. I can connect using wireless to my router but only if I set IPV4 settings to Link-Local Only.

I can't connect to the internet, although it has worked previously. Despite several reboots it's stopped working.

I used ndiswrapper and the broadcom bmc4318 driver to get the wireless working.

I think it's something to do with DHCP ?

Any ideas?

Thanks

---

### Post by Iowan on 2009-05-23
Jauntu apparently added support for rfc3442. I doubt it will solve every problem, but bypassing it in */etc/dhcp3/dhclient.conf* made my DHCP work again. Details [here]("http://ubuntuforums.org/showthread.php?t=1156441").

---

### Post by gibbylinks on 2009-05-24
Strange it's working fine this morning no problems. 

Leaves me wondering if it could be something to do with when other family members are connected with there windoze machines.

---

### Post by gibbylinks on 2009-05-28
** Update **

As stated in my first post Tecra 9100 has the Broadcom 4318 wi-fi chip. 

I've ditched NDISWRAPPER and installed B43-FWCUTTER and had no problems sinces.

Connects every time now. :p

---

