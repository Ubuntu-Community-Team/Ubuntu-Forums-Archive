---
title: "Wireless Continually Disconnects !"
date: 2010-06-11
forum: Networking &amp; Wireless
---

### Post by Ryan. on 2010-06-11
Hello people...

I have found many similar posts, but have not been able to find a solution after working ALL DAY trying to solve my problem(s).  I am very frustrated and sad that I might have to switch back to Windows 7 if I cannot fix this soon, since I require my laptop have a stable internet connection for school.

Anyway, the majority of my problems began after I upgraded to 10.04.   However, this was also around the time I switched from Network Manager to Wicd, so that may also contribute to the problem.

One odd thing worth mentioning is that, even though I always had issues with the wireless after the upgrade, the somewhat-functional wireless seemed to have just instantly died yesterday for no apparent reason.  (The only thing I can think of doing is the usual system updates.)

Anyway, here are the issues:

_1) [HOME] SECURED NETWORK_

When I am at home, I cannot connect to the wireless networks anymore.  Period.

Wicd used to say "Bad password" when I clicked "Connect" to one of the networks even though the password was correct.  Thus, I would have to make sure the network was set to "Auto connect" so that it would eventually connect itself (it usually wouldn't say "Bad password" if it attempted on its own.)  However, now it cannot even connect itself.

What happened before it went completely downhill is that it would self-connect to the network for a few seconds, disconnect, reconnect, disconnect, reconnect, etc. for about 15 minutes until it finally became a somewhat solid connection.  At first I thought it was something to do with signal interference, but now that I am having the problems described below, I have doubts.

_2) [SCHOOL] UNSECURED NETWORK_

My laptop used to connect to the unsecured (school) wireless perfectly, without any disconnects, even after the 10.04 upgrade.  Now, the connection is very flaky and won't stay connected for more than 2 minutes at a time.  (I check this by streaming YouTube videos and running tests.)

However, the odd thing is that, even after it stops sending/receiving data in the browser, Wicd still shows me connected to the network.  When pinging, it says "Network is unreachable."  Usually it fails to reconnect on its own (since it thinks it is connected), so I have to go to Wisc --> Disconnect all --> Connect again and again.

Similar to the "Home" scenario, the connection seems to finally become solid after surfing for a while.  However, as mentioned, unlike the "Home" environment, it always seems to think it is connected even when it's unable to send/receive any packages.

I don't know what's wrong.

[CENTER] - - - - -
[/CENTER]
  [LEFT] Now to get somewhat technical,[/LEFT]
 
I already tried setting the MTU to 1500.  I thought this fixed it, but when I restarted I am having the same problems.

Here is some output:

[SIZE=2]***-- ifconfig --***[/SIZE]

```


**ryan@gaffney:~$ ifconfig**

eth0      Link encap:Ethernet   HWaddr 00:1f:16:0c:27:b7  
          UP BROADCAST MULTICAST   MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0  overruns:0 frame:0
           TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
           collisions:0 txqueuelen:1000 
          RX bytes:0  (0.0 B)  TX bytes:0 (0.0 B)
           Memory:f2600000-f2620000 
 

lo        Link encap:Local Loopback  
           inet addr:127.0.0.1  Mask:255.0.0.0
          inet6  addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING   MTU:16436  Metric:1
           RX packets:243 errors:0 dropped:0 overruns:0 frame:0
           TX packets:243 errors:0 dropped:0 overruns:0 carrier:0
           collisions:0 txqueuelen:0 
          RX bytes:23850  (23.8 KB)  TX bytes:23850 (23.8 KB)
 

wlan0     Link encap:Ethernet  HWaddr  00:21:5d:c2:bb:e2  
          UP BROADCAST MULTICAST  MTU:1500   Metric:1
          RX packets:19662 errors:0 dropped:0  overruns:0 frame:0
           TX packets:11896 errors:0 dropped:0 overruns:0 carrier:0
           collisions:0 txqueuelen:1000 
          RX  bytes:19926404 (19.9 MB)  TX bytes:1424086 (1.4 MB)



```[SIZE=2]***-- iwconfig --***[/SIZE]

