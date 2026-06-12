---
title: "Connects to Wireless Router but not internet"
date: 2009-07-09
forum: Networking &amp; Wireless
---

### Post by juanfernandes on 2009-07-09
Hi everyone.

I have searched the forum for a similar issue to what im having, but ive had not luck. 

Right, I have installed Ubuntu 9.04 dual booting with Windows Vista. 

At home, I can see my wireless connection, I can connect to it but I cannot get any internet access. 

At work, I can connect to the hidden wireless network and I get internet access. This leads me to believe the problem is with my home routers configuration.

Both home and work routers are configured to allow DHCP connections. 

Any ideas?

Thanks in advance.

Juan

---

### Post by zyxuvius on 2009-07-09
I'm having similar problems. Tuesday, I reformatted and partitioned an old computer. I dual mounted hardy 8.04 and Windows XP. Then I took a wireless card off of another old computer, and put it on my ubuntu/Windows computer. After searching the internet for 5 hours, I finally found a working driver for it. Firefox worked fine in windows, but I couldn't get it to work in ubuntu.

So yesterday evening, I finally found out that I needed ndiswrapper. I just got that working, but I haven't been able to get a module to work. I punched in all of the information under Network Settings. I know I'm close, but I don't know what I need to do to get firefox to work on my ubuntu partition.

If anybody can help me too, that would be great!

---

### Post by gpsmikey on 2009-07-09
If you can connect to the router, but not the internet, my first suspicion would be the router is configured to only allow connections to the internet by MAC address and you have not entered the address of your machine (or card) into that table.  Been there, done that one :lolflag:

mikey

---

### Post by superprash2003 on 2009-07-10
post output of the following from the terminal
1)ifconfig
2)ping 208.67.222.222
3)ping google.com 

are you able to access your router?

---

### Post by juanfernandes on 2009-07-10
> **gpsmikey said:**
> If you can connect to the router, but not the internet, my first suspicion would be the router is configured to only allow connections to the internet by MAC address and you have not entered the address of your machine (or card) into that table.  Been there, done that one :lolflag:

mikey

Hi Mikey

Thanks for the reply. 

I thought that too, as at some point I had enabled MAC addresses on the router, but when I checked it was disabled, so just relies on the WPA key. 

Thanks anyway

Juan

---

### Post by juanfernandes on 2009-07-10
> **superprash2003 said:**
> post output of the following from the terminal
1)ifconfig
2)ping 208.67.222.222
3)ping google.com 

are you able to access your router?

Hi superprash2003

Thanks for the reply. I will try that later when I get home. 

No I am unable to connect to the router, although, sometimes, the login window comes up, but i enter my credentials and nothing happens. 

Thanks
Juan

---

### Post by juanfernandes on 2009-07-13
> **superprash2003 said:**
> post output of the following from the terminal
1)ifconfig
2)ping 208.67.222.222
3)ping google.com 

are you able to access your router?

Hi,

Bellow are the results from the above:

ifconfig

