---
title: "Wireless connects, assigns IP, but nothing works (not even ping to router)"
date: 2013-05-09
forum: Networking &amp; Wireless
---

### Post by andyyy57 on 2013-05-09
I installed Ubuntu 13.04 on Asus M50V laptop. It connects to my wireless network, assigns IP (i can see it in ifconfig), but nothing else works. Only thing I can ping is my own IP (look bellow), but ping-ing router or any other IP gives no response.
Router is working properly as every other device can connect to it and access internet. When I had windows 7 on this laptop internet also worked so its not a hardware problem.

I have no idea what is wrong and would be very grateful if anyone can help me. Here are some outputs from command line:

ping in my own ip (192.168.0.101) works, but not pinging rounter:
```

andrej@andrej-M50Vn:~$ ping 192.168.0.101
PING 192.168.0.101 (192.168.0.101) 56(84) bytes of data.
64 bytes from 192.168.0.101: icmp_req=1 ttl=64 time=0.069 ms
64 bytes from 192.168.0.101: icmp_req=2 ttl=64 time=0.067 ms
^C
--- 192.168.0.101 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.067/0.068/0.069/0.001 ms
andrej@andrej-M50Vn:~$ ping 192.168.0.1
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.

^C
--- 192.168.0.1 ping statistics ---
448 packets transmitted, 0 received, 100% packet loss, time 447000ms


```

ifconfig:
```

andrej@andrej-M50Vn:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:23:54:19:7e:cd  
         UP BROADCAST MULTICAST  MTU:1500  Metric:1
         RX packets:0 errors:0 dropped:0 overruns:0 frame:0
         TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
         collisions:0 txqueuelen:1000 
         RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
         inet addr:127.0.0.1  Mask:255.0.0.0
         inet6 addr: ::1/128 Scope:Host
         UP LOOPBACK RUNNING  MTU:65536  Metric:1
         RX packets:360 errors:0 dropped:0 overruns:0 frame:0
         TX packets:360 errors:0 dropped:0 overruns:0 carrier:0
         collisions:0 txqueuelen:0 
         RX bytes:23404 (23.4 KB)  TX bytes:23404 (23.4 KB)

wlan0     Link encap:Ethernet  HWaddr 00:16:ea:9f:1b:da  
         inet addr:192.168.0.101  Bcast:192.168.0.255  Mask:255.255.255.0
         inet6 addr: fe80::216:eaff:fe9f:1bda/64 Scope:Link
         UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
         RX packets:1335 errors:0 dropped:0 overruns:0 frame:0
         TX packets:922 errors:0 dropped:0 overruns:0 carrier:0
         collisions:0 txqueuelen:1000 
         RX bytes:363255 (363.2 KB)  TX bytes:104362 (104.3 KB)

```


iwconfig
```

andrej@andrej-M50Vn:~$ iwconfig
wlan0     IEEE 802.11abgn  ESSID:"ag_network"  
         Mode:Managed  Frequency:2.412 GHz  Access Point: 90:F6:52:B4:0F:0E   
         Bit Rate=65 Mb/s   Tx-Power=15 dBm   
         Retry  long limit:7   RTS thr:off   Fragment thr:off
         Power Management:on
         Link Quality=14/70  Signal level=-96 dBm  
         Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
         Tx excessive retries:98  Invalid misc:41   Missed beacon:0

lo        no wireless extensions.

eth0      no wireless extensions.

```


```

andrej@andrej-M50Vn:~$ lspci | grep Network
03:00.0 Network controller: Intel Corporation WiFi Link 5100

```


```

andrej@andrej-M50Vn:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
192.168.0.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0

```



EDIT: some additional information:




```

andrej@andrej-M50Vn:~$ lsmod | grep wifi
iwlwifi               155077  1 iwldvm
cfg80211              436177  3 iwlwifi,mac80211,iwldvm

```


```

andrej@andrej-M50Vn:~$ dmesg | grep  iwlwifi
[    2.916193] iwlwifi 0000:03:00.0: irq 49 for MSI/MSI-X
[    2.918674] iwlwifi 0000:03:00.0: loaded firmware version 8.83.5.1 build 33692
[    2.986765] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEBUG disabled
[    2.986768] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEBUGFS enabled
[    2.986771] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEVICE_TRACING enabled
[    2.986773] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEVICE_TESTMODE enabled
[    2.986775] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_P2P disabled
[    2.986777] iwlwifi 0000:03:00.0: Detected Intel(R) WiFi Link 5100 AGN, REV=0x54
[    2.986835] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[    3.665769] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[    3.668823] iwlwifi 0000:03:00.0: Radio type=0x1-0x2-0x0
[    3.976789] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[    3.979702] iwlwifi 0000:03:00.0: Radio type=0x1-0x2-0x0

```


