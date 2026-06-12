---
title: "How to configure wireless access point? ath9k + hostapd"
date: 2013-02-04
forum: Networking &amp; Wireless
---

### Post by lle on 2013-02-04
The Plan:

[IMG]http://traceur.ressu.fi/other/plan.png[/IMG]

I'm trying to set up wireless access point on my Ubuntu Server. I'd like to use hostapd to secure the accesspoint with WPA-PSK. I have compiled the ath9k driver from the newest kernel I'm running.

My wireless adapter is D-Link DWA-556.

Point being, I'm finding multiple informative tutorials and help pages, but so far I have failed in setting up the access point.

service hostapd won't start, it just says [failed].

**iwscan** does find all the wireless networks in my apartment, so the card is clearly working. 

I actually managed to get the access point up once a few weeks ago, but I still have no idea how :S. Hostapd failed back then also. So I shut it down as unsecured and upgraded to newest kernel. 


I'll be much appreciated if someone more skilled could help me in setting up the access point! I'm sorry if there's already a thread about this, I ran the search but couldn't find a suitable one for my problem.

Hell lot of other information:

```
# ifup wlan0
Ignoring unknown interface wlan0=wlan0.
``````
# ifup ath0
ath0: ERROR while getting interface flags: No such device
Error for wireless request "Set Mode" (8B06) :
    SET failed on device ath0 ; No such device.
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device ath0 ; No such device.
ssh stop/waiting
ssh start/running, process 31727

``````
# lsb_release -d
Description:    Ubuntu 12.04.1 LTS

``````
# uname -mr
3.8.0-rc5-mikonsynttarit x86_64

``````
# lspci | grep Atheros
02:00.0 Network controller: Atheros Communications Inc. AR5418 Wireless Network Adapter [AR5008E 802.11(a)bgn] (PCI-Express) (rev 01)
``````
# ifconfig
br0       Link encap:Ethernet  HWaddr cc:5d:4e:6f:2b:0a
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

eth0      Link encap:Ethernet  HWaddr cc:5d:4e:6f:2b:0a
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:5403375 errors:0 dropped:91 overruns:0 frame:0
          TX packets:1127084 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:7719813803 (7.7 GB)  TX bytes:873131371 (873.1 MB)

eth1      Link encap:Ethernet  HWaddr 00:50:8d:81:97:14
          inet addr:192.168.0.110  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::250:8dff:fe81:9714/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:114473 errors:0 dropped:0 overruns:0 frame:0
          TX packets:112567 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:16169665 (16.1 MB)  TX bytes:469727639 (469.7 MB)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:33916 errors:0 dropped:0 overruns:0 frame:0
          TX packets:33916 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:6212811 (6.2 MB)  TX bytes:6212811 (6.2 MB)

wlan0     Link encap:Ethernet  HWaddr 14:d6:4d:10:ec:4f
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

``````
# cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

auto eth1
iface eth1 inet dhcp

auto ath0
iface ath0 inet manual
      wireless-mode master
      wireless-essid "ressu"

auto br0
iface br0 inet static
      address 192.168.1.1
      netmask 255.255.255.0
      network 192.168.1.0
      broadcast 192.168.1.255
      bridge-ports eth0 ath0

``````
# iwconfig wlan0
wlan0     IEEE 802.11bgn  ESSID:off/any
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
``````
# lsmod | grep ath
ath9k                 110116  0
mac80211              597768  1 ath9k
ath9k_common           14053  1 ath9k
ath9k_hw              392858  2 ath9k,ath9k_common
ath                    23827  3 ath9k,ath9k_common,ath9k_hw
cfg80211              520338  3 ath9k,mac80211,ath

``````
# cat /etc/hostapd/hostapd.conf
driver=nl80211
interface=wlan0
bridge=br0
hw_mode=g
ssid=ressu

#802.11n asetukset
wme_enabled=1
ieee80211n=1
ht_capab=[HT40+][SHORT-GI-40][DSSS_CCK-40]

#wpa suojaus
wpa=3
wpa_key_mgmt=WPA-PSK
wpa_pairwise=TKIP
rsn_pairwise=CCMP
wpa_passphrase=ikeankukkaruukku

```

---

### Post by lle on 2013-02-06
Still nothing... I forgot to add that before, as I got AP to work momentarily, I used madwifi drivers, not ath9k. But hostapd doesnt support madwifi, so...

---

