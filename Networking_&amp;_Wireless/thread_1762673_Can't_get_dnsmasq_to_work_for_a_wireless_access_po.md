---
title: "Can't get dnsmasq to work for a wireless access point."
date: 2011-05-19
forum: Networking &amp; Wireless
---

### Post by Elline on 2011-05-19
Hello everybody.
I have a two computers, laptop and netbook. Laptop is plugged to a network cable and I want to share that connection with netbook through a wi-fi access point mode.

I has installed a hostapd following these [http://wireless.kernel.org/en/users/Documentation/hostapd]("http://wireless.kernel.org/en/users/Documentation/hostapd") instructions and it seems to work.

There is configuration file for hostapd:
```
#change wlan0 to your wireless device
interface=wlan0
driver=nl80211
ssid=ubunet
hw_mode=g
channel=1
#wpa
#macaddr_acl=0
#auth_algs=1
#ignore_broadcast_ssid=0
#wpa=3
#wpa_passphrase=YourPassPhrase
#wpa_key_mgmt=WPA-PSK
#wpa_pairwise=TKIP
#rsn_pairwise=CCMP
``` I had commented all about WPA encryption just to test first.

When I issuing "sudo hostapd /etc/hostapd/hostapd.conf", I get the following:
```
Configuration file: /etc/hostapd/hostapd.conf
Using interface wlan0 with hwaddr 00:15:af:86:9a:a9 and ssid 'ubunet'
Malformed netlink message: len=992 left=256 plen=976
256 extra bytes in the end of netlink message

``` And then I'm able to see this network from the netbook and connect to it. When it's connecting I see the following on the laptop:
```
wlan0: STA 00:15:af:b5:91:f0 IEEE 802.11: authenticated
wlan0: STA 00:15:af:b5:91:f0 IEEE 802.11: associated (aid 1)
wlan0: STA 00:15:af:b5:91:f0 RADIUS: starting accounting session 4DD53FAB-00000000

```
That's for connection. Here is a "ifconfig" and "iwconfig" for laptop:

ifconfig:
```
eth0      Link encap:Ethernet  HWaddr 00:1d:92:51:21:e6  
          inet addr:10.34.199.228  Bcast:10.34.199.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:46309 errors:0 dropped:0 overruns:0 frame:0
          TX packets:55546 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4927835 (4.9 MB)  TX bytes:45074247 (45.0 MB)
          Interrupt:43 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1809 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1809 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:164889 (164.8 KB)  TX bytes:164889 (164.8 KB)

mon.wlan0 Link encap:UNSPEC  HWaddr 00-15-AF-86-9A-A9-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:97 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6754 (6.7 KB)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:15:af:86:9a:a9  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:3 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:126 (126.0 B)  TX bytes:0 (0.0 B)
```

iwconfig:
```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  Mode:Master  Frequency:2.412 GHz  Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
vboxnet0  no wireless extensions.

mon.wlan0  IEEE 802.11bg  Mode:Monitor  Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

```

Next I thought I need to setup a DHCP server on a laptop to forward a connection, but fell in struggle with it. I have followed these [http://ubuntuforums.org/showthread.php?t=1663788&highlight=access+point+dhcp]("http://ubuntuforums.org/showthread.php?t=1663788&highlight=access+point+dhcp") instructions and used a ap_ctl script with no luck.

I'm tired and near to give up already so get to the forum for help. Maybe some HOW-TO or a brief explanation on how to achieve dsmasq to work applied to my setup?
And I'm sorry for my English cause it may be freaky.

---

### Post by Ratnesh_Agarwal on 2011-10-17
Hi 
Its look like the same problem I am facing... My laptop is wirelessl interface... now furthur I want to get my mobile connected wirelessly to that laptop.. but no Success...
 
If you get any success please shrare the solution...
 
Thanks in advance

---