eth0      Link encap:Ethernet  HWaddr 00:1e:8c:e9:86:08  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 Base address:0xc800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:16:44:a9:86:f6  
          inet addr:192.168.1.10  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:44ff:fea9:86f6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:35 errors:0 dropped:0 overruns:0 frame:0
          TX packets:38 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3797 (3.7 KB)  TX bytes:5627 (5.6 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-16-44-A9-86-F6-36-66-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


ping 208.67.222.222
PING 208.67.222.222 (208.67.222.222) 56(84) bytes of data.
From 192.168.1.10 icmp_seq=10 Destination Host Unreachable
From 192.168.1.10 icmp_seq=11 Destination Host Unreachable
From 192.168.1.10 icmp_seq=12 Destination Host Unreachable
From 192.168.1.10 icmp_seq=13 Destination Host Unreachable
From 192.168.1.10 icmp_seq=14 Destination Host Unreachable
From 192.168.1.10 icmp_seq=15 Destination Host Unreachable
From 192.168.1.10 icmp_seq=16 Destination Host Unreachable
From 192.168.1.10 icmp_seq=17 Destination Host Unreachable

Hope that helps someone help me!

Thanks
Juan

---

### Post by Silverdagger on 2009-07-13
hmm... What do u get when u type: iwconfig

in the terminal?

---

### Post by juanfernandes on 2009-07-13
> **Silverdagger said:**
> hmm... What do u get when u type: iwconfig

in the terminal?

I'll try that this evening when I get home from work. 

This might be a bit of a noob question, but could this be something my ISP has done? 

My ISP is Sky, they provided the router, which has their custom software. 

Juan

---

### Post by superprash2003 on 2009-07-13
hmm.. is 192.168.1.1 your router's ip?? are you able to access and ping that?post output of **route -n**

---

### Post by juanfernandes on 2009-07-14
> **juanfernandes said:**
> I'll try that this evening when I get home from work. 

This might be a bit of a noob question, but could this be something my ISP has done? 

My ISP is Sky, they provided the router, which has their custom software. 

Juan

Results from iwconfig

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"IntraSite Network"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:14:6C:69:B3:E4   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=82/100  Signal level:-30 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

---

### Post by juanfernandes on 2009-07-14
> **superprash2003 said:**
> hmm.. is 192.168.1.1 your router's ip?? are you able to access and ping that?post output of **route -n**

Results of route -n

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     2      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
0.0.0.0         192.168.1.254   0.0.0.0         UG    0      0        0 wlan0

No, my router IP is 192.168.1.254. And I think you meant 192.168.1.10, thats my laptops IP address. 

Thanks

Juan

---

### Post by superprash2003 on 2009-07-14
are you able to access [http://192.168.1.254?](http://192.168.1.254?)

---

### Post by juanfernandes on 2009-07-14
> **superprash2003 said:**
> are you able to access [http://192.168.1.254?](http://192.168.1.254?)

I wasnt able to, until last night, when I decided I was going to plug it into the router and as I got closer to the router it connected, I was then able to get to the router config, but I couldnt ping onto to the internet.

It's not a weak signal, because it had a strong signal when I was trying it before.

I'm really annoyed, this is the fourth version of Ubuntu I have tried and I still cant get rid of Vista for good!

I might go home and reset my router back to defaults - wondering if its something I have done on the router that might be affecting the connection.

Juan

---

### Post by superprash2003 on 2009-07-14
try this , in your terminal type
1)sudo ifdown eth0
2)sudo ifdown wmaster0 

now try accessing

---

### Post by martinbaselier on 2009-07-14
ifdown Is used to turn off a network connection. Why would you advise him to do that?

The problem will almost certainly be some setting in the router, since your internet connection is fine on your work. You can also connect to the router, but the router blocks your access to the outside world.

Strange though that it works on vista. What channel do you use for wireless? (1,7 and 11 usually seem to work best.)

If you reset your router, I'd advice you to begin without any security, no mac-filtering, no encryption (WPA/WEP), no firewall, no NAT on the router. If it works turn on the security options you want to use, one by one, and test if you still have a working connection.

---

### Post by superprash2003 on 2009-07-15
he is only using the wlan0 interface , so bringing down the other interfaces temporarily will let us know better where the problem is.. ifdown is not permanent , it will be up again when rebooted or when networking is restarted..

---

### Post by juanfernandes on 2009-07-20
> **superprash2003 said:**
> try this , in your terminal type
1)sudo ifdown eth0
2)sudo ifdown wmaster0 

now try accessing

Hi, sorry it has taken me a while to reply, ive been quite busy. I tried what you suggested:

----ifdown-----

username@ubuntu:~$ sudo ifdown eth0

[sudo] password for username: 
ifdown: interface eth0 not configured


username@ubuntu:~$ sudo ifdown wmaster0

ifdown: interface wmaster0 not configured


----PING-----

username@ubuntu:~$ ping google.com

PING google.com (74.125.45.100) 56(84) bytes of data.

