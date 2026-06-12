---
title: "Wired Connection Won't Connect 12.04"
date: 2012-05-19
forum: Networking &amp; Wireless
---

### Post by socialdtk on 2012-05-19
After upgrading to 12.04 client edition my wired connection stopped working. It works just fine with 12.04 server, the latest release of Debian, and Fedora. I am connecting to the Internet via a LAN port on a Buffalo N Series Router.

sudo -lshw

*-network
                description: Ethernet interface
                product: 82562EZ 10/100 Ethernet Controller
                vendor: Intel Corporation
                physical id: 8
                bus info: pci@0000:01:08.0
                logical name: eth0
                version: 02
                serial: 00:13:20:5c:74:78
                size: 100Mbit/s
                capacity: 100Mbit/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation

\etc\network\interfaces config file

auto lo
iface lo inet loopback

\etc\NetworkManager\NetworkManager.conf

[main]
plugins=ifupdown,keyfile
dns=dnsmasq

[ifupdown]
managed=false

---

### Post by chili555 on 2012-05-19
Please let us see:```
dmesg | grep -e e100 -e eth0
```Thanks.

---

### Post by socialdtk on 2012-05-19
dmesg | grep -e e100 -e eth0

[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee10000 (reserved)
[    0.371594] pci 0000:01:08.0: Firmware left e100 interrupts enabled; disabling
[    1.622264] e100: Intel(R) PRO/100 Network Driver, 3.5.24-k2-NAPI
[    1.622269] e100: Copyright(c) 1999-2006 Intel Corporation
[    1.622333] e100 0000:01:08.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    1.659055] e100 0000:01:08.0: PME# disabled
[    1.659746] e100 0000:01:08.0: eth0: addr 0xfeaff000, irq 20, MAC addr 00:13:20:5c:74:78
[    5.039209] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   16.781046] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   16.781911] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   16.784167] e100 0000:01:08.0: eth0: NIC Link is Up 100 Mbps Full Duplex
[   16.784430] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   27.232023] eth0: no IPv6 routers present
[   75.976012] eth0: no IPv6 routers present
[  123.352022] eth0: no IPv6 routers present
[  171.760019] eth0: no IPv6 routers present
[  517.104012] eth0: no IPv6 routers present
[  564.616012] eth0: no IPv6 routers present
[  612.592014] eth0: no IPv6 routers present
[  660.984020] eth0: no IPv6 routers present
[  923.889058] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  923.892170] e100 0000:01:08.0: eth0: NIC Link is Up 100 Mbps Full Duplex
[  923.892505] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  934.112023] eth0: no IPv6 routers present
[26999.093179] ADDRCONF(NETDEV_UP): eth0: link is not ready
[26999.096169] e100 0000:01:08.0: eth0: NIC Link is Up 100 Mbps Full Duplex
[26999.096332] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[27010.208026] eth0: no IPv6 routers present
[27058.768033] eth0: no IPv6 routers present
[27106.272015] eth0: no IPv6 routers present
[27154.200014] eth0: no IPv6 routers present
[27499.280014] eth0: no IPv6 routers present
[27547.728026] eth0: no IPv6 routers present
[27596.000026] eth0: no IPv6 routers present
[27643.104020] eth0: no IPv6 routers present
[27988.224035] eth0: no IPv6 routers present
[28036.928014] eth0: no IPv6 routers present
[28084.432024] eth0: no IPv6 routers present
[28132.312014] eth0: no IPv6 routers present
[28477.280014] eth0: no IPv6 routers present
[28525.624021] eth0: no IPv6 routers present
[28544.176030] eth0: no IPv6 routers present
[28555.085018] ADDRCONF(NETDEV_UP): eth0: link is not ready
[28555.088166] e100 0000:01:08.0: eth0: NIC Link is Up 100 Mbps Full Duplex
[28555.089852] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[28565.776015] eth0: no IPv6 routers present
[28613.232025] eth0: no IPv6 routers present
[28661.984035] eth0: no IPv6 routers present
[28709.104018] eth0: no IPv6 routers present
[29054.480032] eth0: no IPv6 routers present
[29102.352022] eth0: no IPv6 routers present
[29150.776031] eth0: no IPv6 routers present
[29198.296028] eth0: no IPv6 routers present
[29543.232021] eth0: no IPv6 routers present
[29591.168032] eth0: no IPv6 routers present
[29639.800025] eth0: no IPv6 routers present
[29687.760033] eth0: no IPv6 routers present
[30032.368013] eth0: no IPv6 routers present
[30080.960015] eth0: no IPv6 routers present

