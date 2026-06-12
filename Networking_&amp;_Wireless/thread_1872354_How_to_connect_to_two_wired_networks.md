---
title: "How to connect to two wired networks"
date: 2011-10-30
forum: Networking &amp; Wireless
---

### Post by cogitordi on 2011-10-30
I have Ubuntu (10.04 LTS) on a PC with two network ports. Both ports work.

I have two LANs: LAN A has the Internet connection (through a router/switch), and LAN B has a router/switch with no WAN connection; LAN B has access to my files on NAS. I keep them separate for security.

I have an M-Windows box that is connected to both networks. To make the box see both networks, the network port connected to LAN B has a static IP address and no gateway is specified. 

So I know how to achieve my goal with M-Windows, but I can't make it work in Linux. IFCONFIG shows that I have eth0 and eth1 for LAN A and LAN B; I do have Internet access through LAN A; the network port for LAN B shows a valid address. But I can't see the devices on LAN B. 

I've tried editing /etc/network/interfaces to specify a static IP for LAN B, then restarting init.d. Nothing seems to work.

Is it just my ignorance or is this really a difficult thing to accomplish?

---

### Post by Jonathan L on 2011-10-30
> **cogitordi said:**
>  IFCONFIG shows that I have eth0 and eth1 for LAN A and LAN B; I do have Internet access through LAN A; the internet [[COLOR=Red]ethernet?[/COLOR]] port for LAN B shows a valid address. But I can't see the devices on LAN B. 

Hi

It's a perfectly reasonable thing to do and quite common.  It's normally straightfoward unless you have overlapping network addressing.  The only thing at all unusual is you say that the non-WAN network B has a router/switch attached to it: I presume it's an ADSL router with no ADSL plugged in, so it behaves just as an ethernet switch?

What addresses are you using, and how are you doing your name resolution for the NAS devices?  I'd check your routes on your Ubuntu machine, and try pinging them by number, if you haven't already done so.

Also: are you running 10.04 server or desktop?

Kind regards,
Jonathan.

---

### Post by cogitordi on 2011-10-30
> **Jonathan L said:**
> The only thing at all unusual is you say that the non-WAN network B has a router/switch attached to it: I presume it's an ADSL router with no ADSL plugged in, so it behaves just as an ethernet switch?

Correct, it is a modem-router with no WAN. I'm using it to serve IP addresses (DHCP) to a number of NAS devices. It is at 10.0.0.1.

> try pinging them by number

PING to 10.0.0.1 fails (no successful delivery of packets).

> Also: are you running 10.04 server or desktop?

It's the desktop version, 64b. 

My LAN A router is at 192.168.1.1. 

The ROUTE command shows everything that I've described.

---

### Post by Jonathan L on 2011-10-30
Hi again Cogito

With LAN A having 10.0.1.1 and LAN B having 10.0.0.1 my guess would be to check the netmasks on both sides.  After that I'd check link lights.  After that I'd try tcpdump or wireshark to see if my packets were going out the wrong port.

Hope that's helpful.

Kind regards,
Jonathan.

---

### Post by cogitordi on 2011-10-30
LAN A is 192.168.1.0 (WAN)
LAN B is 10.0.0.0

---

### Post by Jonathan L on 2011-10-30
> **cogitordi said:**
> LAN A is 192.168.1.0 (WAN)
LAN B is 10.0.0.0

Hi ..

(192.168.1.1: sorry. I did misread it.)

