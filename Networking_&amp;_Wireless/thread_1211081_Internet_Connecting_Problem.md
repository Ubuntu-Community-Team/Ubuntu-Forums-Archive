---
title: "Internet Connecting Problem"
date: 2009-07-12
forum: Networking &amp; Wireless
---

### Post by shahan on 2009-07-12
I use WIRED connection. I can connect on WindowsXP. It is so easy. I Need to setup the IP, Netmask, Gateway, DNS and Network 10Mbps
then it is connected in WindowsXP
But I tried on ubuntu. It doesn't connect.

---

### Post by grappler on 2009-07-12
Are you using gnome-network manager? Mine auto-connects to a wired connection when it is plugged in. 

Does the network-manager icon have "Enable Networking" ticked? 

Give us more information.

---

### Post by superprash2003 on 2009-07-12
post output of **ifconfig** from the terminal

---

### Post by shahan on 2009-07-13
here is some screen shot of my UBUNTU 9.04 about connecting internet
[Ubuntu 9.04]("http://i714.photobucket.com/albums/ww145/shahan011/myinternet.png")

I have set everything, but there is one more setting which I need to make for windows XP. See the screenshot below

[http://i714.photobucket.com/albums/ww145/shahan011/LinkSpeed.jpg]("http://i714.photobucket.com/albums/ww145/shahan011/LinkSpeed.jpg")

how can I set it in my ubuntu 9.04

---

### Post by shahan on 2009-07-14
> **shahan said:**
> here is some screen shot of my UBUNTU 9.04 about connecting internet
[Ubuntu 9.04]("http://i714.photobucket.com/albums/ww145/shahan011/myinternet.png")

I have set everything, but there is one more setting which I need to make for windows XP. See the screenshot below

[http://i714.photobucket.com/albums/ww145/shahan011/LinkSpeed.jpg]("http://i714.photobucket.com/albums/ww145/shahan011/LinkSpeed.jpg")

how can I set it in my ubuntu 9.04


is there any one who can help me?

---

### Post by superprash2003 on 2009-07-14
do you really need to make that setting? it should work automatically.. have you tried restarting networking after making changes to the /etc/network/interfaces file?

---

### Post by shahan on 2009-07-14
> **superprash2003 said:**
> do you really need to make that setting? it should work automatically.. have you tried restarting networking after making changes to the /etc/network/interfaces file?

I have tried my level best. In windows XP I am to configure the [10Mbps speed]("http://i714.photobucket.com/albums/ww145/shahan011/LinkSpeed.jpg") maunally. If I don't do it. it becomes unable to browse the site. 
 How to do it in ubuntu 9.04.

---

### Post by martinbaselier on 2009-07-14
To change the speed open a terminal and type or paste (ctrl+shift+v) the following line:

sudo ethtool eth0 speed 100

replace eth0 with the name of yournetworkcard. If you only have one, it's probably eth0.

Please check if this works and if it's really necessary. 

If the answer to both question is yes, proceed with:

echo ethtool eth0 speed 100 | sudo tee -a /etc/rc.local

---

### Post by shahan on 2009-07-14
> **martinbaselier said:**
> To change the speed open a terminal and type or paste (ctrl+shift+v) the following line:

sudo ethtool eth0 speed 100

replace eth0 with the name of yournetworkcard. If you only have one, it's probably eth0.

Please check if this works and if it's really necessary. 

If the answer to both question is yes, proceed with:

echo ethtool eth0 speed 100 | sudo tee -a /etc/rc.local

In windows Xp I am to change it into 10, not 100....
what should I do now?
sudo ethtool eth0 speed 100
or,
sudo ethtool eth0 speed 10


echo ethtool eth0 speed 100 | sudo tee -a /etc/rc.local
or,
echo ethtool eth0 speed 10 | sudo tee -a /etc/rc.local

---

### Post by taziturn on 2009-07-14
i have the same problem too.

---

### Post by Thorstien78 on 2009-07-14
I had a similar problem. this worked for me. go to Applications/Terminal and type  
**sudo dhclient eth0**

here is where i found it  [http://ubuntuforums.org/archive/index.php/t-994525.html](http://ubuntuforums.org/archive/index.php/t-994525.html)

---

### Post by shahan on 2009-07-15
> **taziturn said:**
> i have the same problem too.

is there any one who can help us??????????

---

### Post by shahan on 2009-07-15
> **martinbaselier said:**
> To change the speed open a terminal and type or paste (ctrl+shift+v) the following line:

sudo ethtool eth0 speed 100

replace eth0 with the name of yournetworkcard. If you only have one, it's probably eth0.

Please check if this works and if it's really necessary. 

If the answer to both question is yes, proceed with:

echo ethtool eth0 speed 100 | sudo tee -a /etc/rc.local


I have tried this but there is some thing unexpected....see the screenshot
[click here]("http://i714.photobucket.com/albums/ww145/shahan011/ethtool.png")

---

### Post by Norcoracer25 on 2009-07-16
Hey Everyone. Let me start off by saying I love gOS and have been using it on my old PC and just installed it from my USB drive onto my Asus EEE PC 1000. Well thats when the problems started happening.. I gave the laptop a wired ethernet connection and it just didnt even reckognize it so I couldnt get any updates for the computer.. so now I cant connect using a wireless connection either... So I cant solve any problems from my EEE PC. Im using my desktop.... Can someone please help me! Im getting so frustrated with this! Thank you.

---

### Post by Norcoracer25 on 2009-07-16
Sorry guys. I posted in the wrong area!

---

### Post by shahan on 2009-07-17
my problem is not solving

---

### Post by martinbaselier on 2009-07-17
sorry guys I made a mistake (2 actually)

the correct statement is:

[B]sudo ethtool -s eth0 speed 100
[/B]
Use 10 if you want to change it to 10mbps

And for it to run automatically each time you boot, you need to add it **/etc/rc.local** before the **exit 0**-statement (there are other ways, but this is one of the easiest.)
To do so type:
**sudo gedit /etc/rc.local**

I just did a very quick **man ethtool** the first time.

---

### Post by shahan on 2009-07-19
it is not connecting.

I have used ping google.com

nothing is happening....it is not pinging

---

### Post by shahan on 2009-07-22
site is not pinging

[click me]("http://i714.photobucket.com/albums/ww145/shahan011/pingsite.png")

---

### Post by shahan on 2009-07-23
shahan@ubuntu:~$ ping 192.168.10.116
PING 192.168.10.116 (192.168.10.116) 56(84) bytes of data.
64 bytes from 192.168.10.116: icmp_seq=1 ttl=64 time=0.033 ms
64 bytes from 192.168.10.116: icmp_seq=2 ttl=64 time=0.024 ms
^C
--- 192.168.10.116 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.024/0.028/0.033/0.007 ms
shahan@ubuntu:~$ sudo dhclient eth0
[sudo] password for shahan: 
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:24:1d:36:f5:44
Sending on   LPF/eth0/00:24:1d:36:f5:44
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 20
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
shahan@ubuntu:~$ ipconfig
bash: ipconfig: command not found
shahan@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:24:1d:36:f5:44  
          inet6 addr: fe80::224:1dff:fe36:f544/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:882 errors:0 dropped:0 overruns:0 frame:0
          TX packets:39 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:77166 (77.1 KB)  TX bytes:7605 (7.6 KB)
          Interrupt:253 Base address:0xc000 

eth0:avahi Link encap:Ethernet  HWaddr 00:24:1d:36:f5:44  
          inet addr:169.254.6.41  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:253 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:56 errors:0 dropped:0 overruns:0 frame:0
          TX packets:56 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4240 (4.2 KB)  TX bytes:4240 (4.2 KB)

---

### Post by xihad76 on 2009-07-23
&#2486;&#2494;&#2489;&#2494;&#2472; &#2477;&#2494;&#2439;, &#2438;&#2474;&#2472;&#2494;&#2480;&#2503;&#2451; &#2439;&#2472;&#2509;&#2463;&#2494;&#2480;&#2472;&#2503;&#2463; &#2472;&#2495;&#2527;&#2494; &#2461;&#2494;&#2478;&#2503;&#2482;&#2494;&#2527; &#2474;&#2524;&#2468;&#2503; &#2470;&#2503;&#2454;&#2503; &#2474;&#2504;&#2486;&#2494;&#2458;&#2495;&#2453; &#2438;&#2472;&#2472;&#2509;&#2470; &#2474;&#2494;&#2439;&#2468;&#2503;&#2488;&#2495;! :d &#2438;&#2478;&#2494;&#2480; &#2447;&#2460; &#2478;&#2507;&#2465;&#2503;&#2478; &#2470;&#2495;&#2527;&#2503;&#2451; &#2460;&#2495;&#2474;&#2495;&#2468;&#2503; &#2453;&#2494;&#2478; &#2453;&#2480;&#2468;&#2503;&#2488;&#2503;&#2472;&#2494;&#2404; &#2441;&#2476;&#2497;&#2472;&#2509;&#2463;&#2497; &#2460;&#2472;&#2509;&#2463;&#2495; &#2478;&#2472;&#2509;&#2463;&#2495; &#2474;&#2494;&#2472;&#2509;&#2463;&#2495;&#2480; &#2441;&#2474;&#2480; &#2478;&#2503;&#2460;&#2494;&#2460; &#2454;&#2494;&#2480;&#2494;&#2474; &#2489;&#2439;&#2468;&#2503;&#2488;&#2503; &#2447;&#2454;&#2472; :(

---

### Post by shahan on 2009-07-23
> **xihad76 said:**
> &#2486;&#2494;&#2489;&#2494;&#2472; &#2477;&#2494;&#2439;, &#2438;&#2474;&#2472;&#2494;&#2480;&#2503;&#2451; &#2439;&#2472;&#2509;&#2463;&#2494;&#2480;&#2472;&#2503;&#2463; &#2472;&#2495;&#2527;&#2494; &#2461;&#2494;&#2478;&#2503;&#2482;&#2494;&#2527; &#2474;&#2524;&#2468;&#2503; &#2470;&#2503;&#2454;&#2503; &#2474;&#2504;&#2486;&#2494;&#2458;&#2495;&#2453; &#2438;&#2472;&#2472;&#2509;&#2470; &#2474;&#2494;&#2439;&#2468;&#2503;&#2488;&#2495;! :d &#2438;&#2478;&#2494;&#2480; &#2447;&#2460; &#2478;&#2507;&#2465;&#2503;&#2478; &#2470;&#2495;&#2527;&#2503;&#2451; &#2460;&#2495;&#2474;&#2495;&#2468;&#2503; &#2453;&#2494;&#2478; &#2453;&#2480;&#2468;&#2503;&#2488;&#2503;&#2472;&#2494;&#2404; &#2441;&#2476;&#2497;&#2472;&#2509;&#2463;&#2497; &#2460;&#2472;&#2509;&#2463;&#2495; &#2478;&#2472;&#2509;&#2463;&#2495; &#2474;&#2494;&#2472;&#2509;&#2463;&#2495;&#2480; &#2441;&#2474;&#2480; &#2478;&#2503;&#2460;&#2494;&#2460; &#2454;&#2494;&#2480;&#2494;&#2474; &#2489;&#2439;&#2468;&#2503;&#2488;&#2503; &#2447;&#2454;&#2472; :(
&#2438;&#2474;&#2472;&#2494;&#2480; &#2478;&#2507;&#2465;&#2503;&#2478; &#2447;&#2480; &#2476;&#2495;&#2488;&#2509;&#2468;&#2494;&#2480;&#2495;&#2468; &#2488;&#2489; &#2482;&#2495;&#2454;&#2503;&#2472;&#2404; &#2438;&#2486;&#2494; &#2453;&#2480;&#2495; &#2488;&#2494;&#2489;&#2494;&#2479;&#2509;&#2479; &#2453;&#2480;&#2468;&#2503; &#2474;&#2494;&#2480;&#2476;&#2404; 
[&#2447;&#2439; &#2482;&#2495;&#2434;&#2453; &#2463;&#2495; &#2470;&#2503;&#2454;&#2503;&#2472;]("http://forum.amaderprojukti.com/viewtopic.php?f=42&t=3223")
&#2438;&#2486;&#2494; &#2453;&#2480;&#2495; &#2441;&#2474;&#2453;&#2499;&#2468; &#2489;&#2476;&#2503;&#2472;&#2404;

---

### Post by shahan on 2009-07-23
is it possible that, the problem is occouring because of ISP?

---

### Post by xihad76 on 2009-07-23
> **shahan said:**
> &#2438;&#2474;&#2472;&#2494;&#2480; &#2478;&#2507;&#2465;&#2503;&#2478; &#2447;&#2480; &#2476;&#2495;&#2488;&#2509;&#2468;&#2494;&#2480;&#2495;&#2468; &#2488;&#2489; &#2482;&#2495;&#2454;&#2503;&#2472;&#2404; &#2438;&#2486;&#2494; &#2453;&#2480;&#2495; &#2488;&#2494;&#2489;&#2494;&#2479;&#2509;&#2479; &#2453;&#2480;&#2468;&#2503; &#2474;&#2494;&#2480;&#2476;&#2404; 
[&#2447;&#2439; &#2482;&#2495;&#2434;&#2453; &#2463;&#2495; &#2470;&#2503;&#2454;&#2503;&#2472;]("http://forum.amaderprojukti.com/viewtopic.php?f=42&t=3223")
&#2438;&#2486;&#2494; &#2453;&#2480;&#2495; &#2441;&#2474;&#2453;&#2499;&#2468; &#2489;&#2476;&#2503;&#2472;&#2404;

&#2438;&#2478;&#2495; &#2437;&#2482;&#2480;&#2503;&#2465;&#2495; &#2474;&#2507;&#2488;&#2509;&#2463; &#2453;&#2480;&#2488;&#2495; [&#2447;&#2439;&#2454;&#2494;&#2472;&#2503;]("http://ubuntuforums.org/showthread.php?t=1220100")&#2404; &#2453;&#2495;&#2472;&#2509;&#2468;&#2497; &#2447;&#2454;&#2472;&#2507; &#2438;&#2486;&#2494;&#2472;&#2497;&#2480;&#2497;&#2474; &#2488;&#2494;&#2524;&#2494; &#2474;&#2494;&#2439;&#2472;&#2495;&#2404; 

&#2438;&#2480; &#2438;&#2478;&#2495; &#2438;&#2439;&#2441;&#2463;&#2495;&#2527;&#2494;&#2472;'&#2534;&#2539; &#2404; &#2453;&#2494;&#2460;&#2503;&#2439; &#2438;&#2474;&#2472;&#2495; &#2453;&#2480;&#2503; &#2476;&#2482;&#2494;&#2480; &#2453;&#2507;&#2472; &#2478;&#2494;&#2472;&#2503; &#2489;&#2527;&#2472;&#2494;! :D:D:D

---

### Post by shahan on 2009-07-23
> **xihad76 said:**
> 

&#2438;&#2480; &#2438;&#2478;&#2495; &#2438;&#2439;&#2441;&#2463;&#2495;&#2527;&#2494;&#2472;'&#2534;&#2539; &#2404; &#2453;&#2494;&#2460;&#2503;&#2439; &#2438;&#2474;&#2472;&#2495; &#2453;&#2480;&#2503; &#2476;&#2482;&#2494;&#2480; &#2453;&#2507;&#2472; &#2478;&#2494;&#2472;&#2503; &#2489;&#2527;&#2472;&#2494;! :d:d:d
[size="5"]&#2476;&#2497;&#2461;&#2482;&#2494;&#2478; &#2472;&#2494;!!![/size]

---

### Post by shahan on 2009-07-27
Tried 8.10 too...
oh my GOD.......
didn't connected yet......
shahan@ubuntu:~$ sudo invoke-rc.d networking restart
 * Reconfiguring network interfaces...                                   [ OK ] 
shahan@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:24:1d:36:f5:44  
          inet addr:192.168.10.116  Bcast:192.168.10.255  Mask:255.255.255.0
          inet6 addr: fe80::224:1dff:fe36:f544/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:936351246 overruns:0 frame:0
          TX packets:657 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:173007 (173.0 KB)
          Interrupt:221 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1376 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1376 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:98160 (98.1 KB)  TX bytes:98160 (98.1 KB)

shahan@ubuntu:~$ ping google.com
ping: unknown host google.com
shahan@ubuntu:~$ ping google.com
ping: unknown host google.com
shahan@ubuntu:~$ ping 192.168.10.116
PING 192.168.10.116 (192.168.10.116) 56(84) bytes of data.
64 bytes from 192.168.10.116: icmp_seq=1 ttl=64 time=0.033 ms
ping: sendmsg: Network is unreachable
ping: sendmsg: Network is unreachable
ping: sendmsg: Network is unreachable
ping: sendmsg: Network is unreachable
64 bytes from 192.168.10.116: icmp_seq=6 ttl=64 time=0.037 ms
ping: sendmsg: Network is unreachable
ping: sendmsg: Network is unreachable
ping: sendmsg: Network is unreachable
^C
--- 192.168.10.116 ping statistics ---
9 packets transmitted, 2 received, 77% packet loss, time 8007ms
rtt min/avg/max/mdev = 0.033/0.035/0.037/0.002 ms
shahan@ubuntu:~$

---

### Post by shahan on 2009-09-13
After a long time I have installed UBUNTU again. it is now 8.04.3 before it was 8.04.2. However, , His time I failed againn to connect internet. I don't know why it is occurring. Is any body here who really can help me?

---

### Post by shahan on 2009-09-13
any one here who can escape me from the problem???

---

### Post by shahan on 2009-10-18
> **grappler said:**
> Are you using gnome-network manager? Mine auto-connects to a wired connection when it is plugged in. 

Does the network-manager icon have "Enable Networking" ticked? 

Give us more information.

may be yours is DHCP

---

### Post by shahan on 2009-11-04
new problem arises

[http://i714.photobucket.com/albums/ww145/shahan011/NetworkManager.png](http://i714.photobucket.com/albums/ww145/shahan011/NetworkManager.png)

Is there no solution for my problem?

---

### Post by cariboo on 2009-11-09
@shahan

Instead of posting screenshots, could copy and paste the following from the terminal.

```
sudo lshw -C network
```

The above command will list all your network devices, and whether the proper driver is installed.

```
ifconfig
```

This command will show use whether you are getting an ip address.

To copy and paste from a terminal, just highlight the text with your mouse, then to click where you want to paste then press the mouse wheel if you have one, or both mouse buttons at the same time if you don't.

From what I've seen from this thread, you are making things to complicated, do one thing at a time, it'll make things a lot easier.

Also this is an English only forum, please post in English, or don't post at all.

---

### Post by shahan on 2009-11-09
ok...
posting the codes....
going to ubuntu 
rstarting Windows XP

---

### Post by shahan on 2009-11-09
> **cariboo907 said:**
> @shahan

Instead of posting screenshots, could copy and paste the following from the terminal.

```
sudo lshw -C network
```

The above command will list all your network devices, and whether the proper driver is installed.

```
ifconfig
```


**Mine is UBUNTU 9.10 Right now. It is a fresh installation.**

**sudo lshw -C network**
shahan@shahan-desktop:~$ sudo lshw -C network 
[sudo] password for shahan:  
  *-network                
       description: Ethernet interface 
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller 
       vendor: Realtek Semiconductor Co., Ltd. 
       physical id: 0 
       bus info: pci@0000:02:00.0 
       logical name: eth0 
       version: 02 
       serial: 00:24:1d:36:f5:44 
       size: 10MB/s 
       capacity: 100MB/s 
       width: 64 bits 
       clock: 33MHz 
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation 
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s 
       resources: irq:27 ioport:be00(size=256) memory:fddff000-fddfffff(prefetchable) memory:fdde0000-fddeffff(prefetchable) memory:fdd00000-fdd1ffff(prefetchable) 
shahan@shahan-desktop:~$  



**ifconfig**
shahan@shahan-desktop:~$ ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:24:1d:36:f5:44   
          inet6 addr: fe80::224:1dff:fe36:f544/64 Scope:Link 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:3 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000  
          RX bytes:0 (0.0 B)  TX bytes:238 (238.0 B) 
          Interrupt:27 Base address:0xc000  
 
lo        Link encap:Local Loopback   
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0  
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
 
shahan@shahan-desktop:~$


**I am so thirsty to use internet on my UBUNTU 9.10 using my static IP broadband wired connection.**

---

### Post by cariboo on 2009-11-09
Can you get it to work with a dynamic address?

The first thing we need to know is how you are connecting, cable modem, or DSL?

---

### Post by shahan on 2009-11-09
> **cariboo907 said:**
> Can you get it to work with a dynamic address?

The first thing we need to know is how you are connecting, cable modem, or DSL?

I use my LAN(attached with my motherboard)
To be connected on WIndows XP I am to use my 
Ip (192.168.10.116)
subnet mast (255.255.255.0)
Default gateway (192.168.10.1)
DNS 123.49.44.129
    123.49.44.130
    123.49.44.131
    123.49.44.132
(I am to use this four, if I use 2 or 3, it doesn't work)

the last thing is 
I am to change my Link Speed/Duplex Mode to 10Mbps/Full Duplex

No need to set any MAC address(physical address)
(but when I see ipconfig/all(in windows XP) command on CMD(start>run) I see the following output

> Microsoft Windows XP [Version 5.1.2600]
(C) Copyright 1985-2001 Microsoft Corp.

C:\Documents and Settings\Sh@han's>ipconfig/all

Windows IP Configuration

        Host Name . . . . . . . . . . . . : www-8eef1b1b4bc
        Primary Dns Suffix  . . . . . . . :
        Node Type . . . . . . . . . . . . : Unknown
        IP Routing Enabled. . . . . . . . : No
        WINS Proxy Enabled. . . . . . . . : No

Ethernet adapter Local Area Connection:

        Connection-specific DNS Suffix  . :
        Description . . . . . . . . . . . : Realtek RTL8102E Family PCI-E Fast E
thernet NIC
        Physical Address. . . . . . . . . : 00-08-56-00-08-69
        Dhcp Enabled. . . . . . . . . . . : No
        IP Address. . . . . . . . . . . . : 192.168.10.116
        Subnet Mask . . . . . . . . . . . : 255.255.255.0
        Default Gateway . . . . . . . . . : 192.168.10.1
        DNS Servers . . . . . . . . . . . : 123.49.44.129
                                            123.49.44.130
                                            123.49.44.131
                                            123.49.44.132

C:\Documents and Settings\Sh@han's>

In this output we see the physical address is 00-08-56-00-08-69

but when I see the ifconfig on ubuntu(terminal) I see that there the physical address is 00:24:1d:36:f5:44 (HWaddr 00:24:1d:36:f5:44 ) I dont know why it happens.

That all my procedure to be connected on internet on Windows XP

---

### Post by cariboo on 2009-11-09
Before making all the changes, make sure you can connect to the internet. Why are you setting the network speed, most nics auto-negotiate the speed. I will stress again make sure your network connection works before trying to set  up anything else.

What is it you are trying to do?

---

### Post by shahan on 2009-11-10
> **cariboo907 said:**
> Before making all the changes, make sure you can connect to the internet. Why are you setting the network speed, most nics auto-negotiate the speed. I will stress again make sure your network connection works before trying to set up anything else.
 
What is it you are trying to do?
 
No....If I don't make any change it doesn't connect...Because mine is not Dynaic IP....
Mine is Static IP(I am sure about it...)
 
In windows XP I am to change the Network speed ...Otherewise it doesn't connect...I don't know why...thats all....

---

### Post by cariboo on 2009-11-10
I still don't know what you are trying to do, are you trying to share a connection between two computers. What are you using a dns server for. do you have a large network? Why do you need 4 network addresses? You still haven't said how you connect to the internet. 

A lot more info would be helpful.

---

### Post by shahan on 2009-11-10
> **cariboo907 said:**
> I still don't know what you are trying to do, are you trying to share a connection between two computers. What are you using a dns server for. do you have a large network? Why do you need 4 network addresses? You still haven't said how you connect to the internet. 
 
A lot more info would be helpful.
 
No I am just making an internet connection in my computer.....not sharing any connection...
I don't know why DNS is used for.
 
But the ISP usually share their line to many users....

---

### Post by cariboo on 2009-11-10
You don't need Bind9 remove it, you don't need 4 ip addresses get rid of them. If you isp provides a static ip address, does your cable/DSl modem provide dhcp?

You are trying to do way to much to get a network connection. it is pretty simple:

Internet-->modem-->computer

Can you post the network information from Windows. Go to Start-->Run, type cmd and press enter. Once at the command prompt type:

```
ipconfig /all > ipconfig.txt
```

the file will be located in C:\Documents and Settings\<user> where <user> is your user name, if you have a default Windows setup, the file will probably be called ipconfig.

---

### Post by shahan on 2009-11-10
> **cariboo907 said:**
> You don't need Bind9 remove it, you don't need 4 ip addresses get rid of them. If you isp provides a static ip address, does your cable/DSl modem provide dhcp?
 
Can you post the network information from Windows. Go to Start-->Run, type cmd and press enter. Once at the command prompt type:
 
```
ipconfig /all > ipconfig.txt
```
 

No ...My ISP doesn't provide dhcp...
 
**Here is my ipconfig.txt file....**
>  
Windows IP Configuration
 
        Host Name . . . . . . . . . . . . : www-8eef1b1b4bc
        Primary Dns Suffix  . . . . . . . : 
        Node Type . . . . . . . . . . . . : Unknown
        IP Routing Enabled. . . . . . . . : No
        WINS Proxy Enabled. . . . . . . . : No
 
Ethernet adapter Local Area Connection:
 
        Connection-specific DNS Suffix  . : 
        Description . . . . . . . . . . . : Realtek RTL8102E Family PCI-E Fast Ethernet NIC
        Physical Address. . . . . . . . . : 00-08-56-00-08-69
        Dhcp Enabled. . . . . . . . . . . : No
        IP Address. . . . . . . . . . . . : 192.168.10.116
        Subnet Mask . . . . . . . . . . . : 255.255.255.0
        Default Gateway . . . . . . . . . : 192.168.10.1
        DNS Servers . . . . . . . . . . . : 123.49.44.129
                                            123.49.44.130
                                            123.49.44.131
                                            123.49.44.132
 
>  
You are trying to do way to much to get a network connection. it is pretty simple:
 
Internet-->modem-->computer

In UBUNTU 9.10 I don't get modem after Internet>modem....

---

### Post by pinenut on 2009-11-10
> **shahan said:**
> **Mine is UBUNTU 9.10 Right now. It is a fresh installation.**
..........

**ifconfig**
shahan@shahan-desktop:~$ ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:24:1d:36:f5:44   
          inet6 addr: fe80::224:1dff:fe36:f544/64 Scope:Link 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
.............


I do not see the IPv4 address. You should see two lines as below for both IPv4 and IPv6 addresses. 

inet addr:192.168.0.144  Bcast:192.168.0.255  Mask:255.255.255.0
inet6 addr: fe80::217:31ff:fe70:af88/64 Scope:Link

---

### Post by shahan on 2009-11-10
> **pinenut said:**
> I do not see the IPv4 address. You should see two lines as below for both IPv4 and IPv6 addresses. 
 
inet addr:192.168.0.144 Bcast:192.168.0.255 Mask:255.255.255.0
inet6 addr: fe80::217:31ff:fe70:af88/64 Scope:Link
 
I don't know why it is like that....
 
From the following output we can understand that my PC is connected with the ISP local PC.
```

[FONT=Times New Roman][COLOR=#333333][FONT=SolaimanLipi]shahan@shahan-desktop:~$ sudo /etc/init.d/networking restart[/FONT][/COLOR][COLOR=#333333][FONT=SolaimanLipi][/FONT][/COLOR][/FONT]
[COLOR=#333333][FONT=SolaimanLipi][FONT=Times New Roman][/FONT][/FONT][/COLOR]
[FONT=Times New Roman][COLOR=#333333][FONT=SolaimanLipi] * Reconfiguring network interfaces...                                          SIOCDELRT: No such process[/FONT][/COLOR][COLOR=#333333][FONT=SolaimanLipi][/FONT][/COLOR][/FONT]
[COLOR=#333333][FONT=SolaimanLipi][FONT=Times New Roman][/FONT][/FONT][/COLOR]
[FONT=Times New Roman][COLOR=#333333][FONT=SolaimanLipi]                                                                         [ OK ][/FONT][/COLOR][COLOR=#333333][FONT=SolaimanLipi][/FONT][/COLOR][/FONT]
[COLOR=#333333][FONT=SolaimanLipi][FONT=Times New Roman][/FONT][/FONT][/COLOR]
[FONT=Times New Roman][COLOR=#333333][FONT=SolaimanLipi]shahan@shahan-desktop:~$ sudo /etc/init.d/networking restart[/FONT][/COLOR][COLOR=#333333][FONT=SolaimanLipi][/FONT][/COLOR][/FONT]
[COLOR=#333333][FONT=SolaimanLipi][FONT=Times New Roman][/FONT][/FONT][/COLOR]
[FONT=Times New Roman][COLOR=#333333][FONT=SolaimanLipi] * Reconfiguring network interfaces...                                   [ OK ] [/FONT][/COLOR][COLOR=#333333][FONT=SolaimanLipi][/FONT][/COLOR][/FONT]
[COLOR=#333333][FONT=SolaimanLipi][FONT=Times New Roman][/FONT][/FONT][/COLOR]
[FONT=Times New Roman][COLOR=#333333][FONT=SolaimanLipi]shahan@shahan-desktop:~$ ping 192.168.10.116[/FONT][/COLOR][COLOR=#333333][FONT=SolaimanLipi][/FONT][/COLOR][/FONT]
[COLOR=#333333][FONT=SolaimanLipi][FONT=Times New Roman][/FONT][/FONT][/COLOR]
[FONT=Times New Roman][COLOR=#333333][FONT=SolaimanLipi]PING 192.168.10.116 (192.168.10.116) 56(84) bytes of data.[/FONT][/COLOR][COLOR=#333333][FONT=SolaimanLipi][/FONT][/COLOR][/FONT]
[COLOR=#333333][FONT=SolaimanLipi][FONT=Times New Roman][/FONT][/FONT][/COLOR]
[FONT=Times New Roman][COLOR=#333333][FONT=SolaimanLipi]64 bytes from 192.168.10.116: icmp_seq=1 ttl=64 time=0.038 ms[/FONT][/COLOR][COLOR=#333333][FONT=SolaimanLipi][/FONT][/COLOR][/FONT]
[COLOR=#333333][FONT=SolaimanLipi][FONT=Times New Roman][/FONT][/FONT][/COLOR]
[FONT=Times New Roman][COLOR=#333333][FONT=SolaimanLipi]64 bytes from 192.168.10.116: icmp_seq=2 ttl=64 time=0.029 ms[/FONT][/COLOR][COLOR=#333333][FONT=SolaimanLipi][/FONT][/COLOR][/FONT]
[COLOR=#333333][FONT=SolaimanLipi][FONT=Times New Roman][/FONT][/FONT][/COLOR]
[FONT=Times New Roman][COLOR=#333333][FONT=SolaimanLipi]64 bytes from 192.168.10.116: icmp_seq=3 ttl=64 time=0.028 ms[/FONT][/COLOR][COLOR=#333333][FONT=SolaimanLipi][/FONT][/COLOR][/FONT]
[COLOR=#333333][FONT=SolaimanLipi][FONT=Times New Roman][/FONT][/FONT][/COLOR]
[FONT=Times New Roman][COLOR=#333333][FONT=SolaimanLipi]64 bytes from 192.168.10.116: icmp_seq=4 ttl=64 time=0.043 ms[/FONT][/COLOR][COLOR=#333333][FONT=SolaimanLipi][/FONT][/COLOR][/FONT]
[COLOR=#333333][FONT=SolaimanLipi][FONT=Times New Roman][/FONT][/FONT][/COLOR]
[FONT=Times New Roman][COLOR=#333333][FONT=SolaimanLipi]64 bytes from 192.168.10.116: icmp_seq=5 ttl=64 time=0.043 ms[/FONT][/COLOR][COLOR=#333333][FONT=SolaimanLipi][/FONT][/COLOR][/FONT]
[COLOR=#333333][FONT=SolaimanLipi][FONT=Times New Roman][/FONT][/FONT][/COLOR]
[FONT=Times New Roman][COLOR=#333333][FONT=SolaimanLipi]64 bytes from 192.168.10.116: icmp_seq=6 ttl=64 time=0.030 ms[/FONT][/COLOR][COLOR=#333333][FONT=SolaimanLipi][/FONT][/COLOR][/FONT]
[COLOR=#333333][FONT=SolaimanLipi][FONT=Times New Roman][/FONT][/FONT][/COLOR]
[FONT=Times New Roman][COLOR=#333333][FONT=SolaimanLipi]64 bytes from 192.168.10.116: icmp_seq=7 ttl=64 time=0.043 ms[/FONT][/COLOR][COLOR=#333333][FONT=SolaimanLipi][/FONT][/COLOR][/FONT]
[COLOR=#333333][FONT=SolaimanLipi][FONT=Times New Roman][/FONT][/FONT][/COLOR]
[FONT=Times New Roman][COLOR=#333333][FONT=SolaimanLipi]64 bytes from 192.168.10.116: icmp_seq=8 ttl=64 time=0.043 ms[/FONT][/COLOR][COLOR=#333333][FONT=SolaimanLipi][/FONT][/COLOR][/FONT]
[COLOR=#333333][FONT=SolaimanLipi][FONT=Times New Roman][/FONT][/FONT][/COLOR]
[FONT=Times New Roman][COLOR=#333333][FONT=SolaimanLipi]64 bytes from 192.168.10.116: icmp_seq=9 ttl=64 time=0.042 ms[/FONT][/COLOR][COLOR=#333333][FONT=SolaimanLipi][/FONT][/COLOR][/FONT]
[COLOR=#333333][FONT=SolaimanLipi][FONT=Times New Roman][/FONT][/FONT][/COLOR]
[FONT=Times New Roman][COLOR=#333333][FONT=SolaimanLipi]64 bytes from 192.168.10.116: icmp_seq=10 ttl=64 time=0.029 ms[/FONT][/COLOR][COLOR=#333333][FONT=SolaimanLipi][/FONT][/COLOR][/FONT]
[COLOR=#333333][FONT=SolaimanLipi][FONT=Times New Roman][/FONT][/FONT][/COLOR]
[FONT=Times New Roman][COLOR=#333333][FONT=SolaimanLipi]64 bytes from 192.168.10.116: icmp_seq=11 ttl=64 time=0.028 ms[/FONT][/COLOR][COLOR=#333333][FONT=SolaimanLipi][/FONT][/COLOR][/FONT]
[COLOR=#333333][FONT=SolaimanLipi][FONT=Times New Roman][/FONT][/FONT][/COLOR]
[FONT=Times New Roman][COLOR=#333333][FONT=SolaimanLipi]64 bytes from 192.168.10.116: icmp_seq=12 ttl=64 time=0.030 ms[/FONT][/COLOR][COLOR=#333333][FONT=SolaimanLipi][/FONT][/COLOR][/FONT]
[COLOR=#333333][FONT=SolaimanLipi][FONT=Times New Roman][/FONT][/FONT][/COLOR]
[FONT=Times New Roman][COLOR=#333333][FONT=SolaimanLipi]64 bytes from 192.168.10.116: icmp_seq=13 ttl=64 time=0.030 ms[/FONT][/COLOR][COLOR=#333333][FONT=SolaimanLipi][/FONT][/COLOR][/FONT]
[COLOR=#333333][FONT=SolaimanLipi][FONT=Times New Roman][/FONT][/FONT][/COLOR]
[FONT=Times New Roman][COLOR=#333333][FONT=SolaimanLipi]ping: sendmsg: Network is unreachable[/FONT][/COLOR][COLOR=#333333][FONT=SolaimanLipi][/FONT][/COLOR][/FONT]
[COLOR=#333333][FONT=SolaimanLipi][FONT=Times New Roman][/FONT][/FONT][/COLOR]
[FONT=Times New Roman][COLOR=#333333][FONT=SolaimanLipi]ping: sendmsg: Network is unreachable[/FONT][/COLOR][COLOR=#333333][FONT=SolaimanLipi][/FONT][/COLOR][/FONT]
[COLOR=#333333][FONT=SolaimanLipi][FONT=Times New Roman][/FONT][/FONT][/COLOR]
[FONT=Times New Roman][COLOR=#333333][FONT=SolaimanLipi]ping: sendmsg: Network is unreachable[/FONT][/COLOR][COLOR=#333333][FONT=SolaimanLipi][/FONT][/COLOR][/FONT]
[COLOR=#333333][FONT=SolaimanLipi][FONT=Times New Roman][/FONT][/FONT][/COLOR]
[FONT=Times New Roman][COLOR=#333333][FONT=SolaimanLipi]ping: sendmsg: Network is unreachable[/FONT][/COLOR][COLOR=#333333][FONT=SolaimanLipi][/FONT][/COLOR][/FONT]
[COLOR=#333333][FONT=SolaimanLipi][FONT=Times New Roman][/FONT][/FONT][/COLOR]
[FONT=Times New Roman][COLOR=#333333][FONT=SolaimanLipi]ping: sendmsg: Network is unreachable[/FONT][/COLOR][COLOR=#333333][FONT=SolaimanLipi][/FONT][/COLOR][/FONT]
[COLOR=#333333][FONT=SolaimanLipi][FONT=Times New Roman][/FONT][/FONT][/COLOR]
[FONT=Times New Roman][COLOR=#333333][FONT=SolaimanLipi]ping: sendmsg: Network is unreachable[/FONT][/COLOR][COLOR=#333333][FONT=SolaimanLipi][/FONT][/COLOR][/FONT]
[COLOR=#333333][FONT=SolaimanLipi][FONT=Times New Roman][/FONT][/FONT][/COLOR]
[FONT=Times New Roman][COLOR=#333333][FONT=SolaimanLipi]ping: sendmsg: Network is unreachable[/FONT][/COLOR][COLOR=#333333][FONT=SolaimanLipi][/FONT][/COLOR][/FONT]
[COLOR=#333333][FONT=SolaimanLipi][FONT=Times New Roman][/FONT][/FONT][/COLOR]
[FONT=Times New Roman][COLOR=#333333][FONT=SolaimanLipi]ping: sendmsg: Network is unreachable[/FONT][/COLOR][COLOR=#333333][FONT=SolaimanLipi][/FONT][/COLOR][/FONT]
[COLOR=#333333][FONT=SolaimanLipi][FONT=Times New Roman][/FONT][/FONT][/COLOR]
[FONT=Times New Roman][COLOR=#333333][FONT=SolaimanLipi]ping: sendmsg: Network is unreachable[/FONT][/COLOR][COLOR=#333333][FONT=SolaimanLipi][/FONT][/COLOR][/FONT]
[COLOR=#333333][FONT=SolaimanLipi][FONT=Times New Roman][/FONT][/FONT][/COLOR]
[FONT=Times New Roman][COLOR=#333333][FONT=SolaimanLipi]ping: sendmsg: Network is unreachable[/FONT][/COLOR][COLOR=#333333][FONT=SolaimanLipi][/FONT][/COLOR][/FONT]
[COLOR=#333333][FONT=SolaimanLipi][FONT=Times New Roman][/FONT][/FONT][/COLOR]
[FONT=Times New Roman][COLOR=#333333][FONT=SolaimanLipi]64 bytes from 192.168.10.116: icmp_seq=24 ttl=64 time=0.035 ms[/FONT][/COLOR][COLOR=#333333][FONT=SolaimanLipi][/FONT][/COLOR][/FONT]
[COLOR=#333333][FONT=SolaimanLipi][FONT=Times New Roman][/FONT][/FONT][/COLOR]
[FONT=Times New Roman][COLOR=#333333][FONT=SolaimanLipi]64 bytes from 192.168.10.116: icmp_seq=25 ttl=64 time=0.042 ms[/FONT][/COLOR][COLOR=#333333][FONT=SolaimanLipi][/FONT][/COLOR][/FONT]
[COLOR=#333333][FONT=SolaimanLipi][FONT=Times New Roman][/FONT][/FONT][/COLOR]
[FONT=Times New Roman][COLOR=#333333][FONT=SolaimanLipi]64 bytes from 192.168.10.116: icmp_seq=26 ttl=64 time=0.028 ms[/FONT][/COLOR][COLOR=#333333][FONT=SolaimanLipi][/FONT][/COLOR][/FONT]
[COLOR=#333333][FONT=SolaimanLipi][FONT=Times New Roman][/FONT][/FONT][/COLOR]
[FONT=Times New Roman][COLOR=#333333][FONT=SolaimanLipi]64 bytes from 192.168.10.116: icmp_seq=27 ttl=64 time=0.026 ms[/FONT][/COLOR][COLOR=#333333][FONT=SolaimanLipi][/FONT][/COLOR][/FONT]
[COLOR=#333333][FONT=SolaimanLipi][FONT=Times New Roman][/FONT][/FONT][/COLOR]
[FONT=Times New Roman][COLOR=#333333][FONT=SolaimanLipi]64 bytes from 192.168.10.116: icmp_seq=28 ttl=64 time=0.028 ms[/FONT][/COLOR][COLOR=#333333][FONT=SolaimanLipi][/FONT][/COLOR][/FONT]
[COLOR=#333333][FONT=SolaimanLipi][FONT=Times New Roman][/FONT][/FONT][/COLOR]
[FONT=Times New Roman][COLOR=#333333][FONT=SolaimanLipi]64 bytes from 192.168.10.116: icmp_seq=29 ttl=64 time=0.040 ms[/FONT][/COLOR][COLOR=#333333][FONT=SolaimanLipi][/FONT][/COLOR][/FONT]
[COLOR=#333333][FONT=SolaimanLipi][FONT=Times New Roman][/FONT][/FONT][/COLOR]
[FONT=Times New Roman][COLOR=#333333][FONT=SolaimanLipi]64 bytes from 192.168.10.116: icmp_seq=30 ttl=64 time=0.043 ms[/FONT][/COLOR][COLOR=#333333][FONT=SolaimanLipi][/FONT][/COLOR][/FONT]
[COLOR=#333333][FONT=SolaimanLipi][FONT=Times New Roman][/FONT][/FONT][/COLOR]
[FONT=Times New Roman][COLOR=#333333][FONT=SolaimanLipi]64 bytes from 192.168.10.116: icmp_seq=31 ttl=64 time=0.031 ms[/FONT][/COLOR][COLOR=#333333][FONT=SolaimanLipi][/FONT][/COLOR][/FONT]
[COLOR=#333333][FONT=SolaimanLipi][FONT=Times New Roman][/FONT][/FONT][/COLOR]
[FONT=Times New Roman][COLOR=#333333][FONT=SolaimanLipi]64 bytes from 192.168.10.116: icmp_seq=32 ttl=64 time=0.025 ms[/FONT][/COLOR][COLOR=#333333][FONT=SolaimanLipi][/FONT][/COLOR][/FONT]
[COLOR=#333333][FONT=SolaimanLipi][FONT=Times New Roman][/FONT][/FONT][/COLOR]
[FONT=Times New Roman][COLOR=#333333][FONT=SolaimanLipi]64 bytes from 192.168.10.116: icmp_seq=33 ttl=64 time=0.045 ms[/FONT][/COLOR][COLOR=#333333][FONT=SolaimanLipi][/FONT][/COLOR][/FONT]
[COLOR=#333333][FONT=SolaimanLipi][FONT=Times New Roman][/FONT][/FONT][/COLOR]
[FONT=Times New Roman][COLOR=#333333][FONT=SolaimanLipi]64 bytes from 192.168.10.116: icmp_seq=34 ttl=64 time=0.044 ms[/FONT][/COLOR][COLOR=#333333][FONT=SolaimanLipi][/FONT][/COLOR][/FONT]
[COLOR=#333333][FONT=SolaimanLipi][FONT=Times New Roman][/FONT][/FONT][/COLOR]
[FONT=Times New Roman][COLOR=#333333][FONT=SolaimanLipi]64 bytes from 192.168.10.116: icmp_seq=35 ttl=64 time=0.029 ms[/FONT][/COLOR][COLOR=#333333][FONT=SolaimanLipi][/FONT][/COLOR][/FONT]
[COLOR=#333333][FONT=SolaimanLipi][FONT=Times New Roman][/FONT][/FONT][/COLOR]
[FONT=Times New Roman][COLOR=#333333][FONT=SolaimanLipi]64 bytes from 192.168.10.116: icmp_seq=36 ttl=64 time=0.031 ms[/FONT][/COLOR][COLOR=#333333][FONT=SolaimanLipi][/FONT][/COLOR][/FONT]
[COLOR=#333333][FONT=SolaimanLipi][FONT=Times New Roman][/FONT][/FONT][/COLOR]
[FONT=Times New Roman][COLOR=#333333][FONT=SolaimanLipi]64 bytes from 192.168.10.116: icmp_seq=37 ttl=64 time=0.031 ms[/FONT][/COLOR][COLOR=#333333][FONT=SolaimanLipi][/FONT][/COLOR][/FONT]
[COLOR=#333333][FONT=SolaimanLipi][FONT=Times New Roman][/FONT][/FONT][/COLOR]
[FONT=Times New Roman][COLOR=#333333][FONT=SolaimanLipi]64 bytes from 192.168.10.116: icmp_seq=38 ttl=64 time=0.033 ms[/FONT][/COLOR][COLOR=#333333][FONT=SolaimanLipi][/FONT][/COLOR][/FONT]
[COLOR=#333333][FONT=SolaimanLipi][FONT=Times New Roman][/FONT][/FONT][/COLOR]
[FONT=Times New Roman][COLOR=#333333][FONT=SolaimanLipi]ping: sendmsg: Network is unreachable[/FONT][/COLOR][COLOR=#333333][FONT=SolaimanLipi][/FONT][/COLOR][/FONT]
[COLOR=#333333][FONT=SolaimanLipi][FONT=Times New Roman][/FONT][/FONT][/COLOR]
[FONT=Times New Roman][COLOR=#333333][FONT=SolaimanLipi]64 bytes from 192.168.10.116: icmp_seq=40 ttl=64 time=0.044 ms[/FONT][/COLOR][COLOR=#333333][FONT=SolaimanLipi][/FONT][/COLOR][/FONT]
[COLOR=#333333][FONT=SolaimanLipi][FONT=Times New Roman][/FONT][/FONT][/COLOR]
[FONT=Times New Roman][COLOR=#333333][FONT=SolaimanLipi]64 bytes from 192.168.10.116: icmp_seq=41 ttl=64 time=0.044 ms[/FONT][/COLOR][COLOR=#333333][FONT=SolaimanLipi][/FONT][/COLOR][/FONT]
[COLOR=#333333][FONT=SolaimanLipi][FONT=Times New Roman][/FONT][/FONT][/COLOR]
[FONT=Times New Roman][COLOR=#333333][FONT=SolaimanLipi]64 bytes from 192.168.10.116: icmp_seq=42 ttl=64 time=0.027 ms[/FONT][/COLOR][COLOR=#333333][FONT=SolaimanLipi][/FONT][/COLOR][/FONT]
[COLOR=#333333][FONT=SolaimanLipi][FONT=Times New Roman][/FONT][/FONT][/COLOR]
[FONT=Times New Roman][COLOR=#333333][FONT=SolaimanLipi]64 bytes from 192.168.10.116: icmp_seq=43 ttl=64 time=0.031 ms[/FONT][/COLOR][COLOR=#333333][FONT=SolaimanLipi][/FONT][/COLOR][/FONT]
[COLOR=#333333][FONT=SolaimanLipi][FONT=Times New Roman][/FONT][/FONT][/COLOR]
[FONT=Times New Roman][COLOR=#333333][FONT=SolaimanLipi]64 bytes from 192.168.10.116: icmp_seq=44 ttl=64 time=0.031 ms[/FONT][/COLOR][COLOR=#333333][FONT=SolaimanLipi][/FONT][/COLOR][/FONT]
[COLOR=#333333][FONT=SolaimanLipi][FONT=Times New Roman][/FONT][/FONT][/COLOR]
[FONT=Times New Roman][COLOR=#333333][FONT=SolaimanLipi]64 bytes from 192.168.10.116: icmp_seq=45 ttl=64 time=0.030 ms[/FONT][/COLOR][COLOR=#333333][FONT=SolaimanLipi][/FONT][/COLOR][/FONT]
[COLOR=#333333][FONT=SolaimanLipi][FONT=Times New Roman][/FONT][/FONT][/COLOR]
[FONT=Times New Roman][COLOR=#333333][FONT=SolaimanLipi]ping: sendmsg: Network is unreachable[/FONT][/COLOR][COLOR=#333333][FONT=SolaimanLipi][/FONT][/COLOR][/FONT]
[COLOR=#333333][FONT=SolaimanLipi][FONT=Times New Roman][/FONT][/FONT][/COLOR]
[FONT=Times New Roman][COLOR=#333333][FONT=SolaimanLipi]ping: sendmsg: Network is unreachable[/FONT][/COLOR][COLOR=#333333][FONT=SolaimanLipi][/FONT][/COLOR][/FONT]
[COLOR=#333333][FONT=SolaimanLipi][FONT=Times New Roman][/FONT][/FONT][/COLOR]
[FONT=Times New Roman][COLOR=#333333][FONT=SolaimanLipi]64 bytes from 192.168.10.116: icmp_seq=48 ttl=64 time=0.044 ms[/FONT][/COLOR][COLOR=#333333][FONT=SolaimanLipi][/FONT][/COLOR][/FONT]
[COLOR=#333333][FONT=SolaimanLipi][FONT=Times New Roman][/FONT][/FONT][/COLOR]
[FONT=Times New Roman][COLOR=#333333][FONT=SolaimanLipi]64 bytes from 192.168.10.116: icmp_seq=49 ttl=64 time=0.053 ms[/FONT][/COLOR][COLOR=#333333][FONT=SolaimanLipi][/FONT][/COLOR][/FONT]
[COLOR=#333333][FONT=SolaimanLipi][FONT=Times New Roman][/FONT][/FONT][/COLOR]
[FONT=Times New Roman][COLOR=#333333][FONT=SolaimanLipi]64 bytes from 192.168.10.116: icmp_seq=50 ttl=64 time=0.044 ms[/FONT][/COLOR][COLOR=#333333][FONT=SolaimanLipi][/FONT][/COLOR][/FONT]
[COLOR=#333333][FONT=SolaimanLipi][FONT=Times New Roman][/FONT][/FONT][/COLOR]
[FONT=Times New Roman][COLOR=#333333][FONT=SolaimanLipi]^C[/FONT][/COLOR][COLOR=#333333][FONT=SolaimanLipi][/FONT][/COLOR][/FONT]
[COLOR=#333333][FONT=SolaimanLipi][FONT=Times New Roman][/FONT][/FONT][/COLOR]
[FONT=Times New Roman][COLOR=#333333][FONT=SolaimanLipi]--- 192.168.10.116 ping statistics ---[/FONT][/COLOR][COLOR=#333333][FONT=SolaimanLipi][/FONT][/COLOR][/FONT]
[COLOR=#333333][FONT=SolaimanLipi][FONT=Times New Roman][/FONT][/FONT][/COLOR]
[FONT=Times New Roman][COLOR=#333333][FONT=SolaimanLipi]50 packets transmitted, 37 received, 26% packet loss, time 49069ms[/FONT][/COLOR][COLOR=#333333][FONT=SolaimanLipi][/FONT][/COLOR][/FONT]
[COLOR=#333333][FONT=SolaimanLipi][FONT=Times New Roman][/FONT][/FONT][/COLOR]
[FONT=Times New Roman][COLOR=#333333][FONT=SolaimanLipi]rtt min/avg/max/mdev = 0.025/0.035/0.053/0.009 ms[/FONT][/COLOR][COLOR=#333333][FONT=SolaimanLipi][/FONT][/COLOR][/FONT]
[COLOR=#333333][FONT=SolaimanLipi][FONT=Times New Roman][/FONT][/FONT][/COLOR]
[COLOR=#333333][FONT=SolaimanLipi][FONT=Times New Roman]shahan@shahan-desktop:~$ [/FONT][/FONT][/COLOR][COLOR=#333333][FONT=SolaimanLipi][/FONT][/COLOR]
[COLOR=#333333][FONT=SolaimanLipi][/FONT][/COLOR]

```

---

### Post by pinenut on 2009-11-10
Iv'e just installed Ubuntu 9.10 and configured the network by following these steps. I suggest you try to do the same.

System > Preferences > Network Connections > Auto eth0 > Edit > IPv4 Setting tab

From this window, you manually set the IP address.

---

### Post by shahan on 2009-11-10
> **pinenut said:**
> Iv'e just installed Ubuntu 9.10 and configured the network by following these steps. I suggest you try to do the same.
 
System > Preferences > Network Connections > Auto eth0 > Edit > IPv4 Setting tab
 
From this window, you manually set the IP address.
Yes...I know this procedure very well...Which I said in my earlier posts..
My problem is that, it works for everyone except me. I also described in my previous post about how I connect to Internet on WINDOWS XP...

---

### Post by shahan on 2009-11-18
My problem solved.
I have used this code
```
sudo mii-tool -F 10baseT-FD
``` in terminal

---

### Post by Goodlooking on 2009-11-18
I have manually set up my internet connection threw a usb port, and it says I am connected , but I can't navigate, I am on my desktop right now and Karmic is on my laptop. I tried the last sudo mi-tool -F 10baseT-FD but it says SIOCGMIIPHY on eth2 failed, I have no eth2 connection, eth1 is the only one i have set up.

---

### Post by shahan on 2009-11-19
> **Goodlooking said:**
> I have manually set up my internet connection threw a usb port, and it says I am connected , but I can't navigate, I am on my desktop right now and Karmic is on my laptop. I tried the last sudo mi-tool -F 10baseT-FD but it says SIOCGMIIPHY on eth2 failed, I have no eth2 connection, eth1 is the only one i have set up.
you should post your problem in a new thread. then it would be easier to help you..

---

### Post by Zintha on 2010-03-12
> **Thorstien78 said:**
> I had a similar problem. this worked for me. go to Applications/Terminal and type 
**sudo dhclient eth0**
 
here is where i found it [http://ubuntuforums.org/archive/index.php/t-994525.html](http://ubuntuforums.org/archive/index.php/t-994525.html)
 
2 hour issue. 2 second fix.
Thank you.
 
Ubuntu 9.10, Wired worked, reset and it stopped working. Spent 2 hours searching forums and google for fix, did 7 different solutions and this fixes it.
 
For all the fustration Ubuntu causes, it has beautifully simplistic fixes. I hope i'll eventually learn some of these handy commands in time hopefully!

---

### Post by shahan on 2010-12-30
I am facing the problem again. Tried all the things again in my system. But not getting the connection ...

my windows "ipconfig" output

```


Windows IP Configuration



        Host Name . . . . . . . . . . . . : SHAHI

        Primary Dns Suffix  . . . . . . . : 

        Node Type . . . . . . . . . . . . : Unknown

        IP Routing Enabled. . . . . . . . : Yes

        WINS Proxy Enabled. . . . . . . . : No



Ethernet adapter Local Area Connection:



        Connection-specific DNS Suffix  . : 

        Description . . . . . . . . . . . : Realtek RTL8139 Family PCI Fast Ethernet NIC

        Physical Address. . . . . . . . . : 00-24-1D-92-D3-C4

        Dhcp Enabled. . . . . . . . . . . : No

        IP Address. . . . . . . . . . . . : 192.168.10.93

        Subnet Mask . . . . . . . . . . . : 255.255.255.0

        Default Gateway . . . . . . . . . : 192.168.10.1

        DNS Servers . . . . . . . . . . . : 8.8.8.8

                                            4.2.2.3


```

---

### Post by Elfy on 2010-12-30
Shahan - I'd start another thread and refer to this.

This is old now.

---

