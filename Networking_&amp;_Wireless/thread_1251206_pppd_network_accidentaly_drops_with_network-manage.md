---
title: "pppd network accidentaly drops with network-manager"
date: 2009-08-27
forum: Networking &amp; Wireless
---

### Post by Shiba on 2009-08-27
Hi all,
I have a little problem with my ethernet-connected adsl modem. Sometimes, especially when I'm using torrent, my connection just drops. Watching **/var/log/messages** I found that the problem is that:

```
pppd[4182]: No response to 3 echo-requests
pppd[4182]: Serial link appears to be disconnected.
```I googled around to work it out and I tried changing the values for **lcp-echo-interval** and **lcp-echo-failure** in **/etc/ppp/options** to:

```
lcp-echo-interval 0
lcp-echo-failure 0
```so that it wouldn't disconnect me when it gets no replies. Well, I admit that I don't whether this works or not when a connection is started by "pon" or "pppd call", but I know for sure that it doesn't with network-manager.

[IMG]http://dl.getdropbox.com/u/737114/nm.png[/IMG]

That is what happens:

"Send PPP echo packets" checked
```
NetworkManager: <debug> [1251384152.221559] nm_ppp_manager_start(): Command line: /usr/sbin/pppd nodetach lock nodefaultroute user eu36616403@tele2.it plugin rp-pppoe.so nic-eth0 noauth nodeflate usepeerdns mru 1492 mtu 1492 **lcp-echo-failure 5** **lcp-echo-interval 30** ipparam /org/freedesktop/NetworkManager/PPP/5 plugin /usr/lib/pppd/2.4.4/nm-pppd-plugin.so
```"Send PPP echo packets" unchecked
```
NetworkManager: <debug> [1251384283.144738] nm_ppp_manager_start(): Command line: /usr/sbin/pppd nodetach lock nodefaultroute user eu36616403@tele2.it plugin rp-pppoe.so nic-eth0 noauth nodeflate usepeerdns mru 1492 mtu 1492 **lcp-echo-failure 3** **lcp-echo-interval 20** ipparam /org/freedesktop/NetworkManager/PPP/8 plugin /usr/lib/pppd/2.4.4/nm-pppd-plugin.so
```I really don't understand why it still tries to send echo packets even if I tell it not to it. It would be nice if it at least used my settings in **/etc/ppp/options**.
So, coming to the final question, does anyone know how to use the values I want with network-manager for those two parameters?

**UPDATE**: Even if I try to connect with "pon" it still hangs, saying:

> pppd[21830]: LCP terminated by peer

and nothing else :\

---

### Post by krychek on 2009-10-24
Related LP bug report:

[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/310035]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/310035")

---

### Post by Shiba on 2009-12-06
Same problem with Ubuntu 9.10.

---

### Post by biji on 2010-01-03
This happened when traffic full such as bittorrent download.

---

