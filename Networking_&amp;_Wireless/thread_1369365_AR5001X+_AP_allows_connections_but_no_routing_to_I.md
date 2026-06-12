---
title: "AR5001X+ AP allows connections but no routing to Internet"
date: 2009-12-31
forum: Networking &amp; Wireless
---

### Post by billechols on 2009-12-31
AP allows connections but does not allow traffic through to the other networks although it is pingable from all the other networks. Server is Ubuntu 9.10 server with DHCP and DNS.

Notes:

[LIST]
[*]ath5k and ath9k blacklisted in /etc/modprobe.d/blacklist.conf
[*]madwifi ath_pci is driver
[*]NetworkManager not installed
[*]kernel 2.6.32-020632-generic
[*]eth0 is public interface (PPPoE), eth1 is one network with MACs, Windows, and Ubuntu computers, ath1 is wireless for laptops running Windows and MacOS
[*]AP pings from 192.168.0.xxx, 192.168.1.xxx, and from public network address.
[*]laptops connect to AP but do not receive IP address from DHCP server; fixed addresses on 192.168.0.xxx or 192.168.1.xxx are not pingable from 192.168.0.xxx or public network address.
[*]bridging ath1 and eth1 was unsuccessful
[/LIST]
sudo lspci -nn | grep Atheros
03:00.0 Ethernet controller [0200]: Atheros Communications Inc. Atheros AR5001X+ Wireless Network Adapter [168c:0013] (rev 01)

ifconfig
ath1      Link encap:Ethernet  HWaddr 06:40:96:a8:f7:02
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::440:96ff:fea8:f702/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:212 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2297 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:28196 (28.1 KB)  TX bytes:459556 (459.5 KB)

eth0      Link encap:Ethernet  HWaddr 00:b0:d0:a1:1e:a4
          inet addr:65.5.215.108  Bcast:65.5.215.255  Mask:255.255.255.254
          inet6 addr: fe80::2b0:d0ff:fea1:1ea4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:395145 errors:0 dropped:0 overruns:0 frame:0
          TX packets:272033 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:524920326 (524.9 MB)  TX bytes:39902531 (39.9 MB)
          Interrupt:18 Base address:0xa800

eth1      Link encap:Ethernet  HWaddr 00:22:6b:be:20:66
          inet addr:192.168.0.13  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::222:6bff:febe:2066/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:260005 errors:0 dropped:0 overruns:0 frame:0
          TX packets:388432 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:32793215 (32.7 MB)  TX bytes:521537908 (521.5 MB)
          Interrupt:16 Base address:0xec00

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:324 errors:0 dropped:0 overruns:0 frame:0
          TX packets:324 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:33428 (33.4 KB)  TX bytes:33428 (33.4 KB)

ppp0      Link encap:Point-to-Point Protocol
          inet addr:65.5.215.108  P-t-P:70.159.198.9  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:394208 errors:0 dropped:0 overruns:0 frame:0
          TX packets:268735 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3
          RX bytes:516191127 (516.1 MB)  TX bytes:33443792 (33.4 MB)

wifi0     Link encap:UNSPEC  HWaddr 00-40-96-A8-F7-02-00-00-00-00-00-00-00-00-00-00
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1165 errors:0 dropped:0 overruns:0 frame:33
          TX packets:2845 errors:504 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:280
          RX bytes:67645 (67.6 KB)  TX bytes:594525 (594.5 KB)
          Interrupt:16

iwconfig ath1
ath1      IEEE 802.11g  ESSID:"LinuxWireless"  Nickname:""
          Mode:Master  Frequency:2.412 GHz  Access Point: 06:40:96:A8:F7:02
          Bit Rate=54 Mb/s   Tx-Power:20 dBm   Sensitivity=1/1
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=-96 dBm  Noise level=-96 dBm
          Rx invalid nwid:297  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

lsmod |grep ath
ath_rate_sample        11340  1
ath_pci               189890  0
wlan                  219759  6 wlan_wep,wlan_scan_ap,wlan_scan_sta,ath_rate_sample,ath_pci
ath_hal               357906  3 ath_rate_sample,ath_pci

