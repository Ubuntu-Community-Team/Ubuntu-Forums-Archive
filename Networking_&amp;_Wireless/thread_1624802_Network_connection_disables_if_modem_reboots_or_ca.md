---
title: "Network connection disables if modem reboots or cable is reinserted"
date: 2010-11-18
forum: Networking &amp; Wireless
---

### Post by ukiome on 2010-11-18
Ok. 
So I recently replaced my windows home server with an ubuntu server x64 10.04. It runs on a Asus P5Q pro motherboard which has two Ethernet ports.

The problem I am having is that whenever i disconnect the Ethernet cable and reconnects it or I restart the adsl modem/router the connection seems to disable itself on the server. I can't connect to it by ssh, I can't connect to my wiki on the apache server and not either samba or nfs shares.
I can however access the machine locally and from there either restart the networking service or restart the entire server.

The Ethernet port is called eth0 and I have tried disabling the eth1 port in case the server switches automatically but that doesn't seem to work. 

Any ideas?

---