---

### Post by socialdtk on 2012-05-19
Also, it looks like the router is attempting to issue the PC an IPV4 address of 192.168.11.61. I have IPV6 set to ignore in Network Manager.

---

### Post by chili555 on 2012-05-19
Very interesting; I thought this was an e1000 device, not e100. Let's try to pin that down:```
lspci -nn | grep 0200
```This looks pretty normal:> [ 16.784167] e100 0000:01:08.0: eth0: NIC Link is Up 100 Mbps Full Duplex
[ 16.784430] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 27.232023] eth0: no IPv6 routers present

---

### Post by socialdtk on 2012-05-19
sudo lspci -nn | grep 0200

01:08.0 Ethernet controller [0200]: Intel Corporation 82562EZ 10/100 Ethernet Controller [8086:1050] (rev 02)

---

### Post by chili555 on 2012-05-19
It is indeed an e100 device. I wonder what Network Manager is doing all this time:```
sudo cat /var/log/syslog | grep -e etwork -e e100 | tail -n20
```Does it try to connect and fail or does it connect and then quickly disconnect? What are its symptoms?

---

### Post by socialdtk on 2012-05-19
When I enable my network adapter I receive a message that state:

"Network
Disconnected you are offline"

Afterwards, Network Manager attempts to connect to the network until the adapter is disabled. There have been a few instances where it has established a connection, but I am still unable to access my router and the Internet.

sudo cat /var/log/syslog | grep -e etwork -e e100 | tail -n20

May 19 10:28:44 anon NetworkManager[3015]: <info> disable requested (sleeping: no  enabled: yes)
May 19 10:28:44 anon NetworkManager[3015]: <info> sleeping or disabling...
May 19 10:28:44 anon NetworkManager[3015]: <info> (eth0): now unmanaged
May 19 10:28:44 anon NetworkManager[3015]: <info> (eth0): device state change: ip-config -> unmanaged (reason 'sleeping') [70 10 37]
May 19 10:28:44 anon NetworkManager[3015]: <info> (eth0): deactivating device (reason 'sleeping') [37]
May 19 10:28:44 anon NetworkManager[3015]: <info> (eth0): canceled DHCP transaction, DHCP client pid 3314
May 19 10:28:44 anon NetworkManager[3015]: <info> (eth0): cleaning up...
May 19 10:28:44 anon NetworkManager[3015]: <info> (eth0): taking down device.
May 19 10:28:44 anon NetworkManager[3015]: <info> (eth0): carrier now OFF (device state 10)
May 19 10:29:06 anon NetworkManager[3015]: <info> Saved default wired connection 'Wired connection 1' to persistent storage
May 19 10:29:07 anon NetworkManager[3015]:    Ifupdown: get unmanaged devices count: 0
May 19 10:29:07 anon NetworkManager[3015]: <info> (eth0): now managed
May 19 10:29:07 anon NetworkManager[3015]: <info> (eth0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
May 19 10:29:07 anon NetworkManager[3015]: <info> (eth0): bringing up device.
May 19 10:29:07 anon NetworkManager[3015]: <info> (eth0): preparing device.
May 19 10:29:07 anon NetworkManager[3015]: <info> (eth0): deactivating device (reason 'managed') [2]
May 19 10:29:07 anon kernel: [31093.008175] e100 0000:01:08.0: eth0: NIC Link is Up 100 Mbps Full Duplex
May 19 10:29:07 anon NetworkManager[3015]:    Ifupdown: get unmanaged devices count: 0
May 19 10:29:07 anon NetworkManager[3015]: <info> (eth0): carrier now ON (device state 20)
May 19 10:29:07 anon NetworkManager[3015]: <info> (eth0): device state change: unavailable -> disconnected (reason 'carrier-changed') [20 30 40]

Thanks so much for all the help you've given me so far!

---

### Post by chili555 on 2012-05-19
What does this tell us?```
nm-tool
```I will be at another computer running Network Manager in about an hour.

---

### Post by socialdtk on 2012-05-19
After 1 hours worth of attempting to connect to the network I finally established a connection and was issued the IPV4 address that my router has been trying to assign:

nm-tool

NetworkManager Tool

State: connected (global)

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            e100
  State:             connected
  Default:           yes
  HW Address:        00:13:20:5C:74:78

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.11.61
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.11.1

    DNS:             192.168.11.1

I then ran a ping on the router. Here are the results:

PING 192.168.11.1 (192.168.11.1) 56(84) bytes of data.
64 bytes from 192.168.11.1: icmp_req=4 ttl=64 time=0.224 ms
From 192.168.11.61 icmp_seq=6 Destination Host Unreachable
From 192.168.11.61 icmp_seq=7 Destination Host Unreachable
From 192.168.11.61 icmp_seq=9 Destination Host Unreachable
From 192.168.11.61 icmp_seq=10 Destination Host Unreachable
From 192.168.11.61 icmp_seq=11 Destination Host Unreachable
From 192.168.11.61 icmp_seq=12 Destination Host Unreachable
From 192.168.11.61 icmp_seq=13 Destination Host Unreachable
64 bytes from 192.168.11.1: icmp_req=18 ttl=64 time=0.256 ms
64 bytes from 192.168.11.1: icmp_req=25 ttl=64 time=0.241 ms
64 bytes from 192.168.11.1: icmp_req=33 ttl=64 time=0.243 ms

--- 192.168.11.1 ping statistics ---
36 packets transmitted, 4 received, +7 errors, 88% packet loss, time 35222ms
rtt min/avg/max/mdev = 0.224/0.241/0.256/0.011 ms, pipe 3

Afterwards, I disabled the network adapter again, reset network manager, and attempted to reconnect but was unable to establish connectivity. Here is the output of the same commands:

nm-tool

NetworkManager Tool

State: connecting

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            e100
  State:             connecting (getting IP configuration)
  Default:           no
  HW Address:        00:13:20:5C:74:78

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

ping 192.168.11.1

connect: Network is unreachable

---

### Post by chili555 on 2012-05-19
> I disabled the network adapter again, reset network manager,How so? What did you do? With no settings at all, except ignore IPv6, it ought to connect on boot with no human help if there is a cable attached with a carrier signal.

---

### Post by socialdtk on 2012-05-19
In the task pane, I clicked the Network Manager icon and then Enable Networking to disable. I then reactivated Network Manager following the same sequence.

I have troubleshoot the physical connection by exchanging the patch cable for multiple patch cords that are known to working. I also booted my Ubuntu server partition and pinged google.com to confirm that my network adapter is good.

After reactivating it took around 20 minutes to re-establish a network connection. I still cannot connect to the internet, and have 90+ percent packet loss when attempting to ping the router.

---

### Post by socialdtk on 2012-05-19
After establishing a new connection I was able to successfully ping google.com ( 74.125.228.40 ) but I am still losing 76% of all packets sent.

PING 74.125.228.40 (74.125.228.40) 56(84) bytes of data.
64 bytes from 74.125.228.40: icmp_req=9 ttl=54 time=21.6 ms
64 bytes from 74.125.228.40: icmp_req=11 ttl=54 time=22.5 ms
64 bytes from 74.125.228.40: icmp_req=14 ttl=54 time=22.3 ms
64 bytes from 74.125.228.40: icmp_req=16 ttl=54 time=21.9 ms
64 bytes from 74.125.228.40: icmp_req=18 ttl=54 time=21.8 ms
64 bytes from 74.125.228.40: icmp_req=25 ttl=54 time=22.1 ms
64 bytes from 74.125.228.40: icmp_req=27 ttl=54 time=22.4 ms
64 bytes from 74.125.228.40: icmp_req=33 ttl=54 time=22.1 ms
64 bytes from 74.125.228.40: icmp_req=38 ttl=54 time=22.1 ms

--- 74.125.228.40 ping statistics ---
39 packets transmitted, 9 received, 76% packet loss, time 38189ms
rtt min/avg/max/mdev = 21.697/22.149/22.527/0.268 ms

I am unable to access any website via web browser and cannot download LAMP software via apt-get.

---

### Post by chili555 on 2012-05-19
> I also booted my Ubuntu server partition and pinged google.com to confirm that my network adapter is good.Is the server running Network Manager or is it using manual methods; i.e. /etc/network/interfaces?

I wonder if the desktop edition is somehow corrupted, especially Network Manager or DHCP. Is there any improvement if you set Network Manager to use a static IP address? Please see attached.

Please use an IP address outside the range used by the DHCP server in the router.

---

### Post by socialdtk on 2012-05-19
Here is the results after changing the Network Adapter to manual and using the following settings:

IP Address: 192.168.11.120 ( This IP address is outside the routers DHCP range )
Netmask: 255.255.255.0
Gateway: 192.168.11.1 ( The Routers IP Address )
DNS Server: 192.168.11.1, 8.8.8.8

ping 192.168.11.1

PING 192.168.11.1 (192.168.11.1) 56(84) bytes of data.
64 bytes from 192.168.11.1: icmp_req=3 ttl=64 time=0.248 ms
64 bytes from 192.168.11.1: icmp_req=4 ttl=64 time=0.244 ms
64 bytes from 192.168.11.1: icmp_req=8 ttl=64 time=0.246 ms
64 bytes from 192.168.11.1: icmp_req=13 ttl=64 time=0.210 ms
64 bytes from 192.168.11.1: icmp_req=17 ttl=64 time=0.247 ms
64 bytes from 192.168.11.1: icmp_req=18 ttl=64 time=0.249 ms
64 bytes from 192.168.11.1: icmp_req=37 ttl=64 time=0.242 ms
64 bytes from 192.168.11.1: icmp_req=38 ttl=64 time=0.252 ms
64 bytes from 192.168.11.1: icmp_req=43 ttl=64 time=0.255 ms
64 bytes from 192.168.11.1: icmp_req=45 ttl=64 time=0.231 ms

--- 192.168.11.1 ping statistics ---
48 packets transmitted, 10 received, 79% packet loss, time 47012ms
rtt min/avg/max/mdev = 0.210/0.242/0.255/0.018 ms

---

### Post by socialdtk on 2012-05-19
Also, this is my 2nd time installing the Desktop Edition of Ubuntu 12.04. Both times I have experienced the same network problems booting via live disk, and after installation.

---

### Post by chili555 on 2012-05-19
Is the server running Network Manager or is it using manual methods; i.e. /etc/network/interfaces? What is the server's IP address and route?```
ifconfig
route -n
```And on the Desktop Edition?```
ifconfig
route -n
```Weird!

---

### Post by socialdtk on 2012-05-19
The server is running Network Manager and auto-detecting the network connection. During the installation of the server software it downloads many updates, and other applications via apt-get repositories.

The Desktop Edition is unable to establish a network connection to download updates or additional files during installation, and I am unable to connect to these software repositories after Ubuntu is installed.

When I run ifconfig on the desktop edition I get the following output:

eth0      Link encap:Ethernet  HWaddr 00:13:20:5c:74:78  
          inet addr:192.168.11.120  Bcast:192.168.11.255  Mask:255.255.255.0
          inet6 addr: fe80::213:20ff:fe5c:7478/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:626 errors:2164 dropped:0 overruns:0 frame:2164
          TX packets:4276 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:58560 (58.5 KB)  TX bytes:714920 (714.9 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:9038 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9038 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:729428 (729.4 KB)  TX bytes:729428 (729.4 KB)

route -n gives me:

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.11.1    0.0.0.0         UG    0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
192.168.11.0    0.0.0.0         255.255.255.0   U     1      0        0 eth0

---

### Post by eumetaxas on 2012-05-19
```
sudo dhclient eth0
```

solved the same problem for me but i have to do it every tine i log in:(

Sad, Canonical should be able to detect these faults during betas

---

### Post by chili555 on 2012-05-19
> **eumetaxas said:**
> ```
sudo dhclient eth0
```

solved the same problem for me but i have to do it every tine i log in:(

Sad, Canonical should be able to detect these faults during betasDid you run the beta and offer your input? Did you post one single request for assistance with your wired connection? 

Canonical doesn't have access to every possible network device on every possible computer; that's why they run betas.

Sad. Your post is in no way helpful.

---

### Post by chili555 on 2012-05-19
> The server is running Network Manager and auto-detecting the network connection. During the installation of the server software it downloads many updates, and other applications via apt-get repositories.

The Desktop Edition is unable to establish a network connection to download updates or additional files during installation, and I am unable to connect to these software repositories after Ubuntu is installed.
Your readings look entirely normal except here:> eth0 Link encap:Ethernet HWaddr 00:13:20:5c:74:78
inet addr:192.168.11.120 Bcast:192.168.11.255 Mask:255.255.255.0
inet6 addr: fe80::213:20ff:fe5c:7478/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:626 [COLOR="Red"]errors:2164[/COLOR] dropped:0 overruns:0 frame:2164
TX packets:4276 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:58560 (58.5 KB) TX bytes:714920 (714.9 KB)
And, of course, here:> 48 packets transmitted, 10 received, [COLOR="Red"]79% packet loss[/COLOR], time 47012msBy setting a static IP, I think we've eliminated DHCP as a problem. I wonder what Network Manager is doing all this time. Please run and post:```
sudo cat /var/log/syslog | grep etwork | tail -n20
```Is there any improvement with:```
sudo ethtool -s eth0 speed 10 duplex full autoneg on
```

---

### Post by socialdtk on 2012-05-19
sudo cat /var/log/syslog | grep etwork | tail -n20

May 19 16:36:58 anon NetworkManager[724]: <info> (eth0): deactivating device (reason 'none') [0]
May 19 16:37:01 anon NetworkManager[724]: <info> Auto-activating connection 'Wired connection 1'.
May 19 16:37:01 anon NetworkManager[724]: <info> Activation (eth0) starting connection 'Wired connection 1'
May 19 16:37:01 anon NetworkManager[724]: <info> (eth0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
May 19 16:37:01 anon NetworkManager[724]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
May 19 16:37:01 anon NetworkManager[724]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) started...
May 19 16:37:01 anon NetworkManager[724]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) scheduled...
May 19 16:37:01 anon NetworkManager[724]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) complete.
May 19 16:37:01 anon NetworkManager[724]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) starting...
May 19 16:37:01 anon NetworkManager[724]: <info> (eth0): device state change: prepare -> config (reason 'none') [40 50 0]
May 19 16:37:01 anon NetworkManager[724]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) successful.
May 19 16:37:01 anon NetworkManager[724]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
May 19 16:37:01 anon NetworkManager[724]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) complete.
May 19 16:37:01 anon NetworkManager[724]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
May 19 16:37:01 anon NetworkManager[724]: <info> (eth0): device state change: config -> ip-config (reason 'none') [50 70 0]
May 19 16:37:01 anon NetworkManager[724]: <info> Activation (eth0) Beginning DHCPv4 transaction (timeout in 45 seconds)
May 19 16:37:01 anon NetworkManager[724]: <info> dhclient started with pid 2055
May 19 16:37:01 anon NetworkManager[724]: <info> Activation (eth0) Beginning IP6 addrconf.
May 19 16:37:01 anon NetworkManager[724]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
May 19 16:37:01 anon NetworkManager[724]: <info> (eth0): DHCPv4 state changed nbi -> preinit

sudo ethtool -s eth0 speed 10 duplex full autoneg on

sudo: ethtool: command not found

I also tried this command: "sudo dhclient eth0" and am prompted to complete the rest of the command. I have to close the terminal or terminate with an alt-c to kill the problem

---

### Post by chili555 on 2012-05-19
> I also tried this command: "sudo dhclient eth0" and am prompted to complete the rest of the command. I have to close the terminal or terminate with an alt-c to kill the problemManual methods; e.g. dhclient, are unlikely to work in the presence of Network Manager.

Your logs reflect the attempt with dhclient and don't give us much help as to what NM is doing.

Let's try to reinstall Network Manager from the apt cache.```
sudo apt-get install --reinstall network-manager
```Does it succeed? Does it help?

---

### Post by socialdtk on 2012-05-19
sudo apt-get install --reinstall network-manager

Reading package list... Done
Building dependency tree
Reading state information... Done
Reinstallation of network-manager is not possible, it cannot be downloaded.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Should I download network manager for the 12.04 repositories and install the package? If so, are all network managers the same or does the software that I need to install depend on the hardware that I have? Thanks again for all of your help. I really appreciate it.

---

### Post by socialdtk on 2012-05-19
I'm not sure if this will be helpful in troubleshooting this problem, but I think it better demonstrates what is actually happening as far as the lost packets go:

**traceroute to google.com 1**

```

