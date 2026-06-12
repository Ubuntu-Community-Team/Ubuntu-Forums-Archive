---
title: "No Internet After Installing Synce"
date: 2009-07-08
forum: Networking &amp; Wireless
---

### Post by wewantutopia on 2009-07-08
Hello, I just installed synce and now my wired (cable via Ethernet) internet connection is no longer running. It was working just fine until I installed synce and tethered my phone.   I am running Jaunty with a static IP.  I am running through a wireless router, but haven't changed anything with it.  Internet connection is working, my EEEpc is working fine via wifi.  Any help would be GREATLY appreciated!

---

### Post by wewantutopia on 2009-07-08
Ok, here is some info...I'm not really sure what you need.

Here is my /etc/network/interfaces:

```
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth0

# The primary network interface
auto eth0
iface eth0 inet static
        address 192.168.1.250
        netmask 255.255.255.0
        network 192.168.1.0
        broadcast 192.168.0.255
        gateway 192.168.1.1
```Here is route:

```
root@classwarfare:~# route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     0      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0
default         192.168.1.1     0.0.0.0         UG    100    0        0 eth0
```Here is ifconfig:

```
root@classwarfare:~# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:19:d1:7a:61:04  
          inet addr:192.168.1.250  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::219:d1ff:fe7a:6104/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:107733 errors:0 dropped:0 overruns:0 frame:0
          TX packets:108049 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:8841784 (8.8 MB)  TX bytes:7582258 (7.5 MB)
          Memory:e3200000-e3220000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1239 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1239 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:89554 (89.5 KB)  TX bytes:89554 (89.5 KB)
```I decided to try pinging after having read some other posts...  here is the result of 74.125.39.147 (that's what someone else tried so I figured I would too)

```
root@classwarfare:~# ping 74.125.39.147
PING 74.125.39.147 (74.125.39.147) 56(84) bytes of data.
64 bytes from 74.125.39.147: icmp_seq=1 ttl=235 time=137 ms
64 bytes from 74.125.39.147: icmp_seq=2 ttl=235 time=145 ms
64 bytes from 74.125.39.147: icmp_seq=3 ttl=235 time=144 ms
64 bytes from 74.125.39.147: icmp_seq=4 ttl=235 time=133 ms
^C
--- 74.125.39.147 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3001ms
rtt min/avg/max/mdev = 133.497/140.179/145.491/5.071 ms
```If I enter 74.125.39.147   in the firefox address bar it goes to Google (english)

Here I ping [www.google.com]("http://www.google.com")

```
root@classwarfare:~# ping www.google.com
ping: unknown host www.google.com

```

And when I type google.com in the firefox address bar I get address not found.

I hope any of this will help.  You help would be GREATLY appreciated!

---

### Post by wewantutopia on 2009-07-08
In network tools i try ping and ping ubuntu.com 

it spits back an error saying the address ubuntu.com cannot be found  please enter a valid network address and try again.  

Anyone have any ideas?

---

