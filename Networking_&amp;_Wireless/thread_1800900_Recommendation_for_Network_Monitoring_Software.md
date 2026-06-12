---
title: "Recommendation for Network Monitoring Software?"
date: 2011-07-09
forum: Networking &amp; Wireless
---

### Post by 337 on 2011-07-09
Hello everyone,

I'm having problems with using too much bandwidth and would really appreciate recommendations for software to monitor what's going on.

I presently have computers, a security camera system, and a "sling box" type device connected to my LAN with both Cat-5 and Wi-Fi.  The router accesses the Internet via a satellite modem (Wild Blue).

The computers are running various Windows versions (Vista, Win7, WinXP)... and this machine which is running Ubuntu.

I would like an easy way of monitoring the LAN traffic as well as the traffic through the modem to determine how to keep my "local" activities from eating up my allocated bandwidth with my service provider.

Thanks for your time and expertise.  I look forward to becoming "more Linuxed".

Lee

---

### Post by Grenage on 2011-07-11
> **337 said:**
> Hello everyone,

I'm having problems with using too much bandwidth and would really appreciate recommendations for software to monitor what's going on.

I presently have computers, a security camera system, and a "sling box" type device connected to my LAN with both Cat-5 and Wi-Fi.  The router accesses the Internet via a satellite modem (Wild Blue).

The computers are running various Windows versions (Vista, Win7, WinXP)... and this machine which is running Ubuntu.

I would like an easy way of monitoring the LAN traffic as well as the traffic through the modem to determine how to keep my "local" activities from eating up my allocated bandwidth with my service provider.

Thanks for your time and expertise.  I look forward to becoming "more Linuxed".

Lee

For a quick and basic check, there appears to be a windows application for Wild Blue routers:

[http://realityripple.com/Software/Applications/WildBlue_Bandwidth_Monitor/](http://realityripple.com/Software/Applications/WildBlue_Bandwidth_Monitor/)

As for more 'comprehensive' monitor of bandwidth, that's somewhat trickier.  Post tools will be using SNMP to poll devices, and those will generally give per-port statistics.  The WAN connection is one port, so you won't get a break-down with user/device bandwidth use; you can monitor the user ports, but then you'll be seeing all of the local data as well as the internet data.

That means that you need something to inspect gateway traffic and base reports on source IP addresses - this requires a unit between the gateway and your network.

---

### Post by Lars Noodén on 2011-07-11
> **337 said:**
> ...I would like an easy way of monitoring the LAN traffic as well as the traffic...

[Wireshark](http://www.wireshark.org/) will monitor network traffic.  That might be a place to start.

---

### Post by xiaokaige on 2012-02-29
There are many LAN Monitoring Software in the LAN. For example:
[http://www.tucows.com/preview/600815](http://www.tucows.com/preview/600815)
[http://www.mysuperspy.com/lan-monitoring-software.htm](http://www.mysuperspy.com/lan-monitoring-software.htm)
[http://www.lan-monitoring.com](http://www.lan-monitoring.com)

---

