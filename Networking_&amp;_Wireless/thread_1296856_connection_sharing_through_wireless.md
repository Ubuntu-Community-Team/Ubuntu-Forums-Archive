---
title: "connection sharing through wireless"
date: 2009-10-21
forum: Networking &amp; Wireless
---

### Post by Bslaccko on 2009-10-21
Hi everyone,
I would like to share the internet connection between two laptops through their wireless cards.
One laptop is a Lenovo ThinkPad R61 running Ubuntu 8.10 (kernel 2.6.27-14-generic x86_64) connected to the internet through a modem/router on the ethernet port (eth0). For the connection I configured pppoe with my ISP account informations, so I connect/disconnect to/from the network with pon/poff. Whenever I connect to the network pppoe creates a point-to-point interface ppp0. I use also Firestarter and wicd. The ethernet card is an Intel 82566MC Gigabit while the wireless card is an Intel PRO/Wireless 4965AGN. The wireless card use the following kernel modules: iwlagn, iwlcore, mac80211 and cfg80211.
The second laptop is a HP Compaq nc6220 running WinXP Pro. The wireless card is an Intel PRO/Wireless 2915AG.

I would like to connect the WinXP laptop to the Ubuntu laptop through their wireless cards and share the network connection on the latter.

I tried to follow this guide but with no success:
[https://help.ubuntu.com/community/WifiDocs/ShareEthernetConnectionThroughWireless](https://help.ubuntu.com/community/WifiDocs/ShareEthernetConnectionThroughWireless)

I summarize here the steps I've done hoping that someone can help me.

1. I configured the wireless card under Ubuntu editing the file /etc/network/interfaces

```
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp

#
iface ppp0 inet ppp
provider alice

[COLOR="Blue"]# Wireless
auto wlan0
iface wlan0 inet static
  address 192.168.0.2
  gateway 192.168.0.1
  netmask 255.255.255.0
  wireless-essid pippo
  wireless-mode Ad-Hoc
  wireless-channel 6[/COLOR]

```

2. Restarting the network: sudo /etc/init.d/networking restart

**ifconfig** output:
```
[pippo@ubuntu: ~]$ sudo ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:1e:37:15:7b:c7  
          inet address:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          address inet6: fe80::21e:37ff:fe15:7bc7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1660790 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2458454 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          Byte RX:334126159 (334.1 MB)  Byte TX:2667784151 (2.6 GB)
          Memory:fe200000-fe220000 

lo        Link encap:Loopback local  
          inet adress:127.0.0.1  Mask:255.0.0.0
          address inet6: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4697 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4697 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          Byte RX:196812 (196.8 KB)  Byte TX:196812 (196.8 KB)

ppp0      Link encap:Point-to-Point Protocol  
          inet address:xxx.xxx.xxx.xxx  P-t-P:192.168.100.1  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:66607 errors:0 dropped:0 overruns:0 frame:0
          TX packets:100761 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          Byte RX:6719604 (6.7 MB)  Byte TX:115251958 (115.2 MB)

wlan0     Link encap:Ethernet  HWaddr 00:1d:e0:0f:f3:8f  
          inet address:192.168.0.2  Bcast:192.168.0.255  Mask:255.255.255.0
          address inet6: fe80::21d:e0ff:fe0f:f38f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:476 errors:0 dropped:0 overruns:0 frame:0
          TX packets:593 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          Byte RX:33601 (33.6 KB)  Byte TX:124904 (124.9 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-1D-E0-0F-F3-8F-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          Byte RX:0 (0.0 B)  Byte TX:0 (0.0 B)

```

**iwconfig** output:
```
[pippo@ubuntu: ~]$ sudo iwconfig 
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:"pippo"  
          Mode:Ad-Hoc  Frequency:2.437 GHz  Cell: CA:D8:D8:59:A8:97   
          Tx-Power=15 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

```

**route** output:
```
[pippo@ubuntu: ~]$ sudo route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.100.1   *               255.255.255.255 UH    0      0        0 ppp0
192.168.1.0     *               255.255.255.0   U     0      0        0 eth0
192.168.0.0     *               255.255.255.0   U     0      0        0 wlan0
link-local      *               255.255.0.0     U     1000   0        0 eth0
default         *               0.0.0.0         U     0      0        0 ppp0
default         192.168.0.1     0.0.0.0         UG    100    0        0 wlan0
default         192.168.1.1     0.0.0.0         UG    100    0        0 eth0

```

3. I configured firestarter:

Menù: Edit->Preferences->Firewall->Network Settings

Internet connected network device: **ppp0**
Local network connected device: **wlan0**
Enable Internet connection sharing: **enabled**
Click on Accept. All seems OK.

4. I configured the wireless network on the WinXP laptop:

Directory Network Connections, right click on Wireless Connection -> Properties
Tab General->Internet Protocol (TCP/IP)->Properties
Use the following IP address:
 Address IP: 192.168.0.10
 Subnet Mask: 255.255.255.0
 Default Gateway: 192.168.0.1
Use the following DNS server:
 I configured the primary and secondary DNS with the ISP provided IPs, that are the same on the /etc/ppp/resolv.conf un the Ubuntu laptop.
Click OK.

5. Double click on the Wireless Connection icon, click on Refresh.
Select the "pippo" network, click on Connect.
It seems all is OK. The connection is established with the parameter I've configured previously, but I can't access the network.

I tried to ping the laptops from one another in both directions but with no success. I noticed that when I ping the wlan0 address (192.168.0.2) from WinXP, ping says "Connection Time-out" but I can see the ping in the Firestarter log (from IP 192.168.0.10).

Any idea?

Thanks in advance.

---

### Post by Bslaccko on 2009-11-02
I have not found a solution yet.
The fact that Firestarter shows the ping attempt from the WinXP suggest me that the connection is working but for some reason what came from the WinXP is not forwarded through.
Could this be a problem with the firewall rules?
From my little understanding of networking the configuration reported in the guide should drive the firewall to forward what came from the wireless connection (wlan0) through the internet (ppp0), right?

If someone could help me I would be very grateful.

---

