---
title: "networkmanager's dsl connection can't have static LAN ip?"
date: 2010-09-02
forum: Networking &amp; Wireless
---

### Post by DavidYun on 2010-09-02
Sorry for reopen a new Thread, but I think it might be better if I change the title of my problem.
here's the early thread/problem I post :
[http://ubuntuforums.org/showthread.php?t=1565472&highlight=dsl+static+ip](http://ubuntuforums.org/showthread.php?t=1565472&highlight=dsl+static+ip)

my steps and result:
1.Install Ubuntu 10.04
2.open NM-applet and edit connections
  LAN
[IMG]http://dl.dropbox.com/u/8186287/LAN-Wired.png[/IMG][IMG]http://dl.dropbox.com/u/8186287/LAN-IPv4%20Settings.png[/IMG]
  ADSL
[IMG]http://dl.dropbox.com/u/8186287/ADSL-Wired.png[/IMG][IMG]http://dl.dropbox.com/u/8186287/ADSL-IPv4%20Settings.png[/IMG]
3.check Network Manager[version=0.8] config
```
sudo vi /etc/NetworkManager/nm-system-settings.conf
``````

[main]
plugins=ifupdown,keyfile

no-auto-default=00:0f:ea:8c:a3:3d,

[ifupdown]
managed=false

``````
sudo vi /etc/NetworkManager/system-connetions/LAN
``````

[connection]
id=LAN
uuid=c03ee42e-8251-442d-b813-ecf42a4e9226
type=802-3-ethernet
autoconnect=false
timestamp=0

[ipv4]
method=manual
addresses1=192.168.1.19;24;192.168.1.1;
ignore-auto-routes=false
ignore-auto-dns=false
dhcp-send-hostname=false
never-default=false

[802-3-ethernet]
speed=0
duplex=full
auto-negotiate=true
mac-address=0:f:ea:8c:a3:3d
mtu=0

[ipv6]
method=ignore
ignore-auto-routes=false
ignore-auto-dns=false
never-default=false

``````
sudo vi /etc/NetworkManager/system-connetions/ADSL
``````

[connection]
id=ADSL
uuid=af897894-84f1-44da-9d6b-6c358f62b8a7
type=pppoe
autoconnect=true
timestamp=0

[ppp]
noauth=true
refuse-eap=false
refuse-pap=false
refuse-chap=false
refuse-mschap=false
refuse-mschapv2=false
nobsdcomp=false
nodeflate=true
no-vj-comp=false
require-mppe=false
require-mppe-128=false
mppe-stateful=false
crtscts=false
baud=0

mru=1492
mtu=1492
lcp-echo-failure=5
lcp-echo-interval=30

[ipv4]
method=manual
addresses1=192.168.1.19;24;192.168.1.1;
addresses2=192.168.1.20;24;0.0.0.0;
ignore-auto-routes=false
ignore-auto-dns=false
dhcp-send-hostname=false
never-default=false

[pppoe]
service=HInetVDSL
username=7xxxxxxx@xxxxxxxx
password=xxxxxxxxxx

[802-3-ethernet]
speed=0
duplex=full
auto-negotiate=true
mac-address=0:f:ea:8c:a3:3d
mtu=0

```4.connect ADSL and check ifconfig
```

eth0      Link encap:Ethernet  HWaddr 00:0f:ea:8c:a3:3d  
          inet6 addr: fe80::20f:eaff:fe8c:a33d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:31483 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20193 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:37771800 (37.7 MB)  TX bytes:2772030 (2.7 MB)
          Interrupt:21 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:92 errors:0 dropped:0 overruns:0 frame:0
          TX packets:92 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:6896 (6.8 KB)  TX bytes:6896 (6.8 KB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:114.42.89.144  P-t-P:168.95.98.254  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:26050 errors:0 dropped:0 overruns:0 frame:0
          TX packets:15710 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:32156005 (32.1 MB)  TX bytes:1821223 (1.8 MB)


```5.connect LAN and check ifconfig
```

eth0      Link encap:Ethernet  HWaddr 00:0f:ea:8c:a3:3d  
          inet addr:192.168.1.19  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:eaff:fe8c:a33d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:31580 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20290 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:37839176 (37.8 MB)  TX bytes:2794024 (2.7 MB)
          Interrupt:21 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:108 errors:0 dropped:0 overruns:0 frame:0
          TX packets:108 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:8080 (8.0 KB)  TX bytes:8080 (8.0 KB)

```[SIZE=3][COLOR=Blue]The Whole Problem is that(maybe a bug?)
why doesn't the setting in ADSL address1=192.168.1.19 work?
I need the static LAN IP when I connect the internet!!![/COLOR][/SIZE]

---

