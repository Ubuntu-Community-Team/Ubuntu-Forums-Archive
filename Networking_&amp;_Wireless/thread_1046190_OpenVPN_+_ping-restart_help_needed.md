---
title: "OpenVPN + ping-restart help needed"
date: 2009-01-21
forum: Networking &amp; Wireless
---

### Post by dipeshmehta on 2009-01-21
Hello,

I have setup OpenVPN to bridge networks as per following [http://ubuntuforums.org/showthread.php?t=752127](http://ubuntuforums.org/showthread.php?t=752127) Part1

I have been using Ubuntu 8.04LTS, with plain iptables, no other firewall is there. My linux servers are behind ADSL router (from which I forward appropriate ports to linux servers)

I have setup at both side as guided into the said howto.  The setup runs fine thanks to spaceteddy, and I am able to surf the both networks without having any trouble when internet link on both side is working.

The problem starts when internet link is down on either side, and when it becomes available openvpn instances do not recognise it anyway, and I need to restart the daemon on both side.  I have tried ping 10 / ping-restart 120, ping 100 / ping-restart 1200, and even removing these lines, the problem continues when link is down for a long time.

Can anybody help me getting out of this.

Dipesh

---