lsmod | grep wlan
wlan_wep                5037  1
wlan_scan_ap            8038  1
wlan_scan_sta          11505  0
wlan                  219759  6 wlan_wep,wlan_scan_ap,wlan_scan_sta,ath_rate_sample,ath_pci

dmesg | grep wifi
[   13.096216] wifi0: Atheros AR5213A chip found (MAC 5.9, PHY 2112 4.3, Radio 3.6)
[   13.309538] ath_pci: wifi0: Atheros 5212: mem=0x48000000, irq=16
[ 1327.702072] wifi0: ath_fatal_tasklet: Hardware error; resetting.
[ 1328.725795] wifi0: ath_fatal_tasklet: Hardware error; resetting.
[ 1329.750163] wifi0: ath_fatal_tasklet: Hardware error; resetting.
[ 1330.671266] wifi0: ath_fatal_tasklet: Hardware error; resetting.
[ 1358.727516] wifi0: ath_fatal_tasklet: Hardware error; resetting.
[ 1359.751014] wifi0: ath_fatal_tasklet: Hardware error; resetting.
[ 1360.672513] wifi0: ath_fatal_tasklet: Hardware error; resetting.
[ 1361.696451] wifi0: ath_fatal_tasklet: Hardware error; resetting.
[ 1389.752375] wifi0: ath_fatal_tasklet: Hardware error; resetting.
[ 1390.673908] wifi0: ath_fatal_tasklet: Hardware error; resetting.
[ 1392.722711] wifi0: ath_fatal_tasklet: Hardware error; resetting.
[ 1420.678201] wifi0: ath_fatal_tasklet: Hardware error; resetting.
[ 1421.702055] wifi0: ath_fatal_tasklet: Hardware error; resetting.
[ 1422.726233] wifi0: ath_fatal_tasklet: Hardware error; resetting.
[ 1423.750617] wifi0: ath_fatal_tasklet: Hardware error; resetting.
[ 1451.709712] wifi0: ath_fatal_tasklet: Hardware error; resetting.
[ 1452.733834] wifi0: ath_fatal_tasklet: Hardware error; resetting.
[ 1453.757563] wifi0: ath_fatal_tasklet: Hardware error; resetting.
[ 1454.679312] wifi0: ath_fatal_tasklet: Hardware error; resetting.
[ 1544.698304] wifi0: ath_fatal_tasklet: Hardware error; resetting.
[ 1545.722393] wifi0: ath_fatal_tasklet: Hardware error; resetting.
[ 1546.746749] wifi0: ath_fatal_tasklet: Hardware error; resetting.
[ 1547.668217] wifi0: ath_fatal_tasklet: Hardware error; resetting.
[ 1577.673773] wifi0: ath_fatal_tasklet: Hardware error; resetting.
[ 1606.757715] wifi0: ath_fatal_tasklet: Hardware error; resetting.
[ 1607.679134] wifi0: ath_fatal_tasklet: Hardware error; resetting.
[ 1608.703246] wifi0: ath_fatal_tasklet: Hardware error; resetting.
[ 1609.727550] wifi0: ath_fatal_tasklet: Hardware error; resetting.

