---
title: "how to configure your pc to act as router"
date: 2011-04-27
forum: Networking &amp; Wireless
---

### Post by hemantparmar on 2011-04-27
I have pc running ubuntu 10.04 connected in a LAN now i am getting internet over the LAN but not the other computer and i want to configure my pc such that i am able to direct the traffic from other pc in LAN so that they can connect to the internet...... is there a way to do say plz help me out .....

---

### Post by deconstrained on 2011-04-28
You have 2 NIC's, correct?

Turn on ipv4 forwarding using sysctl (and modify /etc/sysctl.conf so the settings persist between reboots). Set up your firewall with packet forwarding rules. Set up/configure dnsmasq to serve IP's on a private subnet controlled by the inward-facing NIC.

It's a long but rewarding process. And there are wiki pages/forum posts available for it:
[http://ubuntuforums.org/showthread.php?t=119787](http://ubuntuforums.org/showthread.php?t=119787)
[https://help.ubuntu.com/community/Router](https://help.ubuntu.com/community/Router)
I've never done it for Ubuntu but have for Arch Linux;
[https://wiki.archlinux.org/index.php/Simple_stateful_firewall_HOWTO#Setting_up_a_NAT_gateway](https://wiki.archlinux.org/index.php/Simple_stateful_firewall_HOWTO#Setting_up_a_NAT_gateway)
[https://wiki.archlinux.org/index.php/Router](https://wiki.archlinux.org/index.php/Router)
[https://wiki.archlinux.org/index.php/Internet_Share](https://wiki.archlinux.org/index.php/Internet_Share)
Most of those directions apply to configuring the Linux kernel/IPtables and thus would be the same for any distribution of GNU/Linux.

---

