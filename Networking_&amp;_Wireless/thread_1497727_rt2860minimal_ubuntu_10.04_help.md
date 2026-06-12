---
title: "rt2860/minimal ubuntu 10.04 help"
date: 2010-05-30
forum: Networking &amp; Wireless
---

### Post by AuXBoX on 2010-05-30
I've been trying to get this going for a couple of weeks
i have a rt2860 chipset wifi card and installed minimal install ubuntu 10.04.
I installed the drivers from this:
```
http://ubuntuforums.org/showthread.php?t=1476007
```

lspci -nn | grep RaLink
```
03:00.0 Network controller [0280]: RaLink RT2860 [1814:0781]
```

ifconfig
```
eth0      Link encap:Ethernet  HWaddr 00:1f:d0:26:79:79
          inet addr:192.168.254.4  Bcast:192.168.254.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:d0ff:fe26:7979/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:234 errors:0 dropped:0 overruns:0 frame:0
          TX packets:193 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:24729 (24.7 KB)  TX bytes:28055 (28.0 KB)
          Interrupt:30 Base address:0x4000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

ra0       Link encap:Ethernet  HWaddr e0:cb:4e:9f:eb:5f
          inet6 addr: fe80::e2cb:4eff:fe9f:eb5f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:109 (109.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18

```

iwconfig
```
ra0       Ralink STA  ESSID:""  Nickname:"RT2860STA"
          Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated
          Bit Rate:1 Mb/s
          RTS thr:off   Fragment thr:off
          Link Quality=10/100  Signal level:0 dBm  Noise level:-87 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

lsmod | grep rt2860sta

```
rt2860sta             768598  1
```

dmesg
not too sure how. tried dmesg | grep ra0
```
[  181.721508] ra0: no IPv6 routers present
```

sudo lshw -C network
```
*-network
       description: Wireless interface
       product: RT2860
       vendor: RaLink
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: ra0
       version: 00
       serial: e0:cb:4e:9f:eb:5f
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=RALINK WLAN driverversion=2.3.0.0 latency=0 multicast=yes wireless=Ralink STA
       resources: irq:18 memory:df000000-df00ffff

```

iwlist scan
```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Interface doesn't support scanning.

ra0       Scan completed :
          Cell 01 - Address: 00:13:A3:C5:C9:4C
                    Protocol:802.11b/g
                    ESSID:"home"
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:24/100  Signal level:-80 dBm  Noise level:-75 dBm
                    Encryption key:off
                    Bit Rates:54 Mb/s

```
The next door neighbor has wifi with wpa2. I think this might be stuffing things up

lsb_release -d
```
Description:    Ubuntu 10.04 LTS
```

uname -mr
```
2.6.32-21-generic-pae i686
```

sudo /etc/init.d/networking restart
```
* Reconfiguring network interfaces...                                          There is already a pid file /var/run/dhclient.ra0.pid with pid 1099
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/ra0/e0:cb:4e:9f:eb:5f
Sending on   LPF/ra0/e0:cb:4e:9f:eb:5f
Sending on   Socket/fallback
There is already a pid file /var/run/dhclient.eth0.pid with pid 1144
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/eth0/00:1f:d0:26:79:79
Sending on   LPF/eth0/00:1f:d0:26:79:79
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.254.254 port 67
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/ra0/e0:cb:4e:9f:eb:5f
Sending on   LPF/ra0/e0:cb:4e:9f:eb:5f
Sending on   Socket/fallback
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 21
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 12
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
ssh stop/waiting
ssh start/running, process 1241
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/eth0/00:1f:d0:26:79:79
Sending on   LPF/eth0/00:1f:d0:26:79:79
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPOFFER of 192.168.254.4 from 192.168.254.254
DHCPREQUEST of 192.168.254.4 on eth0 to 255.255.255.255 port 67
DHCPACK of 192.168.254.4 from 192.168.254.254
bound to 192.168.254.4 -- renewal in 872205725 seconds.
ssh stop/waiting
ssh start/running, process 1285
                                                                         [ OK ]

```

I've reformatted so many time over the past 2 weeks, i've had it connected with wicd but then something goes wrong and it disconnects and cannot connect again.

At the moment its a fresh install of minimal ubuntu 10.04 with wireless-tool installed.

---

### Post by rhd on 2010-05-31
If you have any kind of available internet connection, try 
```
sudo apt-get install broadcom-sta-source broadcom-sta-common
```
or download both of them (and ALL OF THEIR DEPENDENCIES)  from packages.ubuntu.com. That fixed the problem for me.

---

### Post by Talon2 on 2010-05-31
> **rhd said:**
> If you have any kind of available internet connection, try 
```
sudo apt-get install broadcom-sta-source broadcom-sta-common
```
or download both of them (and ALL OF THEIR DEPENDENCIES)  from packages.ubuntu.com. That fixed the problem for me.

Please explain to me how installing these files is going to help with a device based on an Ralink chipset?

---

### Post by Talon2 on 2010-05-31
I have a device based on the rt2870 chipset.  I managed to get it working and I filed this bug:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/549801](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/549801)

Note the link that I posted.

---

### Post by AuXBoX on 2010-05-31
> **Talon2 said:**
> I have a device based on the rt2870 chipset.  I managed to get it working and I filed this bug:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/549801](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/549801)

Note the link that I posted.

Thanks Talon i'll have to try again tomorrow and report back.
Briefly read through it and i hope it is the same for pci as it is with usb

---