64 bytes from yx-in-f100.google.com (74.125.45.100): icmp_seq=3 ttl=53 time=178 ms

64 bytes from yx-in-f100.google.com (74.125.45.100): icmp_seq=14 ttl=53 time=180 ms

64 bytes from yx-in-f100.google.com (74.125.45.100): icmp_seq=15 ttl=53 time=179 ms

64 bytes from 74.125.45.100: icmp_seq=22 ttl=53 time=182 ms

From ubuntu.local (192.168.1.11) icmp_seq=59 Destination Host Unreachable

From ubuntu.local (192.168.1.11) icmp_seq=60 Destination Host Unreachable

From ubuntu.local (192.168.1.11) icmp_seq=73 Destination Host Unreachable

From ubuntu.local (192.168.1.11) icmp_seq=74 Destination Host Unreachable

From ubuntu.local (192.168.1.11) icmp_seq=75 Destination Host Unreachable

From ubuntu.local (192.168.1.11) icmp_seq=76 Destination Host Unreachable

From ubuntu.local (192.168.1.11) icmp_seq=77 Destination Host Unreachable

From ubuntu.local (192.168.1.11) icmp_seq=81 Destination Host Unreachable

From ubuntu.local (192.168.1.11) icmp_seq=82 Destination Host Unreachable

From ubuntu.local (192.168.1.11) icmp_seq=83 Destination Host Unreachable

64 bytes from 74.125.45.100: icmp_seq=87 ttl=53 time=187 ms

64 bytes from 74.125.45.100: icmp_seq=89 ttl=53 time=174 ms

64 bytes from 74.125.45.100: icmp_seq=91 ttl=53 time=187 ms

64 bytes from 74.125.45.100: icmp_seq=96 ttl=53 time=176 ms

64 bytes from yx-in-f100.google.com (74.125.45.100): icmp_seq=110 ttl=53 time=1195 ms

64 bytes from yx-in-f100.google.com (74.125.45.100): icmp_seq=112 ttl=53 time=190 ms

64 bytes from 74.125.45.100: icmp_seq=115 ttl=53 time=177 ms

64 bytes from yx-in-f100.google.com (74.125.45.100): icmp_seq=119 ttl=53 time=181 ms


^C
--- google.com ping statistics ---
132 packets transmitted, 12 received, +10 errors, 90% packet loss, time 332482ms
rtt min/avg/max/mdev = 

174.272/265.894/1195.034/280.185 ms, pipe 4

So after doing that, I was partly able to access the internet, although it was very limited and very slow. 

I tried accessing google.com and it never reached it, but then I tried google.co.uk and I was able to access it and also access gmail, but I wasnt able to send emails.

This is sounding like a DNS issue now. Is that a correct assumption? 

Juan

---

### Post by martinbaselier on 2009-07-20
> he is only using the wlan0 interface , so bringing down the other interfaces temporarily will let us know better where the problem is.. ifdown is not permanent , it will be up again when rebooted or when networking is restarted..

That's true, but wmaster0 is a virtual interface created for wlan0. So shutting that down is probably not going to do much good. And as long as there's no cable connected eth0 will not have any influence.

Also sudo ifconfig eth0 down would be the better choice in this case, it will bring down the interface on driver level. ifdown/ifup are used for devices configured in /etc/network/interfaces, if I understand the manuals correctly.

---

### Post by martinbaselier on 2009-07-20
It doesn't look like a dns problem to me. It seems you loose your connection a lot. But I could be wrong. You could test, by using the ip address of google directly and ping the ip. 
ping 74.125.45.100

If it can't reach the address that way either, it's not a dns problem, otherwise it probably is. You could try using the opendns service then, their dns servers are: 208.67.222.222 and 208.67.220.220

I'd also advise you to check iwconfig wlan0 several times, to see if the strength is constant or variable. 

also **ping 192.168.1.254** will show you if there's any problem between the laptop and the router. If that's ok, you would need to check your router's setting.

---

