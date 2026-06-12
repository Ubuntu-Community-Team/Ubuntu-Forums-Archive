---
title: "OpenVPN - Cannot configure Static Ip for tun0"
date: 2011-01-21
forum: Networking &amp; Wireless
---

### Post by DoneRightI.T. on 2011-01-21
Running 64 Bit 10.10 with 
openvpn 2.1.0-ubuntu1
gadmin-openvpn-client 0.1.1-1
network-manager-openvpn-gnome 0.8.1+git.20100810t173015.1711d04-0ubuntu1

the problem I am having is the openvpn configuration I have been provided, has a static ip address, the open vpn client configuration through network manager util does not have the ability to configure "static" addresses... ie. the option does not exist and thus the "add" is greyed out.

I have successfully configured and connected from the cli utilizing a .conf file located within /etc/openvpn

I have as well found the configuration file for the nm-applet openvpn, and attempted to configure this manually, however I can find no documentation nor am I able to guess the values to be set within this file. /etc/NetworkManager/system-connections/openvpnconnection

Any insight would be greatly appreciated in order to get this up and running.

---

### Post by gordintoronto on 2011-01-21
Static or dynamic is determined when you connect to the network, it's not configured in VPN. If you right-click on the network manager icon and select "edit connections" you can get to the place where you select a static IP, as opposed to DHCP. With a static IP, you must specify the other characteristics of the connection, such as the DNS server to use.

---

### Post by DoneRightI.T. on 2011-01-22
> **gordintoronto said:**
> Static or dynamic is determined when you connect to the network, it's not configured in VPN. If you right-click on the network manager icon and select "edit connections" you can get to the place where you select a static IP, as opposed to DHCP. With a static IP, you must specify the other characteristics of the connection, such as the DNS server to use.

within a default openvpn setup you have the ability to determine if the tap device is static or dhcp. I have this working from the cli and installed as a service using a "static device" ie. ifconfig 192.168.2.2 255.255.0.0
obviously the above ip's are an example.... point being it works and assigns the address to the tap device.
I have found the config file where this "should" be possible. however cannot figure the params to make this happen... the specific error I have encountered from teh logs are below. and based on google I have attempted a direct connect(even though the cli connection works)... Just to be safe.



```

Jan 22 16:23:43 c nm-openvpn[3933]: OpenVPN 2.1.0 x86_64-pc-linux-gnu [SSL] [LZO2] [EPOLL] [PKCS11] [MH] [PF_INET6] [eurephia] built on Jul 12 2010
Jan 22 16:23:43 c nm-openvpn[3933]: WARNING: No server certificate verification method has been enabled.  See http://openvpn.net/howto.html#mitm for more info.
Jan 22 16:23:43 c nm-openvpn[3933]: NOTE: the current --script-security setting may allow this configuration to call user-defined scripts
Jan 22 16:23:43 c nm-openvpn[3933]: /usr/bin/openssl-vulnkey -q -b 1024 -m <modulus omitted>
Jan 22 16:23:44 c nm-openvpn[3933]: LZO compression initialized
Jan 22 16:23:44 c nm-openvpn[3933]: UDPv4 link local: [undef]
Jan 22 16:23:44 c nm-openvpn[3933]: UDPv4 link remote: [AF_INET]207.231.224.16:1222
Jan 22 16:23:44 c nm-openvpn[3933]: WARNING: 'cipher' is used inconsistently, local='cipher DES-CBC', remote='cipher BF-CBC'
Jan 22 16:23:44 c nm-openvpn[3933]: WARNING: 'keysize' is used inconsistently, local='keysize 64', remote='keysize 128'
Jan 22 16:23:44 c nm-openvpn[3933]: [*********] Peer Connection Initiated with [AF_INET]***.***.**.**:1222
Jan 22 16:23:47 c nm-openvpn[3933]: TUN/TAP device tap0 opened
Jan 22 16:23:47 c nm-openvpn[3933]: /usr/lib/network-manager-openvpn/nm-openvpn-service-openvpn-helper tap0 1500 1574   init
Jan 22 16:23:47 c modem-manager: (net/tap0): could not get port's parent device
Jan 22 16:23:47 c NetworkManager[1010]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/tap0, iface: tap0)
Jan 22 16:23:47 c NetworkManager[1010]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/tap0, iface: tap0): no ifupdown configuration found.
Jan 22 16:23:47 c NetworkManager[1010]: <warn> /sys/devices/virtual/net/tap0: couldn't determine device driver; ignoring...
Jan 22 16:23:47 c NetworkManager[1010]: <warn> VPN plugin failed: 2
Jan 22 16:23:47 c nm-openvpn[3933]: script failed: external program exited with error status: 1
Jan 22 16:23:47 c nm-openvpn[3933]: Exiting
Jan 22 16:23:47 c avahi-daemon[1016]: Withdrawing workstation service for tap0.
Jan 22 16:23:47 c NetworkManager[1010]:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/virtual/net/tap0, iface: tap0)
Jan 22 16:23:47 c NetworkManager[1010]: <warn> VPN plugin failed: 1
Jan 22 16:23:47 c NetworkManager[1010]: <info> VPN plugin state changed: 6
Jan 22 16:23:47 c NetworkManager[1010]: <info> VPN plugin state change reason: 0
Jan 22 16:23:47 c NetworkManager[1010]: <warn> error disconnecting VPN: Could not process the request because no VPN connection was active.
Jan 22 16:23:47 c NetworkManager[1010]: <info> Policy set 'Auto DRI' (wlan0) as default for IPv4 routing and DNS.

```

---

