---
title: "ssh bandwidth usage"
date: 2008-12-24
forum: Networking &amp; Wireless
---

### Post by chmac on 2008-12-24
Hola,

I'm looking to find out how much bandwidth a "typical" ssh session uses. I'm curious to know if screen increases bandwidth usage or has no effect.

I'm considering various forms of satellite broadband, one option provides 2.4kbps so I'm trying to get a handle on whether I can use ssh over such a connection.

Can anyone suggest a method of monitoring the bandwidth usage of an individual program in real time? I found [this (link)]("http://lists.clug.org.za/pipermail/clug-chat/2004-November/008461.html"), which might work, but I'd prefer something that monitored usage in real time if possible.

---

### Post by gctaylor1 on 2008-12-24
You could use the program Ethereal/Wireshark and set up filters to monitor just the destination ssh port.  I believe there's a summary that you could monitor.

The program iptraf also displays this type of information real time.  You could also set up a filter in this program to watch just the ssh traffic.

As an FYI - ssh by design is intended to produce a consistent level of traffic to thwart traffic analyzers intended to discover usage patterns and thus base an attack on this information.

---