```


**ryan@gaffney:~$ sudo iwconfig**

[sudo] password for ryan: 
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:"AirBears"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:1F:9E:8D:DF:C6   
          Bit Rate=0 kb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=63/70  Signal level=-47 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.


```[SIZE=2]***-- lshw --***[/SIZE]

```


**ryan@gaffney:~$ lshw -C network**

WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 82567LM Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 03
       serial: 00:1f:16:0c:27:b7
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e1000e driverversion=1.0.2-k2 firmware=1.8-3 latency=0 multicast=yes
       resources: irq:27 memory:f2600000-f261ffff memory:f2625000-f2625fff ioport:1840(size=32)
  *-network
       description: Wireless interface
       product: PRO/Wireless 5100 AGN [Shiloh] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 00
       serial: 00:21:5d:c2:bb:e2
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn driverversion=2.6.32-22-generic firmware=8.24.2.12 ip=10.10.64.41 latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:30 memory:f2500000-f2501fff


```[SIZE=2]***-- route --***[/SIZE]

```


**ryan@gaffney:~$ route -n**

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.10.64.0      0.0.0.0         255.255.252.0   U     0      0        0 wlan0
0.0.0.0         10.10.64.1      0.0.0.0         UG    0      0        0 wlan0


```[SIZE=2]***-- cat --***[/SIZE]

```


**ryan@gaffney:~$ cat /etc/network/interfaces**

auto lo
iface lo inet loopback
mtu 1500

**ryan@gaffney:~$ cat /etc/resolv.conf**

nameserver 128.32.206.9
nameserver 128.32.136.9
nameserver 128.32.206.12
nameserver 128.32.136.12
domain AirBears.Berkeley.EDU
search AirBears.Berkeley.EDU


```[SIZE=2]***-- ping --***[/SIZE]

```


**ryan@gaffney:~$ ping 136.152.176.23 -c 1 -s 1472 -M do**

PING 136.152.176.23 (136.152.176.23) 1472(1500) bytes of data.
1480 bytes from 136.152.176.23: icmp_seq=1 ttl=62 time=4.81 ms

--- 136.152.176.23 ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 4.815/4.815/4.815/0.000 ms


**ryan@gaffney:~$ ping 136.152.176.23 -c 1 -s 1473 -M do**

PING 136.152.176.23 (136.152.176.23) 1473(1501) bytes of data.
From 10.10.64.41 icmp_seq=1 Frag needed and DF set (mtu = 1500)

--- 136.152.176.23 ping statistics ---
0 packets transmitted, 0 received, +1 errors


```The unsecured network is obviously the only one I can test on right now since it won't connect at all to the network at my home.  Oh, also, I don't know if this will help, but my laptop is a Lenovo X200 Tablet.

Any help is much appreciated -- I am going freaking nuts!!!

---

### Post by jamdazzle on 2010-09-05
Here is how I fixed it.

sudo stop avahi-daemon
sudo sed -e '/start/,+1s/^/#/' /etc/init/avahi-daemon.conf 
sudo ifconfig wlan0 up
sudo iwconfig wlan0 essid AirBears
sudo iwconfig wlan0 mode managed
sudo dhclient wlan0

Hope this helps

---

### Post by Bunyak on 2010-09-29
Well?  Was this cure successful for you?  Dying to know... similar issues myself.

---

### Post by imsangha on 2011-02-28
Ok here is how i fixed it... 

1. sudo gedit /etc/default/grub
2. replace "quiet splash" with "quiet splash ipv6.disable=1"
3. save
4. sudo update-grub
5. restart

Even though I've uninstalled wicd and come back to network-manager, Airbears doesn't drop me anymore. Thanks goes to actionparsnip!

---

### Post by imsangha on 2011-03-01
Also, this link if you've installed wicd on your computer. 

[http://opennomad.com/content/ubuntu-lucid-wicd-and-domain-name-servers](http://opennomad.com/content/ubuntu-lucid-wicd-and-domain-name-servers)

---