traceroute to 74.125.228.38 ( 74.125.228.38 ), 30 hops max, 60 byte packets
 1  anon (192.168.11.61)  1601.771 ms !H  1601.762 ms !H  1601.749 ms !H

```

**traceroute to google.com 2**

```

traceroute to 74.125.228.38 ( 74.125.228.38 ) , 30 hops max, 60 byte packets
 1  * * *
 2  * * *
 3  * * *
 4  * * *
 5  * * *
 6  * * *
 7  * * *
 8  * 72.14.219.254 ( 72.14.219.254 )  64.342 ms *
 9  * * *
10  * * *
11  * * *
12  74.125.228.38 ( 74.125.228.38 )  58.596 ms  59.104 ms *
```

**traceroute to google from my Mac**

```

 1  dd-wrt ( 192.168.11.1 )  1.491 ms  1.047 ms  0.969 ms
 2  10.0.0.1 ( 10.0.0.1 )  1.609 ms  1.362 ms  1.728 ms
 3  nc-76-6-0-1.dhcp.embarqhsd.net ( 76.6.0.1 )  49.742 ms  50.292 ms  50.118 ms
 4  nc-65-162-201-233.sta.embarqhsd.net ( 65.162.201.233 )  54.658 ms  66.573 ms  85.050 ms
 5  206-51-88-118.centurylink.net ( 206.51.88.118 )  48.067 ms  47.213 ms  50.657 ms
 6  bb-asbnvacy-jx9-02-ae3.0.core.centurytel.net ( 208.110.248.170 )  72.721 ms  73.975 ms  75.676 ms
 7  bb-asbnvacy-jx9-01-ae0.0.core.centurytel.net ( 208.110.248.117 )  55.281 ms  50.976 ms  53.399 ms
 8  72.14.219.254 ( 72.14.219.254 )  57.804 ms  62.644 ms  60.535 ms
 9  72.14.238.214 ( 72.14.238.214 )  58.860 ms  55.239 ms  54.850 ms
