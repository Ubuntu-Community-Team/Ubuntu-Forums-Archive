---
title: "Firestarter ignoring policies in 9.04"
date: 2009-04-27
forum: Networking &amp; Wireless
---

### Post by Zerocool3001 on 2009-04-27
After upgrading to 9.04 firestarter is no longer recognizing the custom policies I've set. For instance I have a policy to allow all connections inbound from "192.168.0.1/24" (which allows connections from all machines on the internal network). This worked in 8.10, but after the upgrade I get a timeout on any connections, as it should be for any incoming connection that was *not* in a policy. I have to turn the firewall off just to ssh in.

Any help would be much appreciated.

---

### Post by jordanaustin on 2009-05-07
I have to second this, something isn't right since the update. If I boot up ubuntu and open my uTorrent everything is good, ports forwarded, green checkmark, nice speeds. I open firestarter up and my speeds drop down, I get a red checkmark, and it says I need to change my listening port.

  My policy has been and is always set to allow that port. I close firestarter, speeds jump right back up, green checkmark again.

---

### Post by Zerocool3001 on 2009-05-14
I should add that I have modified Firestarter to allow multicast broadcasts by editing /etc/firestarter/user-pre to include the lines:

$IPT -A INPUT -p udp --dport 5353 -d 224.0.0.251 -j ACCEPT
$IPT -A OUTPUT -p udp --dport 5353 -d 224.0.0.251 -j ACCEPT

---

