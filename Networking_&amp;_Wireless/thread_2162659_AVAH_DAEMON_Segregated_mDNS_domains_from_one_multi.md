---
title: "AVAH DAEMON: Segregated mDNS domains from one multi-homed host"
date: 2013-07-15
forum: Networking &amp; Wireless
---

### Post by misterwiley1 on 2013-07-15
Greetings all,   We're attempting to enable a number of mDNS advertised services on our campus  wide wireless network, most notably airplay.  In our case, the airServers would  sit on our wired network, so we need to advertise the services manually either  with DNS-SD or mDNS on the wireless side.  We've gotten that working using  static service advertisements in avahi and it's pretty slick, but we have a  scaling problem.   We have potentially 150 AirServer hosts in a variety of classrooms around the  campus.  If we were to enable all of them, the list to choose from on iPads  would be outrageously large (to say nothing of students thoroughly enjoying  taking over an AirServer from across campus when a faculty member forgets to  change the password).     What we would like to do is segregate our wireless network on a single vlan per  building basis to form 27 mDNS segments and then run avahi to advertise the  services in each segment, preferably on a single, multi homed host with access  to all of the segments.   I was hoping that avahi-daemon would take a parameter in the avahi-daemon.conf  that points to a unique services directory, so that I could have multiple  config files, each with a different allow-interfaces clause and a pointer to a  different services directory, but that doesn't appear to be a configurable  option.     I was thinking of chroot jailing multiple copies of avahi, but that seems  really kludgy.     Am I missing some more obvious strategy to handle this without creating 27  separate hosts?   Thanks much!   JD

---

