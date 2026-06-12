---
title: "wireless problem"
date: 2009-08-31
forum: Networking &amp; Wireless
---

### Post by cmcanulty on 2009-08-31
I installed Ubuntu on one of our library computers. It connects to the wireless network OK but won't go to the internet, seems impossible. Any fixes? Thanks

---

### Post by hal10000 on 2009-08-31
Is this mashine in a local area network?
If you are in a lan, than the most problems are:
1.) How do you get your ip-address (DHCP or manual setup)?
2.) Do you have an entry for your nameserver in your /etc/resov.conf file? Verify this by typing cat /etc/resov.conf in a terminal window. If the file is empty, ten it' a nameserver problem.
Namserver problems usually occur if you set up a static ip address by manually configuring a network interface, if you used DHCP to configure your network, then the nameserver's ip-address might be received automatically.

---

### Post by shredder12 on 2009-08-31
do you use a proxy server to access internet..
and are you able to ping any of the lan computers (jst to make sure that you are at least connection to LAN).

---

