---
title: "OpenVPN connection speed"
date: 2011-07-31
forum: Networking &amp; Wireless
---

### Post by jstarup on 2011-07-31
Activating my OpenVPN connection leads to a considerable loss in performance. It does establish the connection, but a download would e.g. go from 405 kB/s to less than 1 kB/s with the VPN turned on.

I've updated to 11.04 in April and until recently everything has been working well. I have not made any changes in my configuration in that time nor changed router, ISP etc. The only thing I've done now is that I've disabled and removed the firewall, but that didn't have any effect on performance.

the VPN provider assures me that the problem isn't at their end. Other clients on the same server has not experienced any issues, and they even rebooted the VPN daemon bc I've kept complaining.

any help would be much appreciated


-----

Enter Auth Username:xxxxx
Enter Auth Password:
Sat Jul 30 15:31:15 2011 NOTE: the current --script-security setting
may allow this configuration to call user-defined scripts
Sat Jul 30 15:31:15 2011 /usr/bin/openssl-vulnkey -q -b 2048 -m
<modulus omitted>
Sat Jul 30 15:31:15 2011 Control Channel Authentication: using
'ta.key' as a OpenVPN static key file
Sat Jul 30 15:31:15 2011 LZO compression initialized
Sat Jul 30 15:31:15 2011 UDPv4 link local: [undef]
Sat Jul 30 15:31:15 2011 UDPv4 link remote: [AF_INET]85.17.167.201:443
Sat Jul 30 15:31:15 2011 WARNING: this configuration may cache
passwords in memory -- use the auth-nocache option to prevent this
Sat Jul 30 15:31:36 2011 [vpvault] Peer Connection Initiated with
[AF_INET]85.17.167.201:443
Sat Jul 30 15:31:38 2011 TUN/TAP device tun0 opened
Sat Jul 30 15:31:38 2011 /sbin/ifconfig tun0 10.189.0.150 pointopoint
10.189.0.149 mtu 1500
Sat Jul 30 15:31:38 2011 /etc/openvpn/update-resolv-conf tun0 1500
1558 10.189.0.150 10.189.0.149 init
Sat Jul 30 15:31:38 2011 Initialization Sequence Completed

------

---

