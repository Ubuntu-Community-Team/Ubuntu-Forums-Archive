---
title: "Installed Xen and now I can't seem to get my OpenVPN to connect(routing problem?)"
date: 2012-03-23
forum: Networking &amp; Wireless
---

### Post by RyanRahl on 2012-03-23
I just bought myself a shiny new laptop so I could teach myself to use Xen and I installed the hypervisor and all the tools, but the book I wanted to use is stored on my VPN. When I connect to my VPN (OpenVPN) everything authenticates just fine, however, I don't get an IP address and I can not communicate with any of the hosts on the VPN. I assigned an IP manually but it didn't help, I'm sure I am missing something obvious, does anyone know what I should do here.

my ifconfig looks like this:
```
ryan@the-ship:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:90:f5:c8:f6:92  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:78 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:351 (351.0 B)  TX bytes:351 (351.0 B)

tap0      Link encap:Ethernet  HWaddr fe:ff:ff:ff:ff:ff  
          inet6 addr: fe80::fcff:ffff:feff:ffff/64 Scope:Link
          UP BROADCAST RUNNING PROMISC MULTICAST  MTU:1500  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:29 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:92 (92.0 B)  TX bytes:5196 (5.1 KB)

virbr0    Link encap:Ethernet  HWaddr fe:ff:ff:ff:ff:ff  
          inet addr:192.168.122.1  Bcast:192.168.122.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr d4:9a:20:5a:db:0c  
          inet addr:192.168.200.130  Bcast:192.168.200.255  Mask:255.255.255.0
          inet6 addr: fe80::d69a:20ff:fe5a:db0c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7081 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4125 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:8046443 (8.0 MB)  TX bytes:563548 (563.5 KB)
```

my route -n looks like this
```
ryan@the-ship:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.200.1   0.0.0.0         UG    0      0        0 wlan0
74.94.76.141    192.168.200.1   255.255.255.255 UGH   0      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
192.168.122.0   0.0.0.0         255.255.255.0   U     0      0        0 virbr0
192.168.200.0   0.0.0.0         255.255.255.0   U     2      0        0 wlan0

```

the syslog says the following with
cat /var/log/syslog | grep vpn
```
Mar 22 14:17:05 the-ship NetworkManager[886]: <info> Starting VPN service 'openvpn'...
Mar 22 14:17:05 the-ship NetworkManager[886]: <info> VPN service 'openvpn' started (org.freedesktop.NetworkManager.openvpn), PID 2667
Mar 22 14:17:05 the-ship NetworkManager[886]: <info> VPN service 'openvpn' appeared; activating connections
Mar 22 14:17:05 the-ship nm-openvpn[2670]: OpenVPN 2.2.0 x86_64-linux-gnu [SSL] [LZO2] [EPOLL] [PKCS11] [eurephia] [MH] [PF_INET6] [IPv6 payload 20110424-2 (2.2RC2)] built on Jul  4 2011
Mar 22 14:17:05 the-ship nm-openvpn[2670]: WARNING: No server certificate verification method has been enabled.  See http://openvpn.net/howto.html#mitm for more info.
Mar 22 14:17:05 the-ship nm-openvpn[2670]: NOTE: the current --script-security setting may allow this configuration to call user-defined scripts
Mar 22 14:17:05 the-ship nm-openvpn[2670]: LZO compression initialized
Mar 22 14:17:05 the-ship nm-openvpn[2670]: UDPv4 link local: [undef]
Mar 22 14:17:05 the-ship nm-openvpn[2670]: UDPv4 link remote: [AF_INET]/*IP ommited for privacy*/:1194
Mar 22 14:17:08 the-ship nm-openvpn[2670]: TUN/TAP device tap0 opened
Mar 22 14:17:08 the-ship nm-openvpn[2670]: /usr/lib/NetworkManager/nm-openvpn-service-openvpn-helper tap0 1500 1574 192.168.27.159 255.255.255.0 init
Mar 22 14:17:08 the-ship nm-openvpn[2670]: Initialization Sequence Completed

```

My laptop is running Ubuntu 11.10 and the server is running 11.04

The VPN network is 192.168.27.0/24
and when I ping it looks like:
```
ryan@the-ship:~$ ping 192.168.27.1
PING 192.168.27.1 (192.168.27.1) 56(84) bytes of data.

^C
--- 192.168.27.1 ping statistics ---
25 packets transmitted, 0 received, 100% packet loss, time 24192ms
```

What should I do?

---

### Post by bprozeniuk on 2012-05-12
Libvirt creates a virtual bridge interface, which will automatically add any interface that is created. This seems to cause an issue with OpenVPN, and I don't know why.

My work around was to disable NAT on the default virbr0 interface. This is done in file at:
/var/lib/libvirt/network/default.xml

change forward mode='nat' to forward mode='route'

Forgot I did this too: 
Even in route mode, it was still adding the TAP interface to the bridge, i added a line to the script at /etc/xen/scripts/vif-bridge script

at line 90 it says: add_to_bridge "$bridge" "$dev"

I added a check to see if $dev is not tap0:


  if [ "$dev" -ne "tap0" ]
                add_to_bridge "$bridge" "$dev"
  fi

At this point, if you still want to run NAT, simply do it your self with iptables. I know I already was for my OpenVPN connections.

---

### Post by RyanRahl on 2012-05-16
Awesome, that worked perfectly. After reading the script I have a much better understanding of what is going on as well. Thank you, this information is invaluable to me.:guitar:

---