```

andrej@andrej-M50Vn:~$ sudo lshw -C network
  *-network               
       description: Wireless interface
       product: WiFi Link 5100
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 00
       serial: 00:16:ea:9f:1b:da
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=3.8.0-19-generic firmware=8.83.5.1 build 33692 ip=192.168.0.101 latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn
       resources: irq:49 memory:fdffe000-fdffffff
  *-network
       description: Ethernet interface
       product: RTL8111/8168 PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 02
       serial: 00:23:54:19:7e:cd
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:48 ioport:e800(size=256) memory:f8fff000-f8ffffff memory:f8fe0000-f8feffff memory:feaf0000-feafffff

```






```

andrej@andrej-M50Vn:~$ iwlist wlan0 scan
wlan0     Scan completed :
          Cell 01 - Address: 90:F6:52:B4:0F:0E
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=12/70  Signal level=-98 dBm  
                    Encryption key:on
                    ESSID:"ag_network"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000054c8541ee4
                    Extra: Last beacon: 6920ms ago
                    IE: Unknown: 000A61675F6E6574776F726B
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030101
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101860003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C334E101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 2D1A4E101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C34010D0A00000000000000000000000000000000000000
                    IE: Unknown: 3D16010D0A00000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010006004000
                    IE: Unknown: DD850050F204104A0001101044000102103B000103104700100000000000001000000090F652B40F0E1021000754502D4C494E4B1023000B544C2D5752313034334E4410240003312E3010420003312E301054000800060050F20400011011001B576972656C65737320526F7574657220544C2D5752313034334E44100800020086103C000101

```


```

andrej@andrej-M50Vn:~$ lsb_release -d
Description:    Ubuntu 13.04

```


```

andrej@andrej-M50Vn:~$ uname -mr
3.8.0-19-generic i686

```

---