10  72.14.238.175 ( 72.14.238.175 )  54.225 ms  59.205 ms  57.635 ms
11  iad23s06-in-f6.1e100.net ( 74.125.228.38 )  72.645 ms  70.227 ms  71.312 ms
```

---

### Post by socialdtk on 2012-05-20
I took this snapshot of the syslog right after a connection was established via DHCP:

```

May 19 23:47:56 anon NetworkManager[724]: <info> (eth0): device state change: config -> ip-config (reason 'none') [50 70 0]
May 19 23:47:56 anon NetworkManager[724]: <info> Activation (eth0) Beginning DHCPv4 transaction (timeout in 45 seconds)
May 19 23:47:56 anon NetworkManager[724]: <info> dhclient started with pid 5064
May 19 23:47:56 anon NetworkManager[724]: <info> Activation (eth0) Beginning IP6 addrconf.
May 19 23:47:56 anon NetworkManager[724]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
May 19 23:47:56 anon NetworkManager[724]: <info> (eth0): DHCPv4 state changed nbi -> preinit
May 19 23:47:56 anon NetworkManager[724]: <info> (eth0): DHCPv4 state changed preinit -> reboot
May 19 23:47:56 anon NetworkManager[724]: <info>   address 192.168.11.61
May 19 23:47:56 anon NetworkManager[724]: <info>   prefix 24 (255.255.255.0)
May 19 23:47:56 anon NetworkManager[724]: <info>   gateway 192.168.11.1
May 19 23:47:56 anon NetworkManager[724]: <info>   hostname 'anon'
May 19 23:47:56 anon NetworkManager[724]: <info>   nameserver '192.168.11.1'
May 19 23:47:56 anon NetworkManager[724]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
May 19 23:47:56 anon NetworkManager[724]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Commit) started...
May 19 23:47:57 anon NetworkManager[724]: <info> DNS: starting dnsmasq...
May 19 23:47:57 anon NetworkManager[724]: <info> (eth0): writing resolv.conf to /sbin/resolvconf
May 19 23:47:57 anon NetworkManager[724]: <info> (eth0): device state change: ip-config -> activated (reason 'none') [70 100 0]
May 19 23:47:57 anon NetworkManager[724]: <info> Policy set 'Wired connection 1' (eth0) as default for IPv4 routing and DNS.
May 19 23:47:57 anon NetworkManager[724]: <info> Activation (eth0) successful, device activated.
May 19 23:47:57 anon NetworkManager[724]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Commit) complete.
```

After troubleshooting for awhile I found that if I manually assign the IPV4 address then seconds later I establish a LAN connection. If I set IPV4 to Automatic (DHCP) it takes between 5 and 30 minutes before the PC receives its DHCP configuration from the router. It looks the issue is stemming from my PC not receiving a significant amount of packets that are being transmitted across the network. I think this because:

1. The time it takes to receive the routers DHCP configuration
2. The high packet lose in ping/traceroutes

I eliminated the router from the equation by connecting my laptop directly to the server, manually setting the IP addresses and pinging back and forth. I still lose 75% of all packets sent.

---

### Post by chili555 on 2012-05-20
> Should I download network manager for the 12.04 repositories and install the package? If so, are all network managers the same or does the software that I need to install depend on the hardware that I have? Yes, please. Match the version you have now and your architecture, either 32- or 64-bit. Find out with:```
sudo dpkg -s network-manager
```Then go here: [http://packages.ubuntu.com/precise/net/network-manager](http://packages.ubuntu.com/precise/net/network-manager)

Download the package and I suggest moving it to your desktop with a USB key. Then, let's see if we can connect *without* NM. If so, we'll simply omit it. ```
sudp dpkg -P network-manager
sudo ifconfig eth0 down
sudo /etc/init.d/networking restart
sudo ifconfig eth0 192.168.11.61 up
ping -c3 192.168.11.1
```If this works, we can dispense with NM altogether if you wish. We'll need to write a couple of files to make it persistent.

---

### Post by socialdtk on 2012-05-20
I think that the problem may have been a bad network card. I ran several Live discs this morning all of which I experienced very high packet loss on. My network card must have went bad between the time that I switched from Ubuntu Server to desktop edition.

The good news is I was able to pull a new NIC card from the PC graveyard at work, installed it, and am typing this repsonse from Ubuntu Desktop Edtion. Thank you so much for all of your help!

```

