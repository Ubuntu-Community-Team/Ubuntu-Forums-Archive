---
title: "Ubuntu not connecting to router"
date: 2009-10-14
forum: Networking &amp; Wireless
---

### Post by nicohasa on 2009-10-14
Hey peoples!

Installed ubuntu on my computer some weeks ago now, been running smoothly, 'till a few days ago.

Suddenly, ubuntu won't connect to my router anymore. Vista connects with no problems, as do other computers, and ubuntu connects with no problems to other wireless networks.

Can't think of anything I've done that has caused this...

Halp plix?

Running dualboot Vista/Ubuntu 9.04

Edit:
Oh, and the router in question is a Netgear WGR614v9

---

### Post by hal10000 on 2009-10-14
Can you see your accesspoint in network-manager (or whatever tool you are using to connect to your wireless network)? Did you check if you accidently deleted your wireless-key or other settings.
Do you use a static ip or dhcp?
Are your nameserver entries correct?

You can post the output of the commands
iwconfig
ifconfig
and route
so we can see what's going wrong.

---

### Post by nicohasa on 2009-10-14
> **hal10000 said:**
> Can you see your accesspoint in network-manager (or whatever tool you are using to connect to your wireless network)? Did you check if you accidently deleted your wireless-key or other settings.
Do you use a static ip or dhcp?
Are your nameserver entries correct?

You can post the output of the commands
iwconfig
ifconfig
and route
so we can see what's going wrong.

I can see the accesspoint, have deleted and re-created the wireless-key a bunch of times. I have checked to see if I've got the correct password (WEP2-password, by the way). I'm currently connected to the router through a wire, works like a charm.
Have DHCP, and here is the output of the different commands:

iwconfig:

```
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:"Spindelvevet"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:1F:33:B7:E1:6E   
          Bit Rate=1 Mb/s   Tx-Power=15 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=100/100  Signal level:-20 dBm  Noise level=-127 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.
```

ifconfig:

```
eth0      Link encap:Ethernet  HWaddr 00:1e:68:a2:76:59  
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:68ff:fea2:7659/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:520 errors:0 dropped:0 overruns:0 frame:0
          TX packets:466 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:549762 (549.7 KB)  TX bytes:107956 (107.9 KB)
          Interrupt:247 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:16:ea:82:2f:6e  
          inet6 addr: fe80::216:eaff:fe82:2f6e/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:498 (498.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-16-EA-82-2F-6E-66-36-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```

route:

```
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     1      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0
default         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
```

---

### Post by hal10000 on 2009-10-14
I guess the essid "Spindelvevet" as shown in your iwconfig output is the one you want to get connected to and your dhcp server is located on your router.
It's strange that you get an ip-address when connected via ethernet, but none if you connect via wireless (i suppose the wireless-accesspoint and your router is the same device).

I recommend you set up your wireless with a static ip-address (use the same as your eth0 (ip:192.168.1.4 Broadcast:192.168.1.255 Netmask:255.255.255.0 gateway:192.168.1.1 and nameserver the same address as you can see in /etc/resolv.conf).
Disconnect your ethernet cable before you use the new wireless configuration.


I'm sorry to have no better idea.

[EDIT]
If you don't get a connection this way then there are only two things i can imagine:

1. Something must be wrong with your WPA settings (i know you checked it again and again) or
2. your nameserver ip-address is wrong or missing

You can test the second case with ping command
1. ping [www.google.com](www.google.com) (you will probably get no positive answer)
2. ping 74.125.39.106 (this is the ip-address of the google webserver, if you get a positive answer here, then you have definitely a nameserver problem

[EDIT]
Which network-connection program do you use? If it's network-manager, you should give wicd instead a try, it's much better than network-manager.

---

### Post by nicohasa on 2009-10-15
Ok, tried Wicd, and although I did prefer that to the network-manager, it didn't help solve the problem.

It's not a nameserver problem, didn't seem to help with a static IP, and wicd gets stuck at "Validating Authentication".

Can there be a problem where, since the password is in normal text, the text-to-hex-windows-to-unix or something royally buggers up everything?

Edit:
Tried removing the security on the network. Didn't work diddly-squat. Still stuck at "Validating Authentication"...

Doubleedit:
Restarted ubuntu after installing wicd, suddenly everything works like a charm, weird, as I haven't changed anything, but who am I to complain :D

Thanks a lawt for the help!

---

