---
title: "[SOLVED] Help needed - OpenVPN Bridge"
date: 2008-12-31
forum: Networking &amp; Wireless
---

### Post by dipeshmehta on 2008-12-31
Hello,

I have setup OpenVPN Bridge as per following [http://ubuntuforums.org/showthread.php?t=752127](http://ubuntuforums.org/showthread.php?t=752127)

I have been using Ubuntu 8.04LTS, with plain iptables, no other firewall is there.  My linux servers are behind ADSL router (from which I forward appropriate ports to linux servers)

The setup runs fine and I am able to ping the tunnel from eitherside of my linux server.  but I am not able to ping or access hosts on network another side of VPN bridge.

My setup is like this:

networkA (192.168.1.xxx)
|
Linux Server running OpenVPN A (192.168.1.2)
|
ADSL RouterA
|
|
ADSL RouterB
|
Linux Server running OpenVPN B (192.168.2.2)
|
NetworkB (192.168.2.xxx)

Any suggestions / guidance welcome.

Dipesh

---

### Post by mpokrywka on 2009-01-01
Preface: I assume you used "Part 1" of howto

Does both your "Linux Servers" have 2 network cards, one for LAN, one for Internet?
If not, then your "Server A" is not default gateway for other hosts in "networkA" and packets from "NetB" will be routed back through "RouterA", instead of VPN on "Server A".
That howto lacks one step that would solve this problem - on servers use:
**iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE**
("eth0" should be interface with 192.168.1.x address)
This means: anything that goes to LAN will have LAN source.
Pros: Communication with "NetworkB" works. Both ways.
Cons: All connections from "NetworkB" will look on host in "NetworkA" as if "Server A" started it.

---

### Post by dipeshmehta on 2009-01-02
> **mpokrywka said:**
> on servers use:
**iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE**


Sorry, this doen't work

Dipesh

---

### Post by mpokrywka on 2009-01-02
Hmm, and your routing is?
(on server A and server B, after vpn is established, run **ip route**)

---

### Post by dipeshmehta on 2009-01-09
I unsuccessfully tried some other setup also, and then returned to my original setup.  Unbelievablly now it works OK.  I don't know, where I was wrong the first time I set it up but now OpenVPN is working very fine, at both places.

Thanks guys for helping me when I was stucked.

Dipesh

---

