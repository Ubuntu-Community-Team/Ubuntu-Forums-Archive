---
title: "VPN not working via Network Manager"
date: 2012-07-05
forum: Networking &amp; Wireless
---

### Post by cesera on 2012-07-05
I am trying to set up a VPN connection via Network Manager and it keeps timing out with the following log entries:
```
Jul  5 21:08:07 zaphod NetworkManager[32732]: <info> Starting VPN service 'openvpn'...
Jul  5 21:08:07 zaphod NetworkManager[32732]: <info> VPN service 'openvpn' started (org.freedesktop.NetworkManager.openvpn), PID 1100
Jul  5 21:08:07 zaphod NetworkManager[32732]: <info> VPN service 'openvpn' appeared; activating connections
Jul  5 21:08:07 zaphod NetworkManager[32732]: <info> VPN plugin state changed: init (1)
Jul  5 21:08:07 zaphod NetworkManager[32732]: <info> VPN plugin state changed: starting (3)
Jul  5 21:08:07 zaphod NetworkManager[32732]: <info> VPN connection 'My VPN' (Connect) reply received.
Jul  5 21:08:07 zaphod nm-openvpn[1103]: OpenVPN 2.2.1 x86_64-linux-gnu [SSL] [LZO2] [EPOLL] [PKCS11] [eurephia] [MH] [PF_INET6] [IPv6 payload 20110424-2 (2.2RC2)] built on Mar 30 2012
Jul  5 21:08:07 zaphod nm-openvpn[1103]: WARNING: No server certificate verification method has been enabled.  See http://openvpn.net/howto.html#mitm for more info.
Jul  5 21:08:07 zaphod nm-openvpn[1103]: NOTE: the current --script-security setting may allow this configuration to call user-defined scripts
Jul  5 21:08:07 zaphod nm-openvpn[1103]: LZO compression initialized
Jul  5 21:08:08 zaphod nm-openvpn[1103]: Attempting to establish TCP connection with [AF_INET]xx.xx.xx.xx:443 [nonblock]
Jul  5 21:08:09 zaphod nm-openvpn[1103]: TCP connection established with [AF_INET]xx.xx.xx.xx:443
Jul  5 21:08:09 zaphod nm-openvpn[1103]: TCPv4_CLIENT link local: [undef]
Jul  5 21:08:09 zaphod nm-openvpn[1103]: TCPv4_CLIENT link remote: [AF_INET]xx.xx.xx.xx:443
Jul  5 21:08:47 zaphod NetworkManager[32732]: <warn> VPN connection 'My VPN' (IP Config Get) timeout exceeded.
Jul  5 21:08:47 zaphod nm-openvpn[1103]: SIGTERM[hard,] received, process exiting
Jul  5 21:08:47 zaphod NetworkManager[32732]: <info> Policy set 'Wired connection 2' (eth1) as default for IPv4 routing and DNS.
Jul  5 21:08:52 zaphod NetworkManager[32732]: <info> VPN service 'openvpn' disappeared
```Now, when it was trying to connect I ran the following command with the following result:
```
~$ ps -ef| grep openvpn
root       963 32732  0 20:58 ?        00:00:00 /usr/lib/NetworkManager/nm-openvpn-service
root       966   963  0 20:58 ?        00:00:00 /usr/sbin/openvpn --remote my.vpn.server --comp-lzo --nobind --dev tun --proto tcp-client --port 443 --cipher AES-256-CBC --auth-nocache --syslog nm-openvpn --script-security 2 --up /usr/lib/NetworkManager/nm-openvpn-service-openvpn-helper --up-restart --persist-key --persist-tun --management 127.0.0.1 1194 --management-query-passwords --route-noexec --ifconfig-noexec --client --ca /path/to/my/certs/ca_cert.pem --cert /path/to/my/certs/usercert.pem --key /path/to/my/certs/userkey.pem
```Now the strange thing is that when I take that exact openvpn command and run it manually (prefixed with 'sudo') it works every single time, however via Network Manager it always times out.

Any idea what is going on here?

---

### Post by cesera on 2012-07-18
bump

---

