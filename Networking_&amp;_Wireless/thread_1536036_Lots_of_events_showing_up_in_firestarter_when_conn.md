---
title: "Lots of events showing up in firestarter when connected to VPN"
date: 2010-07-21
forum: Networking &amp; Wireless
---

### Post by hswae on 2010-07-21
Hi,

I managed to get Firestarter working with a VPN in Ubuntu 10.04 using the method found here:
[http://ubuntuforums.org/archive/index.php/t-266708.html](http://ubuntuforums.org/archive/index.php/t-266708.html)

_But I've noticed I'm seeing lots of IP addresses from pretty much the same ports showing up in the Firestarter Events menu._
I was wondering if maybe there's a way to stop them from showing or if I've done something wrong along the way.

I'm also not running anything on the PC that could be using those ports, this is a fresh install of Ubuntu done a few minutes ago. It looks like those IPs are of other people using the VPN...that's what I'm guessing.

This is my output from ifconfig (I've removed the IP from ppp0):

```
[I]eth0      Link encap:Ethernet  HWaddr 00:1e:8c:1c:99:67  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:732 errors:0 dropped:0 overruns:0 frame:0
          TX packets:732 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:46216 (46.2 KB)  TX bytes:46216 (46.2 KB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:*.*.*.*  P-t-P:*.*.*.*  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1400  Metric:1
          RX packets:16281 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11543 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:19361845 (19.3 MB)  TX bytes:1066628 (1.0 MB)

wlan0     Link encap:Ethernet  HWaddr 00:22:6b:a6:ad:c9  
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::222:6bff:fea6:adc9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:26573 errors:0 dropped:0 overruns:0 frame:0
          TX packets:26998 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:25695253 (25.6 MB)  TX bytes:3469221 (3.4 MB)[/I]
```



This is what the Events look like in Firestarter:

[IMG]http://i25.tinypic.com/j7b1pl.png[/IMG]



This is the method I used (maybe it'll help some other people out too):


I used this exactly, and added it to /etc/firestarter/user-pre:

```
[I]# Forward PPTP VPN client traffic
$IPT -A FORWARD -i $IF -o $INIF -p tcp --dport 1723 -m state --state NEW,ESTABLISHED,RELATED -j ACCEPT
$IPT -A FORWARD -i $IF -o $INIF -p 47 -m state --state NEW,ESTABLISHED,RELATED -j ACCEPT
$IPT -A FORWARD -i $INIF -o $IF -p 47 -m state --state NEW,ESTABLISHED,RELATED -j ACCEPT[/I]
```



Then I added this to the top of the same file (I changed the eth1 in the original thread to wlan0 for the second line, and changed the IP too for the second line):

```
[I]# Enable wlan0 with vpn -- edit the second line appropriately for your vpn
$IPT -A INPUT -i wlan0 -p all -s 0.0.0.0/0 -j ACCEPT
$IPT -A OUTPUT -p all -d 142.103.200.0/0 -j ACCEPT
$IPT -A FORWARD -i wlan0 -p all -s 0.0.0.0/0 -d 0.0.0.0/0 -j ACCEPT[/I]
```



Then I installed ip_conntrack_pptp with:
```
*sudo modprobe ip_conntrack_pptp*
```



Then I rebooted Firestarter with:
```
*sudo /etc/init.d/firestarter restart*
```


After that it wouldn't work until I went into Firestarter and added ppp0 as the Internet Connected Network Device, and wlan0 as the Local Network Connected Device.

I've tried enabling and disabling Internet Connection Sharing below that, but it doesn't make a difference.

The IP addresses keep showing up...


If you need to see any other output please let me know.

Thanks for any help!

---