### Post by TheFu on 2013-05-09
Network troubleshooting steps: [http://blog.jdpfu.com/2013/03/01/linux-troubleshooting-101-networking](http://blog.jdpfu.com/2013/03/01/linux-troubleshooting-101-networking)

How far do you get?

---

### Post by andyyy57 on 2013-05-09
It already fails at first step (pinging router) as mentioned in my post. I posted come outputs from different commands too but I can't really get anything out of them as i'm not a network expert.

---

### Post by papibe on 2013-05-10
Hi  andyyy57.

Could you post the results of these commands?
```
cat /etc/network/interfaces

nm-tool

route -n

nslookup ubuntu.com

dig ubuntuforums.org
```
Regards.

---

### Post by andyyy57 on 2013-05-10
hi papibe, here is the output of those commands:

```

andrej@andrej-M50Vn:~$ cat /etc/network/interfaces 
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

```

```

andrej@andrej-M50Vn:~$ nm-tool 


NetworkManager Tool


State: connected (global)


- Device: wlan0  [ag_network] --------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlwifi
  State:             connected
  Default:           yes
  HW Address:        00:16:EA:9F:1B:DA


  Capabilities:
    Speed:           65 Mb/s


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points (* = current AP)
    *ag_network:     Infra, 90:F6:52:B4:0F:0E, Freq 2412 MHz, Rate 54 Mb/s, Strength 77 WPA2
    Innbox-internet-6fe6ef: Infra, 00:C0:02:6F:E6:EF, Freq 2437 MHz, Rate 54 Mb/s, Strength 74 WPA2
    WiFi Net:        Infra, 64:70:02:F4:DA:04, Freq 2457 MHz, Rate 54 Mb/s, Strength 24 WPA


  IPv4 Settings:
    Address:         192.168.0.101
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1


    DNS:             192.168.0.1




- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        00:23:54:19:7E:CD


  Capabilities:
    Carrier Detect:  yes


  Wired Properties
    Carrier:         off

```

```

andrej@andrej-M50Vn:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
192.168.0.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0

```

```

andrej@andrej-M50Vn:~$ nslookup ubuntu.com
;; connection timed out; no servers could be reached

```
   
```
   
andrej@andrej-M50Vn:~$ dig ubuntuforums.org


; <<>> DiG 9.9.2-P1 <<>> ubuntuforums.org
;; global options: +cmd
;; connection timed out; no servers could be reached
andrej@andrej-M50Vn:~$ 

```

---

### Post by prodigy_ on 2013-05-10
Routing table looks OK.

Sanity check:
```
sudo iptables -L
mtr -rnc 1 8.8.8.8
sudo dhclient -r wlan0
sudo dhclient -v wlan0

```

If you're not using DHCP then, instead of running the last two commands, you need to double-check that your router LAN address is really 192.168.0.1. Often it's 192.168.**1**.1.

---

### Post by mee1979 on 2013-05-10
andrej@andrej-M50Vn:~$ uname -mr3.8.0-19-generic i686

---

### Post by andyyy57 on 2013-05-10
hi prodigy


my routner IP really is 192.168.0.1 (with zero). I can ping that IP from my other machine. 

here is the output:

```

andrej@andrej-M50Vn:~$ sudo iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         


Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         


Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
andrej@andrej-M50Vn:~$ 
andrej@andrej-M50Vn:~$ mtr -rnc 1 8.8.8.8
HOST: andrej-M50Vn                Loss%   Snt   Last   Avg  Best  Wrst StDev
andrej@andrej-M50Vn:~$ sudo dhclient -r wlan0
andrej@andrej-M50Vn:~$ sudo dhclient -r wland0
andrej@andrej-M50Vn:~$ 

```

---

### Post by papibe on 2013-05-10
:confused: Puzzling...

Are you able to ping the other machines in your LAN besides your router?

Could you post the result of these ones?
```
mtr -rnc 1 192.168.0.1

sudo ifdown wlan0

sudo ifup wlan0

dmesg | grep -i wlan 
```
Regards.

---

### Post by andyyy57 on 2013-05-10
Hmm, thats interesting, the ifdown command says wlan0 is not configured even though ubuntu says its connected.


```

andrej@andrej-M50Vn:~$ mtr -rnc 1 192.168.0.1
HOST: andrej-M50Vn                Loss%   Snt   Last   Avg  Best  Wrst StDev
andrej@andrej-M50Vn:~$ sudo ifdown wlan0
ifdown: interface wlan0 not configured
andrej@andrej-M50Vn:~$ sudo ifup wlan0
Ignoring unknown interface wlan0=wlan0.
andrej@andrej-M50Vn:~$ dmesg | grep -i wlan
[    5.005947] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[    5.010686] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   11.405384] wlan0: authenticate with 90:f6:52:b4:0f:0e
[   11.407302] wlan0: send auth to 90:f6:52:b4:0f:0e (try 1/3)
[   11.409575] wlan0: authenticated
[   11.412026] wlan0: associate with 90:f6:52:b4:0f:0e (try 1/3)
[   11.415810] wlan0: RX AssocResp from 90:f6:52:b4:0f:0e (capab=0x431 status=0 aid=3)
[   11.429490] wlan0: associated
[   11.429511] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
andrej@andrej-M50Vn:~$ 

```

---

### Post by andyyy57 on 2013-05-10
Oh, and I'm actually able to ping my other machine on network (192.168.0.100) but not router.

---

### Post by prodigy_ on 2013-05-10
Well, check firewall settings on the router. If they're OK, you should file a [bug report](https://bugs.launchpad.net/ubuntu/+filebug).

---

### Post by papibe on 2013-05-10
> **andyyy57 said:**
> Oh, and I'm actually able to ping my other machine on network (192.168.0.100) but not router.
That's a little bit of a relief.

As prodigy_ mentioned it, check your router for settings that may restrict that machines access. For instance, DHCP reservations, MAC filtering, Parental control, Access Blocking Policy, etc.

Regards.

---

### Post by andyyy57 on 2013-05-10
I did something different now, I checked if there is any new firmware for my router and there were a couple! I installed the latest on my router and now everything works perfectly!

Sorry for wasting your time guys :(

---

### Post by papibe on 2013-05-10
:D Glad you sorted it out.

---

### Post by TheFu on 2013-05-10
> **andyyy57 said:**
> I did something different now, I checked if there is any new firmware for my router and there were a couple! I installed the latest on my router and now everything works perfectly!

Sorry for wasting your time guys :(

Router firmwares need to be patched every 6 months or so.  I find it is easier to keep up with releases for the replacement firmwares from dd-wrt, openwrt, tomato ... assuming you don't deploy a business-class system like pfSense with much more powerful controls.

If it has software, it needs to be patched.

---

