---
title: "ndiswrapper connected but web pages won't load"
date: 2009-03-07
forum: Networking &amp; Wireless
---

### Post by initialised on 2009-03-07
Hi. I am new to Ubuntu and have been trying to get my wireless external usb netgear WG111v3 adaptor to work. I have installed ndiswrapper with the appropriate .inf file. The network manager icon on the menu bar (next to volume control) says that I am connected. I also typed in the 

-----------------------------------------------------
lshw -C network 
------------------------------------------------------

command to check that it is correctly installed and it was confirmed. The problem is, though, that I can't get any web pages to load and it displays the message "...server not found" etc. At first I thought that it was maybe a signal strength problem as there are always only one or two bars filled on the network manager icon. So I moved the computer close to the router but this did not solve anything. If somebody could please, please help me with this I'd really appreciate it :)

---

### Post by underage on 2009-03-07
Yo!

Well the information u gave doesn't help much.

Anyways, what's your gateway ?

Run ifconfig to check if the gateway and dns were allocated to the card.

Ping both gateway | dns to check for connection.

if they reply (without losses) ping a website (ex: ping [www.google.com](www.google.com)) you get something like:

ping [www.google.com](www.google.com)

PING [www.l.google.com](www.l.google.com) (**209.85.153.104**) 56(84) bytes of data.
64 bytes from im-in-f104.google.com (209.85.153.104): icmp_seq=1 ttl=128 time=77.3 ms
--- [www.l.google.com](www.l.google.com) ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 30ms

And post the results here.

Holla

Underage

---

### Post by ugm6hr on 2009-03-07
Give the output from these commands (use a USB stick to copy / paste):

```
route -n
ifconfig
iwconfig
```

If you know the IP address of your router:
```
ping router_ipaddress
```

Also:
```
ping www.opendns.com
ping 208.67.219.101
```

---

### Post by initialised on 2009-03-07
Hey underage. Thanks for responding. Here are the results of what you asked for:

 ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:13:d3:15:f4:ad  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
          Interrupt:18 Base address:0x8c00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:250 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:250 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:15768 (15.7 KB)  TX bytes:15768 (15.7 KB) 

wlan0     Link encap:Ethernet  HWaddr 00:1e:2a:b5:d0:24  
          inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0 
          inet6 addr: fe80::21e:2aff:feb5:d024/64 Scope:Link 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:39 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:4574 (4.5 KB) 


ping [www.google.com](www.google.com) 
ping: unknown host [www.google.com](www.google.com) 

I should add that I picked up the .inf and .sys file from this website: [http://en.opensuse.org/SDB:WG111v3](http://en.opensuse.org/SDB:WG111v3) and that I installed it via the GUI.

thanks again;)

---

### Post by ugm6hr on 2009-03-07
Looks like you have an assigned IP.

How about those commands I suggested?

---

### Post by initialised on 2009-03-07
Hi ugm6hr. Thanks for the advice. Here is the information:

  route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     2      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
0.0.0.0         192.168.1.254   0.0.0.0         UG    0      0        0 wlan0



ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:13:d3:15:f4:ad  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
          Interrupt:18 Base address:0x8c00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:250 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:250 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:15768 (15.7 KB)  TX bytes:15768 (15.7 KB) 

wlan0     Link encap:Ethernet  HWaddr 00:1e:2a:b5:d0:24  
          inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0 
          inet6 addr: fe80::21e:2aff:feb5:d024/64 Scope:Link 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:39 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:4574 (4.5 KB) 


 iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"amanda"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:1D:92:C2:07:F1   
          Bit Rate=54 Mb/s   Tx-Power:20 dBm   Sensitivity=0/3  
          RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:39/100  Signal level:-71 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

 ping router_192.168.1.101
ping: unknown host router_192.168.1.101

 
ping [www.opendns.com](www.opendns.com)
ping: unknown host [www.opendns.com](www.opendns.com)