sudo lshw -C network
  *-network
       description: AR5001-0000-0000
       product: Wireless LAN Reference Card
       vendor: Atheros Communications, Inc.
       physical id: 0
       version: 00
       slot: Socket 0
       resources: irq:16
  *-network:0
       description: Ethernet interface
       product: NC100 Network Everywhere Fast Ethernet 10/100
       vendor: ADMtek
       physical id: b
       bus info: pci@0000:02:0b.0
       logical name: eth1
       version: 11
       serial: 00:22:6b:be:20:66
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list rom ethernet physical
       configuration: broadcast=yes driver=tulip driverversion=1.1.15 ip=192.168.0.13 latency=64 maxlatency=128 mingnt=64 multicast=yes
       resources: irq:16 ioport:ec00(size=256) memory:fafffc00-faffffff memory:44000000-4401ffff(prefetchable)
  *-network:1
       description: Ethernet interface
       product: 3c905C-TX/TX-M [Tornado]
       vendor: 3Com Corporation
       physical id: c
       bus info: pci@0000:02:0c.0
       logical name: eth0
       version: 78
       serial: 00:b0:d0:a1:1e:a4
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=3c59x duplex=full ip=65.5.215.108 latency=64 link=yes maxlatency=10 mingnt=10 multicast=yes port=MII speed=100MB/s
       resources: irq:18 ioport:e880(size=128) memory:fafff800-fafff87f memory:44020000-4403ffff(prefetchable)
  *-network
       description: Wireless interface
       product: Atheros AR5001X+ Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 1
       bus info: pci@0000:03:00.0
       logical name: wifi0
       version: 01
       serial: 00:40:96:a8:f7:02
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci ip=192.168.1.2 latency=96 maxlatency=28 mingnt=10 multicast=yes wireless=IEEE 802.11g
       resources: irq:16 memory:48000000-4800ffff

dhcp3-server dhcpd.conf
ddns-update-style none;

# option definitions common to all supported networks...
option domain-name "billechols.name";
option domain-name-servers 192.168.0.13;
option subnet-mask 255.255.255.0;
option ntp-servers 192.168.0.13;
include "/etc/dhcp3/rndc.key";
default-lease-time 86400;
max-lease-time 172800;

# If this DHCP server is the official DHCP server for the local
# network, the authoritative directive should be uncommented.
# authoritative;

# Use this to send dhcp log messages to a different log file (you also
# have to hack syslog.conf to complete the redirection).
log-facility local7;

# No service will be given on this subnet, but declaring it helps the
# DHCP server to understand the network topology.

#subnet 10.152.187.0 netmask 255.255.255.0 {
#}

# This is a very basic subnet declaration.


subnet 192.168.0.0 netmask 255.255.255.0 {
        range 192.168.0.50 192.168.0.100;
        range 192.168.0.150 192.168.0.200;
        option routers 192.168.0.13;
        option broadcast-address 192.168.0.255;

        host linuxserver {
                hardware ethernet 00:22:6b:be:20:66;
                fixed-address 192.168.0.13;
                }
}

subnet 192.168.1.0 netmask 255.255.255.0 {
        range 192.168.1.50 192.168.1.100;
        range 192.168.1.150 192.168.1.200;
        option routers 192.168.1.13;
        option broadcast-address 192.168.1.255;

        host ath1 {
                hardware ethernet 06:40:96:a8:f7:02;
                fixed-address 192.168.1.2;
                }
}

/etc/default/dhcp3-server
INTERFACES="eth1 ath1"

/etc/network/interfaces configuration:
auto lo
iface lo inet loopback

# The primary network interface motherboard NIC to Internet

auto eth0
iface eth0 inet static
        address 65.5.215.108
        netmask 255.255.255.254
        network 65.5.215.0
        broadcast 65.5.215.255
        gateway 70.159.198.9
#       post-up iptables-restore < /etc/iptables.up.rules

# The secondary network interface Linksys to internal network
auto eth1
iface eth1 inet static
        address 192.168.0.13
        netmask 255.255.255.0
        network 192.168.0.0
        broadcast 192.168.0.255
        gateway 65.5.215.108

#auto br0
#iface br0 inet static
#       address 192.168.0.13
#       network 192.168.0.0
#       netmask 255.255.255.0
#       broadcast 192.168.0.255
#       gateway 65.5.215.108
#       bridge_ports eth1 ath1

# added later
up route add default gw 65.5.215.108

auto dsl-provider
iface dsl-provider inet ppp
pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf
provider dsl-provider

lsb_release -d
Description:    Ubuntu 9.10

uname -mr
2.6.32-020632-generic i686

cat /etc/resolv.conf
nameserver 192.168.0.13
nameserver 205.152.132.23
nameserver 205.152.150.23
search billechols.name


What further information can I supply to solve this problem?

---