nm-tool
```

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        00:14:BF:5E:06:55

  Capabilities:
    Carrier Detect:  yes
    Speed:           1000 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.11.14
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.11.1

    DNS:             192.168.11.1

```

ping 192.168.11.1
```
PING 192.168.11.1 (192.168.11.1) 56(84) bytes of data.
64 bytes from 192.168.11.1: icmp_req=1 ttl=64 time=0.337 ms
64 bytes from 192.168.11.1: icmp_req=2 ttl=64 time=0.231 ms
64 bytes from 192.168.11.1: icmp_req=3 ttl=64 time=0.235 ms
64 bytes from 192.168.11.1: icmp_req=4 ttl=64 time=0.239 ms
64 bytes from 192.168.11.1: icmp_req=5 ttl=64 time=0.241 ms
64 bytes from 192.168.11.1: icmp_req=6 ttl=64 time=0.170 ms
64 bytes from 192.168.11.1: icmp_req=7 ttl=64 time=0.232 ms
64 bytes from 192.168.11.1: icmp_req=8 ttl=64 time=0.232 ms

--- 192.168.11.1 ping statistics ---
8 packets transmitted, 8 received, 0% packet loss, time 7000ms
rtt min/avg/max/mdev = 0.170/0.239/0.337/0.046 ms

---

### Post by chili555 on 2012-05-20
Awesome! I'm glad it's working by whatever means.

---