Are you quite certain you're getting any packets at all out of the LAN B?  Would you post the results of
```
ifconfig
netstat -rn
ping -w 2 10.0.0.thisbox
ping -w 2 192.168.1.thisbox
```(for thisbox use the machine's own numbers).

What you've described is completely sensible: I'd be double checking the obvious things.

Kind regards,
Jonathan.

---

### Post by cogitordi on 2011-10-30
netstat -rn
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
10.0.0.0        0.0.0.0         255.255.255.0   U         0 0          0 eth1
192.168.1.0     0.0.0.0         255.255.255.0   U         0 0          0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U         0 0          0 eth1
0.0.0.0         192.168.1.1     0.0.0.0         UG        0 0          0 eth0
```

ping -w 2 10.0.0.31
```
PING 10.0.0.31 (10.0.0.31) 56(84) bytes of data.
64 bytes from 10.0.0.31: icmp_seq=1 ttl=64 time=0.058 ms
64 bytes from 10.0.0.31: icmp_seq=2 ttl=64 time=0.050 ms
64 bytes from 10.0.0.31: icmp_seq=3 ttl=64 time=0.045 ms

--- 10.0.0.31 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 1998ms
rtt min/avg/max/mdev = 0.045/0.051/0.058/0.005 ms

ping -w 2 192.168.1.17
PING 192.168.1.17 (192.168.1.17) 56(84) bytes of data.
64 bytes from 192.168.1.17: icmp_seq=1 ttl=64 time=0.058 ms
64 bytes from 192.168.1.17: icmp_seq=2 ttl=64 time=0.053 ms
64 bytes from 192.168.1.17: icmp_seq=3 ttl=64 time=0.047 ms

--- 192.168.1.17 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 1998ms
rtt min/avg/max/mdev = 0.047/0.052/0.058/0.009 ms
```



ifconfig```

eth0      Link encap:Ethernet  HWaddr 00:16:17:92:36:09  
          inet addr:192.168.1.17  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:17ff:fe92:3609/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7856 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6853 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6391986 (6.3 MB)  TX bytes:1057778 (1.0 MB)
          Interrupt:16 

eth1      Link encap:Ethernet  HWaddr 00:16:17:92:35:19  
          inet addr:10.0.0.31  Bcast:10.0.0.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:23 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:22 errors:0 dropped:0 overruns:0 frame:0
          TX packets:22 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1712 (1.7 KB)  TX bytes:1712 (1.7 KB)
```

---

### Post by Jonathan L on 2011-10-31
```
eth1      Link encap:Ethernet  HWaddr 00:16:17:92:35:19  
          inet addr:10.0.0.31  Bcast:10.0.0.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:[COLOR=Red]0[/COLOR] errors:[COLOR=Red]0[/COLOR] dropped:0 overruns:0 frame:0
          TX packets:[COLOR=Red]0[/COLOR] errors:[COLOR=Red]0[/COLOR] dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:23 Base address:0xa000 
```Hi 

All that looks exactly how it should be done: except we see the RX and RX packet counts are zero.  Unless everything else was switched off, I am suspecting your cable or your switch.  I'd run tcpdump to see if there is anything at to be seen (should see at least arp when the other things talk, and NAS units tend to do a lot of netbios broadcasts):
```
sudo tcpdump -i eth1 -n

```And I'd check the cables and switch.

Hope that helps.

Kind regards,
Jonathan.

---

### Post by cogitordi on 2011-11-02
> **Jonathan L said:**
> 
All that looks exactly how it should be done: except we see the RX and RX packet counts are zero.  Unless everything else was switched off, I am suspecting your cable or your switch.

Yes, no packet counts. I have an M-Windows box connected to both networks and it is working correctly. I can see all the devices from it. So, my routers and switches are working.

I have connected a known good cable. After more fiddling, I can ping both routers but the default gateway is set to Router B (Network B) instead of Router A. I need to research the command to correct this. IP ROUTE something or other...

I am wondering if some of the problem is due to the drivers for my NVidia and Marvell ethernet ports. I suppose one way to confirm this would be to (yuck) install Windows. (o;

---

### Post by Jonathan L on 2011-11-03
> **cogitordi said:**
> Yes, no packet counts. I have an M-Windows box connected to both networks and it is working correctly. I can see all the devices from it. So, my routers and switches are working.

I have connected a known good cable. After more fiddling, I can ping both routers but the default gateway is set to Router B (Network B) instead of Router A. I need to research the command to correct this. IP ROUTE something or other...

I am wondering if some of the problem is due to the drivers for my NVidia and Marvell ethernet ports. I suppose one way to confirm this would be to (yuck) install Windows. (o;

Glad you've got them pinging.  If the default route is set to B, my guess is that the DHCP is doing that, and you'd be better off disabling it or putting a static route there.

What kind of "more fiddling" did you do to get them pinging?  Did you get any luck with the tcpdump I suggested?  Known good cable: but did you try a known good socket on the router?

Just some thoughts.

Kind regards
Jonathan.

---

### Post by cogitordi on 2011-11-04
> **Jonathan L said:**
> Glad you've got them pinging.  If the default route is set to B, my guess is that the DHCP is doing that, 

Recall that there are two DHCP servers. What is unexpected (to me) is that one DHCP server is consistently preferred to the other by Linux. I don't often laud M-Windows, but in this case, Redmond does well to select as the default route the DHCP server through which the OS can ping a server in the outside world.

Of course, I could write a script to do this very thing.

> and you'd be better off disabling it or putting a static route there.

No, not in my case. Using DHCP on LAN B permits other devices to join LAN B without fuss. (No fuss now that I know how to do it, that is!) 

> What kind of "more fiddling" did you do to get them pinging?  Did you get any luck with the tcpdump I suggested?  Known good cable: but did you try a known good socket on the router?

The fiddling of a simpleton. (o: Cold boot to clear RAM of rubbish; examination of the eth information in dmesg, examination of port assignments using ifconfig; examination of "route". Pings all around. Then I fiddled with "ip route del" and "ip route add default via xxx.xxx.xxx.xxx" until everything was just right.

I didn't suspect a bad socket on the router or switch. The switch is in good condition; Ye Olde Router on LAN B only has one 8P8C socket. (o: 

> Just some thoughts.

I do appreciate your assistance. You helped me think through the problem and I learned what I needed to learn. I do most PC fiddling late at night, when I am worn, torn, and forlorn. (o:

Cheers and best wishes.

---

### Post by Jonathan L on 2011-11-06
Hi Cogito

Glad to hear you're winning.

> Recall that there are two DHCP servers. What is unexpected (to me) is that one DHCP server is consistently preferred to the other by Linux. I'd guess the one that is "preferred" is simply the later one, and it overwrites the default route of the previous one.  Given that LAN B doesn't have an (actual) route to the internet, why not set the default route that the DHCP gives out to be Router A?  Any device solely on LAN B will be no different in functionality, and those which are also on LAN A will get (or keep) a functioning route. 

> I don't often laud M-Windows, but in this case, Redmond does well to select as the default route the DHCP server through which the OS can ping a server in the outside world.
It's also an effective form of field monitoring.  Another downside is that your presumed route has to be working at DHCP time, which might not be the case.  In general, much better configuring something which is stable and known to work and doesn't depend on, for example, boot order or DHCP race conditions.


Just another couple of thoughts.

Kind regards,
Jonathan.

---

