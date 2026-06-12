---
title: "eth0 DISABLED upon reboot - Lucid"
date: 2010-09-07
forum: Networking &amp; Wireless
---

### Post by jimjohnsean on 2010-09-07
Network card (82566DM-2 Gigabit Network Connection) is DISABLED upon reboot. Only way to bring it out of disabled mode is to rerun dhclient to obtain a DHCP lease. Upon reboot though, the NIC is back into disabled mode.

A workaround I have found is to uncomment the iface line in /etc/network/interfaces, but considering I have 14 identical PCs to this one, and only this one is currently giving me grief, I am trying to find the root cause

The machine successfully obtains an IP using the PXE boot option in the BIOS - so I can hopefully rule out hardware problems as a cause. Network cable has been replaced, as the location of the machine to a different switch port.

/etc/network/interfaces

```
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
#iface eth0 inet dhcp

```

$ lshw -C network

```
*-network DISABLED
       description: Ethernet interface
       product: 82566DM-2 Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 02
       serial: 00:1e:4f:4a:39:a4
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.0.2-k2 duplex=full firmware=1.1-1 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:27 memory:fe9e0000-fe9fffff memory:fe9db000-fe9dbfff ioport:ecc0(size=32)

```

/etc/NetworkManager/nm-system-settings.conf

```
[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=false
```

/var/log/syslog

```
Sep  7 17:21:40 p1-ast-13 NetworkManager: <info>  starting...
Sep  7 17:21:40 p1-ast-13 NetworkManager: <info>  Trying to start the modem-manager...
Sep  7 17:21:40 p1-ast-13 modem-manager: Loaded plugin Ericsson MBM
Sep  7 17:21:40 p1-ast-13 modem-manager: Loaded plugin Longcheer
Sep  7 17:21:40 p1-ast-13 modem-manager: Loaded plugin ZTE
Sep  7 17:21:40 p1-ast-13 NetworkManager:    SCPlugin-Ifupdown: init!
Sep  7 17:21:40 p1-ast-13 NetworkManager:    SCPlugin-Ifupdown: update_system_hostname
Sep  7 17:21:40 p1-ast-13 NetworkManager:    SCPluginIfupdown: management mode: unmanaged
Sep  7 17:21:40 p1-ast-13 NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:19.0/net/eth0, iface: eth0)
Sep  7 17:21:40 p1-ast-13 NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:19.0/net/eth0, iface: eth0): no ifupdown configuration found.
Sep  7 17:21:40 p1-ast-13 NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
Sep  7 17:21:40 p1-ast-13 NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
Sep  7 17:21:40 p1-ast-13 NetworkManager:    SCPlugin-Ifupdown: end _init.
Sep  7 17:21:40 p1-ast-13 NetworkManager: Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
Sep  7 17:21:40 p1-ast-13 NetworkManager: Loaded plugin keyfile: (c) 2007 - 2008 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Sep  7 17:21:40 p1-ast-13 NetworkManager: <info>  WiFi enabled by radio killswitch; enabled by state file
Sep  7 17:21:40 p1-ast-13 NetworkManager: <info>  WWAN enabled by radio killswitch; enabled by state file
Sep  7 17:21:40 p1-ast-13 NetworkManager:    SCPlugin-Ifupdown: (29828384) ... get_connections.
Sep  7 17:21:40 p1-ast-13 NetworkManager:    SCPlugin-Ifupdown: (29828384) ... get_connections (managed=false): return empty list.
Sep  7 17:21:40 p1-ast-13 modem-manager: Loaded plugin Sierra
Sep  7 17:21:40 p1-ast-13 modem-manager: Loaded plugin Option High-Speed
Sep  7 17:21:40 p1-ast-13 modem-manager: Loaded plugin MotoC
Sep  7 17:21:40 p1-ast-13 modem-manager: Loaded plugin Generic
Sep  7 17:21:41 p1-ast-13 modem-manager: Loaded plugin Gobi
Sep  7 17:21:41 p1-ast-13 NetworkManager:    Ifupdown: get unmanaged devices count: 0
Sep  7 17:21:41 p1-ast-13 NetworkManager: <info>  (eth0): carrier is OFF
Sep  7 17:21:41 p1-ast-13 NetworkManager: <info>  (eth0): new Ethernet device (driver: 'e1000e')
Sep  7 17:21:41 p1-ast-13 NetworkManager: <info>  (eth0): exported as /org/freedesktop/NetworkManager/Devices/0
Sep  7 17:21:41 p1-ast-13 NetworkManager: <info>  modem-manager is now available
Sep  7 17:21:41 p1-ast-13 NetworkManager: <WARN>  default_adapter_cb(): bluez error getting default adapter: The name org.bluez was not provided by any .service files
Sep  7 17:21:41 p1-ast-13 NetworkManager: <info>  Trying to start the supplicant...
```

Has anyone got an idea about what it could be?

Thanks

---

### Post by luceerose on 2010-09-07
As far as I know, the
iface eth0 inet dhcp
line SHOULD be uncommented.
My only other suggestion is, have you tried denoting static ip's to your computers ?
Like so;
```
auto lo
iface lo inet loopback
allow-hotplug eth0
iface eth0 inet static
	address 192.168.X.X
	netmask 255.255.X.X
	network 192.168.X.X
	broadcast 192.168.X.X
	gateway 192.168.X.X
	dns-nameservers 192.168.X.X
```
Or possibly try 'allow-hotplug' on eth0, rather than 'auto'

---

