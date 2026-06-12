---
title: "Ubuntu Server behaviour when network cable disconnected"
date: 2013-09-01
forum: Networking &amp; Wireless
---

### Post by Jackson_Wiegman on 2013-09-01
I have a bare bones Ubuntu 13.04 Server installation, with a static network setup in /etc/network/interfaces. On boot, my network comes up and everything is OK. However, if I remove the Ethernet cable, and plug it back in, the interface does not come back up with an IP address. The port is OK however, I have activity light and can even see traffic on it using tcpdump/Wireshark. I have to bring down and bring back up the interface manually to get the IP address on it.

As further odd behaviour, I tried running ```
sudo service networking restart
```. That brings down the interface but then just appears to hang. If I break out using CTRL-C, and bring the interface back up with ifup, then it comes back up... and does so even if I unplug and re-plug the networking cable, i.e. the behaviour I would expect and want.

Any advice on how to get it to do this automatically?

---

### Post by Jackson_Wiegman on 2013-09-01
I've been able to get around this by installing and running ifplugd. I find it odd that Ubuntu isn't set up by default to reinitialize an interface though.

---

