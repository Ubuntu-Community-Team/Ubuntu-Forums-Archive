---
title: "Problem with VPN connection"
date: 2010-08-17
forum: Networking &amp; Wireless
---

### Post by ronni on 2010-08-17
Hi,

I have a problem getting my VPN to work.
In /var/log/syslog I get the following when trying to connect through network-manager.

----------
Aug 17 11:23:42 rofe-laptop NetworkManager: <info>  Starting VPN service 'org.freedesktop.NetworkManager.openvpn'...
Aug 17 11:23:42 rofe-laptop NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.openvpn' started (org.freedesktop.NetworkManager.openvpn), PID 3544
Aug 17 11:23:42 rofe-laptop NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.openvpn' just appeared, activating connections
Aug 17 11:23:42 rofe-laptop NetworkManager: <info>  VPN plugin state changed: 1
Aug 17 11:23:42 rofe-laptop NetworkManager: <info>  VPN plugin state changed: 3
Aug 17 11:23:42 rofe-laptop NetworkManager: <info>  VPN connection 'Hosting' (Connect) reply received.
Aug 17 11:23:42 rofe-laptop nm-openvpn[3549]: OpenVPN 2.1.0 x86_64-pc-linux-gnu [SSL] [LZO2] [EPOLL] [PKCS11] [MH] [PF_INET6] [eurephia] built on Jul 20 2010
Aug 17 11:23:42 rofe-laptop nm-openvpn[3549]: WARNING: No server certificate verification method has been enabled.  See [http://openvpn.net/howto.html#mitm](http://openvpn.net/howto.html#mitm) for more info.
Aug 17 11:23:42 rofe-laptop nm-openvpn[3549]: NOTE: the current --script-security setting may allow this configuration to call user-defined scripts
Aug 17 11:23:42 rofe-laptop nm-openvpn[3549]: WARNING: file '/home/rofe/easy-rsa/keys/ronni.key' is group or others accessible
Aug 17 11:23:42 rofe-laptop nm-openvpn[3549]: /usr/bin/openssl-vulnkey -q -b 2048 -m <modulus omitted>
Aug 17 11:23:42 rofe-laptop nm-openvpn[3549]: WARNING: file '/home/rofe/easy-rsa/keys/ta.key' is group or others accessible
Aug 17 11:23:42 rofe-laptop nm-openvpn[3549]: Control Channel Authentication: using '/home/rofe/easy-rsa/keys/ta.key' as a OpenVPN static key file
Aug 17 11:23:42 rofe-laptop nm-openvpn[3549]: LZO compression initialized
Aug 17 11:23:42 rofe-laptop nm-openvpn[3549]: UDPv4 link local: [undef]
Aug 17 11:23:42 rofe-laptop nm-openvpn[3549]: UDPv4 link remote: [AF_INET]xxx.xxx.xxx.xxx:1194
Aug 17 11:23:43 rofe-laptop nm-openvpn[3549]: [v111] Peer Connection Initiated with [AF_INET]xxx.xxx.xxx.xxx:1194
Aug 17 11:23:45 rofe-laptop connmand[1039]: tun0 {create} index 12 type 65534 <NONE>
Aug 17 11:23:45 rofe-laptop NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/tun0, iface: tun0)
Aug 17 11:23:45 rofe-laptop NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/tun0, iface: tun0): no ifupdown configuration found.
Aug 17 11:23:45 rofe-laptop kernel: [ 2208.838474] tun0: Disabled Privacy Extensions
Aug 17 11:23:45 rofe-laptop connmand[1039]: tun0 {update} flags 4240 <DOWN>
Aug 17 11:23:45 rofe-laptop connmand[1039]: tun0 {newlink} index 12 operstate 2 <DOWN>
Aug 17 11:23:45 rofe-laptop nm-openvpn[3549]: TUN/TAP device tun0 opened
Aug 17 11:23:45 rofe-laptop nm-openvpn[3549]: /sbin/ifconfig tun0 172.16.x.41 pointopoint 172.16.x.42 mtu 1500
Aug 17 11:23:45 rofe-laptop connmand[1039]: tun0 {add} address 172.16.x.41/32 label tun0
Aug 17 11:23:45 rofe-laptop connmand[1039]: tun0 {newlink} index 12 operstate 2 <DOWN>
Aug 17 11:23:45 rofe-laptop connmand[1039]: tun0 {update} flags 69841 <UP,RUNNING,LOWER_UP>
Aug 17 11:23:45 rofe-laptop connmand[1039]: tun0 {newlink} index 12 operstate 0 <UNKNOWN>
Aug 17 11:23:45 rofe-laptop connmand[1039]: tun0 {del} address 172.16.x.41/32 label tun0
Aug 17 11:23:45 rofe-laptop nm-openvpn[3549]: Linux ifconfig failed: external program exited with error status: 1
Aug 17 11:23:45 rofe-laptop nm-openvpn[3549]: Exiting
Aug 17 11:23:45 rofe-laptop NetworkManager:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/virtual/net/tun0, iface: tun0)
Aug 17 11:23:45 rofe-laptop connmand[1039]: tun0 {update} flags 4240 <DOWN>
Aug 17 11:23:45 rofe-laptop connmand[1039]: tun0 {newlink} index 12 operstate 2 <DOWN>
Aug 17 11:23:45 rofe-laptop connmand[1039]: tun0 {dellink} index 12 operstate 2 <DOWN>
Aug 17 11:23:45 rofe-laptop connmand[1039]: tun0 {remove} index 12
Aug 17 11:23:45 rofe-laptop NetworkManager: <info>  VPN plugin failed: 1
Aug 17 11:23:45 rofe-laptop NetworkManager: <info>  VPN plugin state changed: 6
Aug 17 11:23:45 rofe-laptop NetworkManager: <info>  VPN plugin state change reason: 0
Aug 17 11:23:45 rofe-laptop NetworkManager: <WARN>  connection_state_changed(): Could not process the request because no VPN connection was active.
Aug 17 11:23:45 rofe-laptop NetworkManager: <info>  Policy set 'Auto eth0' (eth0) as default for routing and DNS.
Aug 17 11:23:58 rofe-laptop NetworkManager: <debug> [1282037038.002401] ensure_killed(): waiting for vpn service pid 3544 to exit
Aug 17 11:23:58 rofe-laptop NetworkManager: <debug> [1282037038.002576] ensure_killed(): vpn service pid 3544 cleaned up
----------

Everything on the server looks fine, so I guess it's a local problem.

I've tried asking Google, and surfed the ubuntu forums, but cant find any answer.

---

### Post by ronni on 2010-08-23
Bump!

Anyone?

---

