---
title: "OpenVPN &quot;connection attempt timed out&quot; error when using Network Manager"
date: 2013-01-07
forum: Networking &amp; Wireless
---

### Post by sfritz on 2013-01-07
Hi all,

When I connect to our OpenVPN server using openvpn from the shell everything works fine. We use username and password authentication.

When I try to use the Network Manager I always get an error:

The VPN connection 'Aurea' failed because the connection attempt timed out

from /var/log/syslog:

Jan  7 12:40:41 nbstefan NetworkManager[963]: <info> Starting VPN service 'openvpn'...
Jan  7 12:40:41 nbstefan NetworkManager[963]: <info> VPN service 'openvpn' started (org.freedesktop.NetworkManager.openvpn), PID 5219
Jan  7 12:40:41 nbstefan NetworkManager[963]: <info> VPN service 'openvpn' appeared; activating connections
Jan  7 12:40:41 nbstefan NetworkManager[963]: <info> VPN plugin state changed: init (1)
Jan  7 12:40:42 nbstefan NetworkManager[963]: <info> VPN plugin state changed: starting (3)
Jan  7 12:40:42 nbstefan NetworkManager[963]: <info> VPN connection 'Aurea' (Connect) reply received.
Jan  7 12:40:42 nbstefan nm-openvpn[5224]: OpenVPN 2.2.1 x86_64-linux-gnu [SSL] [LZO2] [EPOLL] [PKCS11] [eurephia] [MH] [PF_INET6] [IPv6 payload 20110424-2 (2.2RC2)] built on Oct  8 2012
Jan  7 12:40:42 nbstefan nm-openvpn[5224]: WARNING: No server certificate verification method has been enabled.  See [http://openvpn.net/howto.html#mitm](http://openvpn.net/howto.html#mitm) for more info.
Jan  7 12:40:42 nbstefan nm-openvpn[5224]: NOTE: the current --script-security setting may allow this configuration to call user-defined scripts
Jan  7 12:40:42 nbstefan nm-openvpn[5224]: UDPv4 link local: [undef]
Jan  7 12:40:42 nbstefan nm-openvpn[5224]: UDPv4 link remote: [AF_INET]107.23.16.62:1194
Jan  7 12:41:21 nbstefan NetworkManager[963]: <warn> VPN connection 'Aurea' (IP Config Get) timeout exceeded.
Jan  7 12:41:21 nbstefan NetworkManager[963]: <info> Policy set 'Wired connection 1' (eth0) as default for IPv4 routing and DNS.
Jan  7 12:41:21 nbstefan nm-openvpn[5224]: SIGTERM[hard,] received, process exiting
Jan  7 12:41:26 nbstefan NetworkManager[963]: <info> VPN service 'openvpn' disappeared


 

I found this thread: [http://ubuntuforums.org/showthread.php?t=2000376](http://ubuntuforums.org/showthread.php?t=2000376)

And this defect: [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1011991](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1011991)

Could it be that I run into this with Ubuntu 12.10 ?
How can I debug the cause?

Thanks
Stefan

---

### Post by sfritz on 2013-01-08
Has nobody an idea or hint? ):P

---

### Post by ruediger.kupper on 2013-02-25
I have the exact same problem.

---

