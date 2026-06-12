---
title: "Internet connection has been lost.."
date: 2011-06-24
forum: Networking &amp; Wireless
---

### Post by Cap_Sot on 2011-06-24
Hello dear Ubuntu users,
i upgraded yesterday my ubuntu OS to version 11.04 and today when i powered on my computer i realised that there was no internet connection.my pc connects to the net using an ethernet cable.
the weird thing is that i have access to the internet from my laptop (wireless) and from my mobile as well.
Already tried to ping my router and the message i get says "connect: Network is unreachable".Also the command "route" shows nothing..

Any suggestions would be appreciated,
Sotiris

---

### Post by Cap_Sot on 2011-06-24
Well, no replies so far but i managed to work around this problem..it seems that somehow the /etc/network/interfaces file didn't include the proper content. once i added the 2 following lines and restarted the computer everything was in place..

auto eth0
iface eth0 inet dhcp

Anyway, problem solved!

---

