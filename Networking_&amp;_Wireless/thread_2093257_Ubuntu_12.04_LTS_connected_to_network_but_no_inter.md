---
title: "Ubuntu 12.04 LTS connected to network but no internet on HP Mini"
date: 2012-12-10
forum: Networking &amp; Wireless
---

### Post by ishmiduti on 2012-12-10
Yet another DHCP problem. I'm on TimeWarner and we just got a router/modem combo and my wife's computer won't connect to the internet(who's been there before?) 

```
alison@alisons-mini:~$ iwconfig
lo        no wireless extensions.

eth1      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"CELLIS"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:1D:D3:71:37:C0   
          Bit Rate=65 Mb/s   Tx-Power=27 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=53/70  Signal level=-57 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:590   Missed beacon:0


```

```
alison@alisons-mini:~$ ifconfig
eth1      Link encap:Ethernet  HWaddr a0:b3:cc:77:6c:70  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:5644 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2176 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4946700 (4.9 MB)  TX bytes:213210 (213.2 KB)
          Interrupt:43 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2835 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2835 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:221506 (221.5 KB)  TX bytes:221506 (221.5 KB)

wlan0     Link encap:Ethernet  HWaddr e0:06:e6:26:4e:ae  
          inet addr:192.168.0.4  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::e206:e6ff:fe26:4eae/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5127 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1061 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:468786 (468.7 KB)  TX bytes:83992 (83.9 KB)


```

```
alison@alisons-mini:~$ nm-tool

NetworkManager Tool

State: connected (global)

- Device: wlan0  [CELLIS] ------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rt2800pci
  State:             connected
  Default:           yes
  HW Address:        E0:06:E6:26:4E:AE

  Capabilities:
    Speed:           65 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    ATCUSER-XPS13-98100: Infra, 00:DB:DF:16:08:9C, Freq 2437 MHz, Rate 54 Mb/s, Strength 42 WPA2
    my wireless:     Infra, 00:1A:70:57:8C:58, Freq 2437 MHz, Rate 54 Mb/s, Strength 25 WEP
    my wireless_EXT: Infra, 20:4E:7F:18:4F:70, Freq 2437 MHz, Rate 54 Mb/s, Strength 25 WEP
    my wireless_xt:  Infra, 08:86:3B:CB:F9:F2, Freq 2437 MHz, Rate 54 Mb/s, Strength 29 WEP
    Janet:           Infra, 00:26:F3:31:C8:C6, Freq 2437 MHz, Rate 54 Mb/s, Strength 25 WPA2
    *CELLIS:         Infra, 00:1D:D3:71:37:C0, Freq 2412 MHz, Rate 54 Mb/s, Strength 61 WPA WPA2

  IPv4 Settings:
    Address:         192.168.0.4
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             8.8.8.8


- Device: eth1 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        A0:B3:CC:77:6C:70

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off



```

```
alison@alisons-mini:~$ sudo lshw -C network
[sudo] password for alison: 
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth1
       version: 05
       serial: a0:b3:cc:77:6c:70
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl_nic/rtl8105e-1.fw latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:43 ioport:3000(size=256) memory:80004000-80004fff memory:80000000-80003fff
  *-network
       description: Wireless interface
       product: RT5390 Wireless 802.11n 1T/1R PCIe
       vendor: Ralink corp.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 00
       serial: e0:06:e6:26:4e:ae
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2800pci driverversion=3.2.0-34-generic-pae firmware=0.34 ip=192.168.0.4 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:82000000-8200ffff

```

```
alison@alisons-mini:~$ ping 192.168.0.1 -c3
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.
64 bytes from 192.168.0.1: icmp_req=1 ttl=64 time=0.805 ms
64 bytes from 192.168.0.1: icmp_req=2 ttl=64 time=0.823 ms
64 bytes from 192.168.0.1: icmp_req=3 ttl=64 time=0.770 ms

--- 192.168.0.1 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2000ms
rtt min/avg/max/mdev = 0.770/0.799/0.823/0.031 ms
alison@alisons-mini:~$ ping 8.8.8.8 -c3
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
64 bytes from 8.8.8.8: icmp_req=1 ttl=51 time=29.2 ms
64 bytes from 8.8.8.8: icmp_req=2 ttl=51 time=28.9 ms
64 bytes from 8.8.8.8: icmp_req=3 ttl=51 time=30.0 ms

--- 8.8.8.8 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2002ms
rtt min/avg/max/mdev = 28.940/29.427/30.078/0.517 ms
alison@alisons-mini:~$ 

```

I don't know what to try next. I've tried a lot of the other various forum posts. It seems that it's not even actually connected to the router.

Thanks, C

---

### Post by Bucky Ball on 2012-12-10
Yes, the access point/router is called CELLIS? If not you are connected to the wrong network. What is your network called? All your outputs look fine and the card is certainly up and running so all good there.

Do you need to add DNS addresses in network manager? Is it a static IP or being served via DHCP by the router? Is the router online? Have you restarted the machine since install? Done an update?

---

### Post by ishmiduti on 2012-12-10
> **Bucky Ball said:**
> Yes, the access point/router is called CELLIS? If not you are connected to the wrong network. What is your network called? All your outputs look fine and the card is certainly up and running so all good there.

Do you need to add DNS addresses in network manager? Is it a static IP or being served via DHCP by the router? Is the router online? Have you restarted the machine since install? Done an update?

Yes the access point is CELLIS and I'm connected to it. It should be served by DHCP, no problems on my Windows Laptop or my Android Tablet. The router is online, I can use the ethernet for internet on the computer. I've restarted it several times since install, and updated/upgraded last night. 

I'm baffled.

---

### Post by Bucky Ball on 2012-12-10
If you right click on the Network icon and edit wireless connection (you should see CELLIS there), is it set to 'Method: automatic DHCP' or manual? It should be set to auto ...

---

### Post by ishmiduti on 2012-12-11
> **Bucky Ball said:**
> If you right click on the Network icon and edit wireless connection (you should see CELLIS there), is it set to 'Method: automatic DHCP' or manual? It should be set to auto ...

I've already tried doing automatic dhcp, manual and automatic dhcp addresses only.

---

