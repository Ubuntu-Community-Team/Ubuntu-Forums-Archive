---
title: "Ubuntu OpenVPN - networking issue."
date: 2013-06-16
forum: Networking &amp; Wireless
---

### Post by Connection on 2013-06-16
OpenVPN (Server): **Ubuntu 11** (served via: Openvz VPS hosting)

OpenVPN (Client): **Windows 7** (2.3.2-I001-i686)

**Issue:**

clients connect successfully to VPN, but dead internet access once inside the VPN.

**Facts:**

    -Everything is in mostly defaults
    -Server packages installed clean via apt-get (Successful without errors)
    -iptables is virgin. (100%)
    -No other active daemons/services (only VPN port listening)
    -No verbose errors in several MB of logs read; just dead internet symptom.
    -Remote administration via SSH and root privileges.
    -Windows 7 fresh installation, drivers updated, no firewall, and no wireless involved.
    -I've googled in search of answers for hours, 12 result pages deep to no avail.


***Notes:***

**netstat -rn**
```

Gateway         Genmask         Flags   MSS Window        irtt          Iface
10.8.0.2        0.0.0.0         255.255.255.255 UH        0 0          0 tun0
10.8.0.0        10.8.0.2        255.255.255.0   UG        0 0          0 tun0
0.0.0.0         0.0.0.0         0.0.0.0         U         0 0          0 venet0
```


**/etc/network/interfaces**

```
auto lo
iface lo inet loopback

auto venet0
iface venet0 inet manual
    up ifconfig venet0 up
    up ifconfig venet0 127.0.0.2
    up route add default dev venet0
    down route del default dev venet0
    down ifconfig venet0 down

iface venet0 inet6 manual
    up route -A inet6 add default dev venet0
    down route -A inet6 del default dev venet0

auto venet0:0
iface venet0:0 inet static
    address xxx.xxx.xxx.xxx
    netmask 255.255.255.255

auto venet0:1
iface venet0:1 inet static
    address xxx.xxx.xxx.xxx
    netmask 255.255.255.255

```
**netstat -a**
```

gre0      Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00
      NOARP  MTU:1476  Metric:1
      RX packets:0 errors:0 dropped:0 overruns:0 frame:0
      TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
      collisions:0 txqueuelen:0
      RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback
      inet addr:127.0.0.1  Mask:255.0.0.0
      inet6 addr: :: Scope:Host
      UP LOOPBACK RUNNING  MTU:16436  Metric:1
      RX packets:0 errors:0 dropped:0 overruns:0 frame:0
      TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
      collisions:0 txqueuelen:0
      RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

venet0    Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00
      inet addr:127.0.0.2  P-t-P:127.0.0.2  Bcast:0.0.0.0  Mask:255.255.255.255
      UP BROADCAST POINTOPOINT RUNNING NOARP  MTU:1500  Metric:1
      RX packets:217 errors:0 dropped:0 overruns:0 frame:0
      TX packets:175 errors:0 dropped:0 overruns:0 carrier:0
      collisions:0 txqueuelen:0
      RX bytes:23259 (23.2 KB)  TX bytes:29368 (29.3 KB)

venet0:0  Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00
      inet addr:xxx.xxx.xxx.xxx  P-t-P:xxx.xxx.xxx.xxx  Bcast:0.0.0.0   Mask:255.255.255.255
      UP BROADCAST POINTOPOINT RUNNING NOARP  MTU:1500  Metric:1

venet0:1  Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00
      inet addr:xxx.xxx.xxx.xxxs  P-t-P:xxx.xxx.xxx.xxx  Bcast:0.0.0.0  Mask:255.255.255.255
      UP BROADCAST POINTOPOINT RUNNING NOARP  MTU:1500  Metric:1
```

[B]
client.ovpn[/B] (OpenVPN - Windows)

```
client
dev tun
proto udp
remote xxx.xxx.xxx.xxx yyyy
resolv-retry infinite
nobind
persist-key
persist-tun
ca MyCa.crt
cert Server.crt
key Server.key
ns-cert-type server
tls-auth ta.key 1
cipher AES-128-CBC
verb 9
```


**/etc/openvpn/server.conf** (OpenVPN - Ubuntu)

```
port xxxx
proto udp
dev tun
ca MyCa.crt
cert Server.crt
key Server.key
dh dh1024.pem
server 10.8.0.0 255.255.255.0
push "redirect-gateway def1 bypass-dhcp"
keepalive 10 120
cipher AES-128-CBC
max-clients 8
log-append  openvpn.log
persist-key
persist-tun
verb 9

```



**/etc/sysctl.conf**
```

net.ipv4.ip_forward=1
```



Ideas?

---