### Post by jimjohnsean on 2010-09-07
> **larsenguitars said:**
> As far as I know, the
iface eth0 inet dhcp
line SHOULD be uncommented.
My only other suggestion is, have you tried denoting static ip's to your computers ?
Like so;
```
auto lo
iface lo inet loopback
allow-hotplug eth0
iface eth0 inet static
	address 192.168.X.X
	netmask 255.255.X.X
	network 192.168.X.X
	broadcast 192.168.X.X
	gateway 192.168.X.X
	dns-nameservers 192.168.X.X
```
Or possibly try 'allow-hotplug' on eth0, rather than 'auto'

Assigning a static IP to eth0 does not bring it up at bootup either. Only "ifconfig eth0 up" makes the interface active after boot.

The other 13 identical machines, plus my laptop, all have the iface line in /etc/network/interfaces commented out, so it doesn't appear that the default is to have it uncommented.

---

### Post by bab1 on 2010-09-07
> **jimjohnsean said:**
> Network card (82566DM-2 Gigabit Network Connection) is DISABLED upon reboot. Only way to bring it out of disabled mode is to rerun dhclient to obtain a DHCP lease. Upon reboot though, the NIC is back into disabled mode.

A workaround I have found is to uncomment the iface line in /etc/network/interfaces, but considering I have 14 identical PCs to this one, and only this one is currently giving me grief, I am trying to find the root cause
This is not a workaround.  This is how it should be (even if it is 14 hosts that have it wrong).  Do you have a script to run dhclient?  Is it possible you modified the system some time ago to cure something else?  See the text in red below.> 

/etc/network/interfaces

```
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0 [COLOR="Red"]**<--This is for bringing up the NIC upon bootup**[/COLOR]
#iface eth0 inet dhcp [COLOR="red"]**This is for configuring the NIC to request an IP via DHCP**[/COLOR]

```


You need both statements for the NIC to operate correctly.

---

### Post by Iowan on 2010-09-07
Just to try a different spin...
What happens if you:```
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
[COLOR="Red"]#[/COLOR]auto eth0
#iface eth0 inet dhcp
```

---

### Post by bab1 on 2010-09-07
> **Iowan said:**
> Just to try a different spin...
What happens if you:```
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
[COLOR="Red"]#[/COLOR]auto eth0
#iface eth0 inet dhcp
```

I believe the OP does not have NM managing this interface.  This means the host will not have eth0 configured at all.  My best guess is that dhclient will also now fail.

---

### Post by jimjohnsean on 2010-09-07
> **Iowan said:**
> Just to try a different spin...
What happens if you:```
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
[COLOR="Red"]#[/COLOR]auto eth0
#iface eth0 inet dhcp
```

Yep - it fails to bring up the NIC as well

I get that uncommenting the iface line works (for DHCP - but note my previous comment that setting a static IP doesn't, i.e.

```
iface eth0 inet static
address 172.29.193.213
netmask 255.255.255.192
gateway 172.29.193.193
```

still makes the NIC disabled). I remember having to use the iface line in Hardy, but from my understanding, NetworkManager is supposed to take care of it. I have had a look at my other 120 boxes (not identical to this one hardware wise, but all Lucid 64bit - I manage a fleet of scientific machines for computation), and not one of them has the inet line uncommented. 

Another post related to this (mostly all concerning the e1000e kernel module) said to install wicd - which I did, and having the line commented brought up the interface with wicd installed, so I think it is a NetworkManager problem.

From one of the identical boxes (which is working), this process exists:

```
/sbin/dhclient -d -sf /usr/lib/NetworkManager/nm-dhcp-client.action -pf /var/run/dhclient-eth0.pid -lf /var/lib/dhcp3/dhclient-966955a4-2b84-411e-97c5-554aff2f129e-eth0.lease -cf /var/run/nm-dhclient-eth0.conf eth0
```

but sure enough that process doesn't exist on the disabled NIC.

Is there any point in removing network-manager, and reinstalling?

---

### Post by bab1 on 2010-09-07
> **jimjohnsean said:**
> Yep - it fails to bring up the NIC as well

I get that uncommenting the iface line works (for DHCP - but note my previous comment that setting a static IP doesn't, i.e.

```
iface eth0 inet static
address 172.29.193.213
netmask 255.255.255.192
gateway 172.29.193.193
```

still makes the NIC disabled). I remember having to use the iface line in Hardy, but from my understanding, NetworkManager is supposed to take care of it. I have had a look at my other 120 boxes (not identical to this one hardware wise, but all Lucid 64bit - I manage a fleet of scientific machines for computation), and not one of them has the inet line uncommented. 

Another post related to this (mostly all concerning the e1000e kernel module) said to install wicd - which I did, and having the line commented brought up the interface with wicd installed, so I think it is a NetworkManager problem.

From one of the identical boxes (which is working), this process exists:

```
/sbin/dhclient -d -sf /usr/lib/NetworkManager/nm-dhcp-client.action -pf /var/run/dhclient-eth0.pid -lf /var/lib/dhcp3/dhclient-966955a4-2b84-411e-97c5-554aff2f129e-eth0.lease -cf /var/run/nm-dhclient-eth0.conf eth0
```

but sure enough that process doesn't exist on the disabled NIC.

Is there any point in removing network-manager, and reinstalling?

I don't think NM knows to manage the interface.  See your note > /etc/NetworkManager/nm-system-settings.conf

```

[main]
plugins=ifupdown,keyfile

[ifupdown]
[COLOR="Red"]**managed=false**[/COLOR]
```


**[COLOR="RoyalBlue"]Edit:**I'll bet it has everything to do with trying WICD and messing with NM. I would try purging NM and reinstalling it. [/COLOR]

---

### Post by elico on 2010-09-07
is the manual way to turn the interface up is working  at all?

if it wont get up using the regular methods at startup just make a script to run on start up that contains

> ifconfig eth0 up

and in case of dhcpclient


> ifconfig eth0 up
dhclient eth0

---

