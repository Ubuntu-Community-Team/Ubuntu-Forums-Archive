---
title: "Wifi fails to reconnect"
date: 2019-09-01
forum: MINT
---

### Post by rogegor on 2019-09-01
I use Mint 19.1 (Ubuntu 18).
For months, sometime after Wifi disconnect it can't reconnect. 
I try some ```
sudo service network-manager restart
``` but without any effect.

Some extract of syslog
```

Jun 13 00:09:01 hal anacron[32181]: Normal exit (1 job run)
Jun 13 00:11:08 hal wpa_supplicant[1028]: wlp6s0: CTRL-EVENT-DISCONNECTED bssid=14:0c:76:7f:0a:00 reason=4 locally_generated=1
Jun 13 00:11:08 hal NetworkManager[1016]: <warn>  [1560377468.1380] sup-iface[0x55de493c3240,wlp6s0]: connection disconnected (reason -4)
Jun 13 00:11:08 hal wpa_supplicant[1028]: wlp6s0: CTRL-EVENT-REGDOM-CHANGE init=CORE type=WORLD
Jun 13 00:11:08 hal wpa_supplicant[1028]: wlp6s0: CTRL-EVENT-REGDOM-CHANGE init=USER type=COUNTRY alpha2=FR
Jun 13 00:11:08 hal NetworkManager[1016]: <info>  [1560377468.1902] device (wlp6s0): supplicant interface state: completed -> disconnected
Jun 13 00:11:08 hal NetworkManager[1016]: <info>  [1560377468.2432] device (wlp6s0): supplicant interface state: disconnected -> scanning
Jun 13 00:11:23 hal NetworkManager[1016]: <warn>  [1560377483.7495] device (wlp6s0): link timed out.
Jun 13 00:11:23 hal NetworkManager[1016]: <info>  [1560377483.7500] device (wlp6s0): state change: activated -> failed (reason 'ssid-not-found', sys-iface-state: 'managed')
Jun 13 00:11:23 hal NetworkManager[1016]: <info>  [1560377483.7503] **manager: NetworkManager state is now DISCONNECTED**
Jun 13 00:11:23 hal NetworkManager[1016]: <warn>  [1560377483.7545] device (wlp6s0): Activation: failed for connection 'zzzzznet'
Jun 13 00:11:23 hal dbus-daemon[1012]: [system] Activating via systemd: service name='org.freedesktop.nm_dispatcher' unit='dbus-org.freedesktop.nm-dispatcher.service' requested by ':1.14' (uid=0 pid=1016 comm="/usr/sbin/NetworkManager --no-daemon " label="unconfined")
Jun 13 00:11:23 hal **NetworkManager[1016]: <info>  [1560377483.7556] device (wlp6s0): state change: failed -> disconnected**(reason 'none', sys-iface-state: 'managed')
Jun 13 00:11:23 hal kernel: [ 3834.138028] IPv6: ADDRCONF(NETDEV_UP): wlp6s0: link is not ready
Jun 13 00:11:23 hal avahi-daemon[1010]: Withdrawing address record for 2a01:e35:2ea3:a200:f5c2:b07f:219e:a6a9 on wlp6s0.
Jun 13 00:11:23 hal avahi-daemon[1010]: Withdrawing address record for 2a01:e35:2ea3:a200:eade:27ff:fe0b:9342 on wlp6s0.
Jun 13 00:11:23 hal avahi-daemon[1010]: Leaving mDNS multicast group on interface wlp6s0.IPv6 with address 2a01:e35:2ea3:a200:eade:27ff:fe0b:9342.
Jun 13 00:11:23 hal avahi-daemon[1010]: Joining mDNS multicast group on interface wlp6s0.IPv6 with address fe80::eade:27ff:fe0b:9342.
Jun 13 00:11:23 hal avahi-daemon[1010]: Registering new address record for fe80::eade:27ff:fe0b:9342 on wlp6s0.*.
Jun 13 00:11:23 hal avahi-daemon[1010]: Withdrawing address record for fe80::eade:27ff:fe0b:9342 on wlp6s0.
Jun 13 00:11:23 hal avahi-daemon[1010]: Leaving mDNS multicast group on interface wlp6s0.IPv6 with address fe80::eade:27ff:fe0b:9342.
Jun 13 00:11:23 hal avahi-daemon[1010]: Interface wlp6s0.IPv6 no longer relevant for mDNS.
Jun 13 00:11:23 hal systemd[1]: Starting Network Manager Script Dispatcher Service...
Jun 13 00:11:23 hal dbus-daemon[1012]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Jun 13 00:11:23 hal systemd[1]: Started Network Manager Script Dispatcher Service.
Jun 13 00:11:23 hal nm-dispatcher: req:1 'down' [wlp6s0]: new request (1 scripts)
Jun 13 00:11:23 hal nm-dispatcher: req:1 'down' [wlp6s0]: start running ordered scripts...
Jun 13 00:11:23 hal nm-dispatcher: req:2 'connectivity-change': new request (1 scripts)
Jun 13 00:11:23 hal NetworkManager[1016]: <info>  [1560377483.7881] dhcp4 (wlp6s0): canceled DHCP transaction, DHCP client pid 1396
Jun 13 00:11:23 hal NetworkManager[1016]: <info>  [1560377483.7881] dhcp4 (wlp6s0): state changed bound -> done
Jun 13 00:11:23 hal avahi-daemon[1010]: Withdrawing address record for 192.168.0.171 on wlp6s0.
Jun 13 00:11:23 hal avahi-daemon[1010]: Leaving mDNS multicast group on interface wlp6s0.IPv4 with address 192.168.0.171.
Jun 13 00:11:23 hal avahi-daemon[1010]: Interface wlp6s0.IPv4 no longer relevant for mDNS.
Jun 13 00:11:23 hal wpa_supplicant[1028]: wlp6s0: Reject scan trigger since one is already pending
Jun 13 00:11:25 hal NetworkManager[1016]: <info>  [1560377485.6470] policy: auto-activating connection 'zzzzznet'
Jun 13 00:11:25 hal NetworkManager[1016]: <info>  [1560377485.6490] device (wlp6s0): Activation: starting connection 'zzzzznet' (32bd47c4-dab3-4532-a903-e107048868bd)
Jun 13 00:11:25 hal NetworkManager[1016]: <info>  [1560377485.6492] device (wlp6s0): state change: disconnected -> prepare (reason 'none', sys-iface-state: 'managed')
Jun 13 00:11:25 hal NetworkManager[1016]: <info>  [1560377485.6494] manager: NetworkManager state is now CONNECTING
Jun 13 00:11:25 hal NetworkManager[1016]: <info>  [1560377485.6501] device (wlp6s0): state change: prepare -> config (reason 'none', sys-iface-state: 'managed')
Jun 13 00:11:25 hal NetworkManager[1016]: <info>  [1560377485.6506] device (wlp6s0): Activation: (wifi) access point 'zzzzznet' has security, but secrets are required.
Jun 13 00:11:25 hal NetworkManager[1016]: <info>  [1560377485.6508] device (wlp6s0): state change: config -> need-auth (reason 'none', sys-iface-state: 'managed')
Jun 13 00:11:25 hal NetworkManager[1016]: <info>  [1560377485.6559] device (wlp6s0): state change: need-auth -> prepare (reason 'none', sys-iface-state: 'managed')
Jun 13 00:11:25 hal NetworkManager[1016]: <info>  [1560377485.6564] device (wlp6s0): state change: prepare -> config (reason 'none', sys-iface-state: 'managed')
Jun 13 00:11:25 hal NetworkManager[1016]: <info>  [1560377485.6566] device (wlp6s0): Activation: (wifi) connection 'zzzzznet' has security, and secrets exist.  No new secrets needed.
Jun 13 00:11:25 hal NetworkManager[1016]: <info>  [1560377485.6567] Config: added 'ssid' value 'zzzzznet'
Jun 13 00:11:25 hal NetworkManager[1016]: <info>  [1560377485.6567] Config: added 'scan_ssid' value '1'
Jun 13 00:11:25 hal NetworkManager[1016]: <info>  [1560377485.6567] Config: added 'bgscan' value 'simple:30:-80:86400'
Jun 13 00:11:25 hal NetworkManager[1016]: <info>  [1560377485.6567] Config: added 'key_mgmt' value 'WPA-PSK'
Jun 13 00:11:25 hal NetworkManager[1016]: <info>  [1560377485.6567] Config: added 'psk' value '<hidden>'
Jun 13 00:11:28 hal nm-dispatcher: req:2 'connectivity-change': start running ordered scripts...
Jun 13 00:11:50 hal NetworkManager[1016]: <warn>  [1560377510.7493] device (wlp6s0): Activation: (wifi) association took too long, failing activation
Jun 13 00:11:50 hal NetworkManager[1016]: <info>  [1560377510.7493] device (wlp6s0): state change: config -> failed (reason 'ssid-not-found', sys-iface-state: 'managed')
Jun 13 00:11:50 hal NetworkManager[1016]: <info>  [1560377510.7498] **manager: NetworkManager state is now DISCONNECTED**
Jun 13 00:11:50 hal NetworkManager[1016]: <warn>  [1560377510.7509] device (wlp6s0): Activation: failed for connection 'zzzzznet'
Jun 13 00:11:50 hal NetworkManager[1016]: <info>  [1560377510.7522] device (wlp6s0): state change: failed -> disconnected (reason 'none', sys-iface-state: 'managed')
Jun 13 00:11:50 hal NetworkManager[1016]: <info>  [1560377510.7544] device (wlp6s0): supplicant interface state: scanning -> disconnected
Jun 13 00:11:50 hal kernel: [ 3861.135175] IPv6: ADDRCONF(NETDEV_UP): wlp6s0: link is not ready
Jun 13 00:11:53 hal NetworkManager[1016]: <info>  [1560377513.2106] policy: auto-activating connection 'zzzzznet'
Jun 13 00:11:53 hal NetworkManager[1016]: <info>  [1560377513.2125] device (wlp6s0): Activation: starting connection 'zzzzznet' (32bd47c4-dab3-4532-a903-e107048868bd)
Jun 13 00:11:53 hal NetworkManager[1016]: <info>  [1560377513.2128] device (wlp6s0): state change: disconnected -> prepare (reason 'none', sys-iface-state: 'managed')
Jun 13 00:11:53 hal NetworkManager[1016]: <info>  [1560377513.2129] manager: NetworkManager state is now CONNECTING
Jun 13 00:11:53 hal NetworkManager[1016]: <info>  [1560377513.2133] device (wlp6s0): state change: prepare -> config (reason 'none', sys-iface-state: 'managed')
Jun 13 00:11:53 hal NetworkManager[1016]: <info>  [1560377513.2134] device (wlp6s0): Activation: (wifi) access point 'zzzzznet' has security, but secrets are required.
Jun 13 00:11:53 hal NetworkManager[1016]: <info>  [1560377513.2135] device (wlp6s0): state change: config -> need-auth (reason 'none', sys-iface-state: 'managed')
Jun 13 00:11:53 hal NetworkManager[1016]: <info>  [1560377513.2166] device (wlp6s0): state change: need-auth -> prepare (reason 'none', sys-iface-state: 'managed')
Jun 13 00:11:53 hal NetworkManager[1016]: <info>  [1560377513.2168] device (wlp6s0): state change: prepare -> config (reason 'none', sys-iface-state: 'managed')
Jun 13 00:11:53 hal NetworkManager[1016]: <info>  [1560377513.2170] device (wlp6s0): Activation: (wifi) connection 'zzzzznet' has security, and secrets exist.  No new secrets needed.
Jun 13 00:11:53 hal NetworkManager[1016]: <info>  [1560377513.2170] Config: added 'ssid' value 'zzzzznet'
Jun 13 00:11:53 hal NetworkManager[1016]: <info>  [1560377513.2170] Config: added 'scan_ssid' value '1'
Jun 13 00:11:53 hal NetworkManager[1016]: <info>  [1560377513.2170] Config: added 'bgscan' value 'simple:30:-80:86400'
Jun 13 00:11:53 hal NetworkManager[1016]: <info>  [1560377513.2170] Config: added 'key_mgmt' value 'WPA-PSK'
Jun 13 00:11:53 hal NetworkManager[1016]: <info>  [1560377513.2171] Config: added 'psk' value '<hidden>'
Jun 13 00:11:53 hal NetworkManager[1016]: <info>  [1560377513.2266] device (wlp6s0): supplicant interface state: disconnected -> scanning
Jun 13 00:12:18 hal NetworkManager[1016]: <warn>  [1560377538.7501] device (wlp6s0): Activation: (wifi) association took too long, failing activation
Jun 13 00:12:18 hal NetworkManager[1016]: <info>  [1560377538.7502] device (wlp6s0): state change: config -> failed (reason 'ssid-not-found', sys-iface-state: 'managed')
Jun 13 00:12:18 hal NetworkManager[1016]: <info>  [1560377538.7507] **manager: NetworkManager state is now DISCONNECTED**
Jun 13 00:12:18 hal NetworkManager[1016]: <warn>  [1560377538.7520] device (wlp6s0): Activation: failed for connection 'zzzzznet'
Jun 13 00:12:18 hal NetworkManager[1016]: <info>  [1560377538.7533] device (wlp6s0): supplicant interface state: scanning -> disconnected
Jun 13 00:12:18 hal NetworkManager[1016]: <info>  [1560377538.7544] device (wlp6s0): state change: failed -> disconnected (reason 'none', sys-iface-state: 'managed')
Jun 13 00:12:18 hal kernel: [ 3889.137771] IPv6: ADDRCONF(NETDEV_UP): wlp6s0: link is not ready
Jun 13 00:12:21 hal NetworkManager[1016]: <info>  [1560377541.2097] policy: auto-activating connection 'zzzzznet'
Jun 13 00:12:21 hal NetworkManager[1016]: <info>  [1560377541.2108] device (wlp6s0): Activation: starting connection 'zzzzznet' (32bd47c4-dab3-4532-a903-e107048868bd)
Jun 13 00:12:21 hal NetworkManager[1016]: <info>  [1560377541.2110] device (wlp6s0): state change: disconnected -> prepare (reason 'none', sys-iface-state: 'managed')
Jun 13 00:12:21 hal NetworkManager[1016]: <info>  [1560377541.2112] manager: NetworkManager state is now CONNECTING
Jun 13 00:12:21 hal NetworkManager[1016]: <info>  [1560377541.2117] device (wlp6s0): state change: prepare -> config (reason 'none', sys-iface-state: 'managed')
Jun 13 00:12:21 hal NetworkManager[1016]: <info>  [1560377541.2119] device (wlp6s0): Activation: (wifi) access point 'zzzzznet' has security, but secrets are required.
Jun 13 00:12:21 hal NetworkManager[1016]: <info>  [1560377541.2119] device (wlp6s0): state change: config -> need-auth (reason 'none', sys-iface-state: 'managed')
Jun 13 00:12:21 hal NetworkManager[1016]: <info>  [1560377541.2156] device (wlp6s0): state change: need-auth -> prepare (reason 'none', sys-iface-state: 'managed')
Jun 13 00:12:21 hal NetworkManager[1016]: <info>  [1560377541.2159] device (wlp6s0): state change: prepare -> config (reason 'none', sys-iface-state: 'managed')
Jun 13 00:12:21 hal NetworkManager[1016]: <info>  [1560377541.2161] device (wlp6s0): Activation: (wifi) connection 'zzzzznet' has security, and secrets exist.  No new secrets needed.
Jun 13 00:12:21 hal NetworkManager[1016]: <info>  [1560377541.2162] Config: added 'ssid' value 'zzzzznet'
Jun 13 00:12:21 hal NetworkManager[1016]: <info>  [1560377541.2162] Config: added 'scan_ssid' value '1'
Jun 13 00:12:21 hal NetworkManager[1016]: <info>  [1560377541.2162] Config: added 'bgscan' value 'simple:30:-80:86400'
Jun 13 00:12:21 hal NetworkManager[1016]: <info>  [1560377541.2162] Config: added 'key_mgmt' value 'WPA-PSK'
Jun 13 00:12:21 hal NetworkManager[1016]: <info>  [1560377541.2162] Config: added 'psk' value '<hidden>'
Jun 13 00:12:21 hal NetworkManager[1016]: <info>  [1560377541.2260] device (wlp6s0): supplicant interface state: disconnected -> scanning
Jun 13 00:12:46 hal NetworkManager[1016]: <warn>  [1560377566.7495] device (wlp6s0): Activation: (wifi) association took too long, failing activation
Jun 13 00:12:46 hal NetworkManager[1016]: <info>  [1560377566.7496] device (wlp6s0): state change: config -> failed (reason 'ssid-not-found', sys-iface-state: 'managed')
Jun 13 00:12:46 hal NetworkManager[1016]: <info>  [1560377566.7502] **manager: NetworkManager state is now DISCONNECTED**
Jun 13 00:12:46 hal NetworkManager[1016]: <warn>  [1560377566.7520] device (wlp6s0): Activation: failed for connection 'zzzzznet'
Jun 13 00:12:46 hal NetworkManager[1016]: <info>  [1560377566.7528] device (wlp6s0): supplicant interface state: scanning -> disconnected
Jun 13 00:12:46 hal NetworkManager[1016]: <info>  [1560377566.7542] device (wlp6s0): state change: failed -> disconnected (reason 'none', sys-iface-state: 'managed')
Jun 13 00:12:46 hal kernel: [ 3917.138088] IPv6: ADDRCONF(NETDEV_UP): wlp6s0: link is not ready

```

My hardware :
```
lshw -C networkWARNING: you should run this program as super-user.
  *-network                 
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: enp3s0
       version: 11
       serial: 40:16:7e:ad:77:93
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8168g-2_0.0.1 02/06/13 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:18 ioport:d000(size=256) memory:f7200000-f7200fff memory:f2100000-f2103fff
  *-network
       description: Wireless interface
       product: AR93xx Wireless Network Adapter
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: wlp6s0
       version: 01
       serial: e8:de:27:0b:93:42
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=4.15.0-58-generic firmware=N/A ip=192.168.0.171 latency=0 link=yes multicast=yes wireless=IEEE 802.11
       resources: irq:19 memory:f7100000-f711ffff memory:f7120000-f712ffff
  *-network
       description: Ethernet interface
       physical id: 1
       logical name: anbox0
       serial: ca:ab:ce:11:f4:b3
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A ip=192.168.250.1 link=yes multicast=yes



```
when I reboot then WiFi start again normally.
It's boring.

Thanks for helping.

---

### Post by coffeecat on 2019-09-01
*Thread moved to the **Mint** sub-forum.*

---

### Post by rogegor on 2019-09-06
Any help please?

---

