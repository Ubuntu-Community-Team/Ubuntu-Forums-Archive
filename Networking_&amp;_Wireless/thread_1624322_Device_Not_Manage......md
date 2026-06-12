---
title: "Device Not Manage?....."
date: 2010-11-17
forum: Networking &amp; Wireless
---

### Post by VcDeveloper on 2010-11-17
My kvm network looks like this:

Ubuntu 10.10 Desktop Server w/qemu-kvm (main server) 192.168.1.65
----------| Ubuntu 9.10 Desktop Server - Web 192.168.1.71
----------| Ubuntu 10.10 Desktop Server - MySql 192.168.1.72

2wire Router only allows HTTP/HTTPS to my **kvm** web server.  I have two NIC's, NIC2 = is used by the **kvm** servers and all can connect directly to the internet.  Not of my friends can connect to my web server.

I have my **interfaces** file configured this way for my **kvm's**. Using **qemu-kvm** w/**bridge-utils**:

```

auto lo
iface lo inet loopback

auto eth1
iface eth1 inet manual

auto br0
iface br0 inet static
        address 192.168.1.66
        network 192.168.1.0
        netmask 255.255.255.0
        broadcast 192.168.1.255
        gateway 192.168.1.254
        bridge_ports eth1
        bridge_stp off
    bridge_fd 9
    bridge_hello 2
    bridge_maxage 12

```Connection Information only has my NIC1 (192.168.1.65) listed.  I saw NIC2 there before and now its not.  **ifconfig** has this listed:

```
br0       Link encap:Ethernet  HWaddr 00:12:17:56:cf:1e  
          inet addr:192.168.1.66  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::3424:fcff:fe9b:ca38/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:604 errors:0 dropped:0 overruns:0 frame:0
          TX packets:234 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:34327 (34.3 KB)  TX bytes:23753 (23.7 KB)

eth0      Link encap:Ethernet  HWaddr 00:1c:c0:94:16:fd  
          inet addr:192.168.1.65  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21c:c0ff:fe94:16fd/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:601 errors:0 dropped:0 overruns:0 frame:0
          TX packets:63 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:41974 (41.9 KB)  TX bytes:9979 (9.9 KB)
          Interrupt:20 Memory:d2300000-d2320000 

eth1      Link encap:Ethernet  HWaddr 00:12:17:56:cf:1e  
          inet6 addr: fe80::212:17ff:fe56:cf1e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:659 errors:0 dropped:0 overruns:0 frame:0
          TX packets:192 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:51251 (51.2 KB)  TX bytes:17390 (17.3 KB)
          Interrupt:22 Base address:0xd000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:44 errors:0 dropped:0 overruns:0 frame:0
          TX packets:44 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3413 (3.4 KB)  TX bytes:3413 (3.4 KB)

virbr0    Link encap:Ethernet  HWaddr 2a:cf:23:95:e0:49  
          inet addr:192.168.122.1  Bcast:192.168.122.255  Mask:255.255.255.0
          inet6 addr: fe80::28cf:23ff:fe95:e049/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:50 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:8819 (8.8 KB)

```I rebooted to see how the NIC's are being configured and got this:

```
Nov 17 14:23:20 anointed kernel: [    6.072175] net eth0: ADMtek Comet rev 17 at Port 0xd000, 00:12:17:56:cf:1e, IRQ 22
Nov 17 14:23:20 anointed kernel: [    6.324926] e1000e 0000:00:19.0: eth1: (PCI Express:2.5GB/s:Width x1) 00:1c:c0:94:16:fd
Nov 17 14:23:20 anointed kernel: [    6.324928] e1000e 0000:00:19.0: eth1: Intel(R) PRO/1000 Network Connection
Nov 17 14:23:20 anointed kernel: [    6.324951] e1000e 0000:00:19.0: eth1: MAC: 7, PHY: 8, PBA No: ffffff-0ff
Nov 17 14:23:20 anointed kernel: [   10.022834] udev[411]: renamed network interface eth1 to eth1-eth0
Nov 17 14:23:20 anointed kernel: [   11.244084] udev[410]: renamed network interface eth0 to eth1
Nov 17 14:23:20 anointed kernel: [   11.272859] udev[411]: renamed network interface eth1-eth0 to eth0
Nov 17 14:23:20 anointed kernel: [   13.005976] device eth1 entered promiscuous mode
Nov 17 14:23:20 anointed kernel: [   13.007692] br0: port 1(eth1) entering learning state
Nov 17 14:23:20 anointed kernel: [   13.007694] br0: port 1(eth1) entering learning state
Nov 17 14:23:34 anointed kernel: [   28.043773] br0: port 1(eth1) entering forwarding state

```Why is eth1 (NIC2) being rename this way.  Could there be something wrong with my NIC2?

I also uplugged/plugged the NIC2 and I got this from my syslog:
```

Nov 17 15:04:28 anointed NetworkManager[1286]: <info> (eth1): carrier now OFF (device state 1)
Nov 17 15:04:28 anointed kernel: [ 2482.561696] br0: port 1(eth1) entering forwarding state
Nov 17 15:05:29 anointed NetworkManager[1286]: <info> (eth1): carrier now ON (device state 1)

```


.....my kernlog:
```

Nov 17 15:05:29 anointed kernel: [ 2542.721450] br0: port 1(eth1) entering learning state
Nov 17 15:05:29 anointed kernel: [ 2542.721454] br0: port 1(eth1) entering learning state
Nov 17 15:05:38 anointed kernel: [ 2551.740029] br0: port 1(eth1) entering forwarding state

```

---

