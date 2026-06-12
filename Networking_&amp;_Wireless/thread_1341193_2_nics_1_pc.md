---
title: "2 nics 1 pc"
date: 2009-11-29
forum: Networking &amp; Wireless
---

### Post by mykelmykel on 2009-11-29
It took me days, on Karmic Koala 9.10 to get two nics, one pc working.

One of the nics must stay on LAN and the other on WAN. Below are the steps I took to making it work. There are plenty of help on this issue but none seem to work for me. If you follow the below,you may be able to get yours working.

DO THIS TO GET DUAL NIC WORKING ON LAN AND WAN
1. Go to sudo gedit /etc/default/NetworkManager
2. Add:
NETWORKING=yes
HOSTNAME=(ADD YOUR PC id here. The one you elect at OS install)
GATEWAY=(ADD YOUR WAN IP ADDRESS HERE)

IF IT STILL DOES NOT WORK:

1. OPEN NETWORK ADMIN USING ALT. F2
2. ON ETH1 ENABLE ROAMING ENABLED, i.e Roaming box checked. This is your WAN.
3. ON ETH0 (LAN) ADD NIC IP ADDRESS. ROAMING NOT ENABLE, i.e Roaming box unchecked. This is your LAN.

Change eth0 1 and eth0 as necessary.

---

