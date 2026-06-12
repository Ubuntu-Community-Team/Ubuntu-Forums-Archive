---
title: "OpenVpn Problems"
date: 2012-08-12
forum: Networking &amp; Wireless
---

### Post by mintIng on 2012-08-12
Hello Ubuntu Community,

I can not extablish the internet connection after activating the vpn-connection to the server of my university. The vpn client can establish connection to the vpn server.
I have already spent a lot of time trying to solve this problem. Without success. Can anybody help me?
I'm using Ubuntu 12.04.
Here is my log output:
Aug 12 14:13:08 USER NetworkManager[740]: <info> Starting VPN service 'openvpn'...
Aug 12 14:13:08 USER NetworkManager[740]: <info> VPN service 'openvpn' started (org.freedesktop.NetworkManager.openvpn), PID 2357
Aug 12 14:13:08 USER NetworkManager[740]: <info> VPN service 'openvpn' appeared; activating connections
Aug 12 14:13:08 USER NetworkManager[740]: <info> VPN plugin state changed: starting (3)
Aug 12 14:13:08 USER NetworkManager[740]: <info> VPN connection 'dhbw-client2' (Connect) reply received.
Aug 12 14:13:08 USER nm-openvpn[2361]: OpenVPN 2.2.1 x86_64-linux-gnu [SSL] [LZO2] [EPOLL] [PKCS11] [eurephia] [MH] [PF_INET6] [IPv6 payload 20110424-2 (2.2RC2)] built on Mar 30 2012
Aug 12 14:13:09 USER nm-openvpn[2361]: WARNING: No server certificate verification method has been enabled.  See [http://openvpn.net/howto.html#mitm](http://openvpn.net/howto.html#mitm) for more info.
Aug 12 14:13:09 USER nm-openvpn[2361]: NOTE: the current --script-security setting may allow this configuration to call user-defined scripts
Aug 12 14:13:09 USER nm-openvpn[2361]: LZO compression initialized
Aug 12 14:13:09 USER nm-openvpn[2361]: UDPv4 link local: [undef]
Aug 12 14:13:09 USER nm-openvpn[2361]: UDPv4 link remote: [AF_INET]193.197.62.35:1198
Aug 12 14:13:10 USER nm-openvpn[2361]: [nacs.ba-stuttgart.de] Peer Connection Initiated with [AF_INET]193.197.62.35:1198
Aug 12 14:13:12 USER nm-openvpn[2361]: TUN/TAP device tun0 opened
Aug 12 14:13:12 USER nm-openvpn[2361]: /usr/lib/NetworkManager/nm-openvpn-service-openvpn-helper tun0 1500 1542 10.14.40.226 10.14.40.225 init
Aug 12 14:13:12 USER NetworkManager[740]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/tun0, iface: tun0)
Aug 12 14:13:12 USER NetworkManager[740]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/tun0, iface: tun0): no ifupdown configuration found.
Aug 12 14:13:12 USER NetworkManager[740]: <info> VPN connection 'dhbw-client2' (IP Config Get) reply received.
Aug 12 14:13:12 USER NetworkManager[740]: <info> VPN Gateway: 193.197.62.35
Aug 12 14:13:12 USER NetworkManager[740]: <info> Internal Gateway: 10.14.40.225
Aug 12 14:13:12 USER NetworkManager[740]: <info> Tunnel Device: tun0
Aug 12 14:13:12 USER NetworkManager[740]: <info> Internal IP4 Address: 10.14.40.226
Aug 12 14:13:12 USER NetworkManager[740]: <info> Internal IP4 Prefix: 32
Aug 12 14:13:12 USER NetworkManager[740]: <info> Internal IP4 Point-to-Point Address: 10.14.40.225
Aug 12 14:13:12 USER NetworkManager[740]: <info> Maximum Segment Size (MSS): 0
Aug 12 14:13:12 USER nm-openvpn[2361]: Initialization Sequence Completed
Aug 12 14:13:12 USER NetworkManager[740]: <info> Static Route: 10.200.0.0/16   Next Hop: 10.200.0.0
Aug 12 14:13:12 USER NetworkManager[740]: <info> Static Route: 10.14.0.1/32   Next Hop: 10.14.0.1
Aug 12 14:13:12 USER NetworkManager[740]: <info> Forbid Default Route: no
Aug 12 14:13:12 USER NetworkManager[740]: <info> DNS Domain: '(none)'
Aug 12 14:13:13 USER dnsmasq[2339]: exiting on receipt of SIGTERM
Aug 12 14:13:13 USER NetworkManager[740]: <info> DNS: starting dnsmasq...
Aug 12 14:13:13 USER NetworkManager[740]: <info> (tun0): writing resolv.conf to /sbin/resolvconf
Aug 12 14:13:13 USER dnsmasq[2367]: started, version 2.59 cache disabled
Aug 12 14:13:13 USER dnsmasq[2367]: compile time options: IPv6 GNU-getopt DBus i18n DHCP TFTP conntrack IDN
Aug 12 14:13:13 USER dnsmasq[2367]: warning: no upstream servers configured
Aug 12 14:13:13 USER NetworkManager[740]: <info> VPN connection 'dhbw-client2' (IP Config Get) complete.
Aug 12 14:13:13 USER NetworkManager[740]: <info> Policy set 'dhbw-client2' (tun0) as default for IPv4 routing and DNS.
Aug 12 14:13:13 USER dbus[553]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
Aug 12 14:13:13 USER NetworkManager[740]: <info> VPN plugin state changed: started (4)
Aug 12 14:13:13 USER dbus[553]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Aug 12 14:13:13 USER ntpdate[2389]: Can't find host ntp.ubuntu.com: Name or service not known (-2)
Aug 12 14:13:13 USER ntpdate[2389]: no servers can be used, exiting

---

### Post by SeijiSensei on 2012-08-12
After the connection appears up, see if you can ping the other end of the tunnel from the Terminal using "ping 10.14.0.1" which the log lists as the "next-hop" router upstream.  If you get replies from the router, you're having a problem with name resolution.

DNS resolution has been [changed considerably in 12.04]("http://www.stgraber.org/2012/02/24/dns-in-ubuntu-12-04/"), and not necessarily for the better in my mind. Try starting up the tunnel in Windows and then writing down the IP addresses of the DNS servers you have.  (You can look at the connection's "status" in Win7.  Otherwise you can open a command shell by entering "cmd" into the box in the Start menu and hitting return.  Then run the command "ipconfig /all" to see what addresses you have.)  Then on the Ubuntu side, try adding the servers manually to /etc/resolvconf/resolv.conf.d/head as Graber describes in that link.

---

### Post by bootedguy on 2012-08-12
You university IT department should have specific instructions on how to do this. VPN server implementations tend to be very site specific.

---

### Post by mintIng on 2012-08-13
@[SeijiSensei]("http://ubuntuforums.org/member.php?u=698195")
Thanks a lot for your answer. Yes, I can ping the address 10.14.0.1. I tried to add some domain name servers, but it does not help. I have used the command /etc/init.d/networking restart. After that my computer also does not recognize my umts-stick.
I need help again :(

---

### Post by steviematt on 2012-08-14
Does anyone else have advice? 

I'm having the same problem and have exactly the same log output as mintling... I'm connecting to the openvpn server without a problem but can't get a connection.

I have PPTP setup no problem with the same provider but i want a more secure connection with openvpn but ubuntu is having none of it.

---

