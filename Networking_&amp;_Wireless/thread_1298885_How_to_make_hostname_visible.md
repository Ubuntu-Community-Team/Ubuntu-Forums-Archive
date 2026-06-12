---
title: "How to make hostname visible"
date: 2009-10-23
forum: Networking &amp; Wireless
---

### Post by ukkuku3d on 2009-10-23
My computer is connected to a Fritz!Box and got IP configuration via DHCP. Also a hostname is set up.
But whe I look via nmap or within my Fritz!Box router, I can only see the IP address but not the hostname.
Another laptop (A Mac 10.5) clearly shows his host-name within nmap.

This is important for me, because I want to connect a dozent or more Ubuntu machines temporary to the router and I need to identify them.

Any idea how to make the hostname visible in nmap or with the router if no DNS is used?

Thanks
  Achim

---

### Post by Dr_Hugh on 2009-10-23
You can discover the hostname by typing 'hostname' into a terminal windows. You can change the name with hostname but I am not sure of the syntax. Try hostname --help in a terminal.

---

### Post by Iowan on 2009-10-23
Check [here]("http://ubuntuforums.org/showthread.php?t=1288328") for a similar thread.  Hope the info helps.

---

### Post by ukkuku3d on 2009-11-07
No, it is simply not working. I've added my host-name in the /etc/dhcp3/dhclient.conf file, even rebooted, but still it is no name shown.

Any other proposal???

Thanks a lot
  Achim

---

