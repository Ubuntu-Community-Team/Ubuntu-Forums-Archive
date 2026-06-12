---
title: "Openswan needs reboots for config to work"
date: 2011-03-22
forum: Networking &amp; Wireless
---

### Post by Chrus on 2011-03-22
I've set up Openswan at home to connect to a Linksys RV082 at the office. Had some trouble in the beginning, but got there in the end. But this leftsourceip= thing is confusing me a little.

If i leave it out of the config, the ipsec connection will come up, but I cant ping anything. From 150.101.X.X icmp_seq=1 Packet filtered. That makes sense.

But why is it that when I add leftsourceip=172.16.10.1 to my config file, and run /etc/init.d/ipsec restart I get the same thing. Packets being filtered again. Its not until I reboot that things start working properly.

Rebooting evertime a new connection is added to the config file is going to get old rather quickly. Is there another service I need to restart in order to get the ipsec connection working without rebooting?

Thanks

---