ping 208.67.219.101
PING 208.67.219.101 (208.67.219.101) 56(84) bytes of data.
From 192.168.1.102 icmp_seq=1 Destination Host Unreachable
From 192.168.1.102 icmp_seq=2 Destination Host Unreachable
From 192.168.1.102 icmp_seq=3 Destination Host Unreachable
From 192.168.1.102 icmp_seq=4 Destination Host Unreachable
From 192.168.1.102 icmp_seq=5 Destination Host Unreachable
From 192.168.1.102 icmp_seq=6 Destination Host Unreachable
From 192.168.1.102 icmp_seq=8 Destination Host Unreachable
From 192.168.1.102 icmp_seq=9 Destination Host Unreachable
From 192.168.1.102 icmp_seq=10 Destination Host Unreachable
From 192.168.1.102 icmp_seq=12 Destination Host Unreachable
From 192.168.1.102 icmp_seq=13 Destination Host Unreachable
From 192.168.1.102 icmp_seq=14 Destination Host Unreachable
From 192.168.1.102 icmp_seq=16 Destination Host Unreachable
From 192.168.1.102 icmp_seq=17 Destination Host Unreachable
From 192.168.1.102 icmp_seq=18 Destination Host Unreachable
From 192.168.1.102 icmp_seq=20 Destination Host Unreachable
From 192.168.1.102 icmp_seq=21 Destination Host Unreachable
From 192.168.1.102 icmp_seq=22 Destination Host Unreachable
From 192.168.1.102 icmp_seq=24 Destination Host Unreachable
From 192.168.1.102 icmp_seq=25 Destination Host Unreachable
From 192.168.1.102 icmp_seq=26 Destination Host Unreachable
^C
--- 208.67.219.101 ping statistics ---
28 packets transmitted, 0 received, +21 errors, 100% packet loss, time 27064ms
, pipe 3

I was worried that perhaps I had picked up the wrong .inf and .sys files. I got it from [http://en.opensuse.org/SDB:WG111v3](http://en.opensuse.org/SDB:WG111v3) because I have struggled to connect to the ndiswrapper site to retrieve it from there. Could that perhaps be the problem? Like I mentioned to underage - I installed ndiswrapper and the .inf file from the gui.

thanks for helping  ;)

---

### Post by ugm6hr on 2009-03-07
Try this:
```
ping -c 3 192.168.1.254
ping -c 3 192.168.1.101
```

---

### Post by ministoat on 2009-03-07
sorry to hop in but i'm trying to set the exact same usb wpa connection as you :)

i can't ping my routers address either (192.168.1.254)

i've noticed that the light on hte netgear is not flashing at all and is just steady - i've tried reconnecting it and that hasn't helped: i know that usually it flashes during network activity.

---

### Post by initialised on 2009-03-07
Hi againn  :)

This is what happened:

 ping -c 3 192.168.1.254
PING 192.168.1.254 (192.168.1.254) 56(84) bytes of data.
From 192.168.1.102 icmp_seq=1 Destination Host Unreachable
From 192.168.1.102 icmp_seq=2 Destination Host Unreachable
From 192.168.1.102 icmp_seq=3 Destination Host Unreachable

--- 192.168.1.254 ping statistics ---
3 packets transmitted, 0 received, +3 errors, 100% packet loss, time 1999ms
, pipe 3


 ping -c 3 192.168.1.101
PING 192.168.1.101 (192.168.1.101) 56(84) bytes of data.
From 192.168.1.102 icmp_seq=1 Destination Host Unreachable
From 192.168.1.102 icmp_seq=2 Destination Host Unreachable
From 192.168.1.102 icmp_seq=3 Destination Host Unreachable

--- 192.168.1.101 ping statistics ---
3 packets transmitted, 0 received, +3 errors, 100% packet loss, time 2012ms
, pipe 3

---

### Post by ministoat on 2009-03-07
how's the light on your usb, is it flashing or steady?

---

### Post by initialised on 2009-03-07
Hi.  Yep, also steady, no flickering at all.   :(

---

### Post by ministoat on 2009-03-07
I also just tried with WEP/WPA2/no security and couldn't connect on any of them, but had a few pings run through successfully for some reason :/

---

### Post by ugm6hr on 2009-03-07
Try turning off all wifi security.

[http://ubuntuforums.org/showthread.php?t=802122](http://ubuntuforums.org/showthread.php?t=802122)

---

### Post by initialised on 2009-03-07
I tried doing that but it made no difference - still get the "can't find server" message  :(

---

### Post by ministoat on 2009-03-08
I'm not able to try this right now, but i found this post so maybe it would be of use to you:

[http://ubuntuforums.org/archive/index.php/t-896493.html](http://ubuntuforums.org/archive/index.php/t-896493.html)

---

### Post by initialised on 2009-03-08
Hi ministoat,

Thanks for the link! I have seen it before but couldn't use it because I do not have the network manager in my SYSTEM<ADMINISTRATION menu so cannot adjust the roaming option. Any idea why this might be? Or how I might fix it? Thanks in advance  :)

---

### Post by ministoat on 2009-03-09
sorry to disappoint but i really don't have a clue how you'd reinstall network manager :(

---

### Post by initialised on 2009-03-12
Hey ministoat,

thanks for replying, anyway. good luck with getting your internet connection to work.

---

