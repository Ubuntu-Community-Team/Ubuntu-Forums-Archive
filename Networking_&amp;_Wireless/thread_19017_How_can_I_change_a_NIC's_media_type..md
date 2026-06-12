---
title: "How can I change a NIC's media type."
date: 2005-03-09
forum: Networking &amp; Wireless
---

### Post by c0rrupt on 2005-03-09
I want to change the media type of eth0 to 10baseT Full Duplex, and hopefully have Ubuntu do this at every boot.  How can I do this?

---

### Post by alastair on 2005-03-10
Look into a program called "ethtool". Your driver might support it.

---

### Post by c0rrupt on 2005-03-10
I don't have that installed on my system.  I used mii-tool instead (sudo mii-tool eth0 --advertise 10baseT-FD).  Only thing is now, how can I make Ubuntu do this at startup before it tries to setup the connection via DHCP?

---

### Post by alastair on 2005-03-10
OK - I'm a new Debian user but there appear to be "pre" network device scripts under :

/etc/network

e.g.

/etc/network/if-pre-up.d/

The wireless-tools seem to do this. Worth playing with it perhaps.

---

