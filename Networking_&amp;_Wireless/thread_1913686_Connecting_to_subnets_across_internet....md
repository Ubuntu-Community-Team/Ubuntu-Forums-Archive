---
title: "Connecting to subnets across internet..."
date: 2012-01-23
forum: Networking &amp; Wireless
---

### Post by IslandBill on 2012-01-23
Hello all,

I am running a brand new WISP (Wireless Internet Service Provider), and I need to be able to remotely administer access points behind the NAS on my various hotspots.  Each hotspot is running coovachilli, and the APs have static private IPs.  Each hotspot has a different private subnet beginning with 192.168.  Each NAS has a static IP from our ISP.  Here is a picture of what  I need to do:


192.168.1.0 -> NAS(gateway) X.X.X.X -----INTERNET------ NAS(gateway) Y.Y.Y.Y---> 192.168.2.0

While I can reliably connect over the WAN to Y.Y.Y.Y and administer that server via web or ssh, I need to be able to administer the static private IPs (the radio devices) on 192.168.2.0 from the 192.168.1.0 LAN via my web browser (this is due to the nature of the firmware on the devices), as well as being able to bring all of my SNMP under one "roof".

SPECIFIC QUESTION:  How can I define the routing on NAS X... and NAS Y...  to allow me to simply web or ssh or whatever 192.168.2.x from the 192.168.1.x side?  NAT?  VPN?  PPTP?  Which would be the best solution?

Many thanks in advance, folks :)

---

### Post by IslandBill on 2012-01-23
bump in the road....

---

