---
title: "Name resolution for attached RNDIS device"
date: 2012-05-22
forum: Networking &amp; Wireless
---

### Post by Kai R on 2012-05-22
I have an embedded device (with Windows CE, yeah I know) that connects to a computer via USB RNDIS. On the instrument, there is a DHCP server to configure IPv4 and IPv6 is setup via an ULA and router advertisement. When I attach the instrument to an Ubuntu box, the network interface is created and fully configured as expected for IPv4 and IPv6 (and without driver installation, yay!)

With Windows, I can setup a DNS via DHCP that also points to the instrument and Windows' non-standard nameserver handling allows me to enter the instrument's name into the browser's address bar to access the running web server. This usually uses the AAAA record's IPv6 address, but I really don't care anymore. At the same time, my network's "normal" DNS is used to resolve the internet.

The nice thing is, that I can attach several instruments simultaneously to the same computer. The IPv4 configuration is different on each one (a /30 net), as is the name resolved via DNS, and in IPv6, each instrument uses a different subnet in the common ULA prefix. Windows just asks all known nameservers and one of the instruments will reply with proper A and AAAA records.


Are there choices to make name resolution Just Work (tm) with Ubuntu (and other distributions) as well in this configuration?


Currently, attaching the instrument adds the nameserver to the configuration, but after the standard interface's one, so the authorative "I do not know that name" hinders name resolution. When I change the order of name servers, the internet is not resolved anymore.

---

### Post by alexfish on 2012-05-22
Have you tried resolvconf , but read what it conflicts with before  trying

---

### Post by Kai R on 2012-05-23
The nameserver information successfully lands in resolv.conf, but only the first server listed in there is ever asked. If this one answers "Not found", no other server is asked. That means I can either resolve the internet, or I can resolve one name of one attached instrument and what I can do even depends on the order in which I bring up the network interfaces…

---

