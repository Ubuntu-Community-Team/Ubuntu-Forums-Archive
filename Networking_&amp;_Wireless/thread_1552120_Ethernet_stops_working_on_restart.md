---
title: "Ethernet stops working on restart"
date: 2010-08-13
forum: Networking &amp; Wireless
---

### Post by loboes41 on 2010-08-13
I upgraded to the newest version of Ubuntu a few months ago, and ever since then, the ethernet connection to my router stops working when I restart the machine. It eventually comes back, but after varying amounts of time. Sometimes 20 minutes, sometimes 2 days.

Restarting the computer and cycled reboots of the router don't seem to have any beneficial effect, at least that I can detect.

The light for the slot on the router does not light up like it normally would, so it's almost like the OS doesn't even recognize the network card.

I'm not sure how to troubleshoot this, so any help would be most appreciated.

Ubuntu 10.4,64-bit. Dell XPS 410.

---

### Post by aeiah on 2010-08-13
do you use dhcp or a static ip? is there anything in dmesg? you can probably search with ```
dmesg | grep eth0
``` but if that shows nothing, you may have to scour through the recent boot log. that command obviously assumes your network card is eth0

if you're using dhcp, does issuing this result in a connection?:
```

sudo dhclient

```

---

### Post by loboes41 on 2010-08-13
The router is set to use DHCP , but I do assign that computer a specific IP address.

Here is the output of those commands:

dmesg | grep eth0:
```
[    2.072476] 0000:00:19.0: eth0: (PCI Express:2.5GB/s:Width x1) 00:19:d1:91:28:63

[    2.072479] 0000:00:19.0: eth0: Intel(R) PRO/1000 Network Connection

[    2.072500] 0000:00:19.0: eth0: MAC: 6, PHY: 6, PBA No: 1021ff-0ff

[   23.610354] ADDRCONF(NETDEV_UP): eth0: link is not ready

[   25.140918] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX

[   25.140922] 0000:00:19.0: eth0: 10/100 speed: disabling TSO

[   25.141195] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready

[   25.870219] e1000e: eth0 NIC Link is Down

[   27.550885] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX

[   27.550889] 0000:00:19.0: eth0: 10/100 speed: disabling TSO

[   28.300160] e1000e: eth0 NIC Link is Down

```

sudo dhclient:
```
~$ sudo dhclient

Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/


Listening on LPF/pan0/6e:03:8d:5c:af:51

Sending on   LPF/pan0/6e:03:8d:5c:af:51

Listening on LPF/eth0/00:19:d1:91:28:63

Sending on   LPF/eth0/00:19:d1:91:28:63

Sending on   Socket/fallback
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 5

DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5

DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 5

DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13

DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 10

DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8

DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 15

DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 19

DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 20

DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13

DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 6

DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3

No DHCPOFFERS received.
No working leases in persistent database - sleeping.


```

---

### Post by varunendra on 2010-08-13
So the card & its detection looks ok.
Are you sure your physical connection is fine?

If yes, please post outputs of:
```
ifconfig -a
```
```
cat /etc/network/interfaces
```
```
cat /etc/NetworkManager/nm-system-settings.conf
```
and....

```
route -n
(this one is not necessary)
```

Also, what is the IP/subnet of your router?

---

### Post by loboes41 on 2010-08-13
I tested the connection, no luck there.

Router IP is 192.168.0.1
Subnet Mask: 255.255.255.0


ifconfig -a

```
eth0      Link encap:Ethernet  HWaddr 00:19:d1:91:28:63  
          inet6 addr: fe80::219:d1ff:fe91:2863/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:0 (0.0 B)  TX bytes:1676 (1.6 KB)
          Memory:dffe0000-e0000000 

eth0:avahi Link encap:Ethernet  HWaddr 00:19:d1:91:28:63  
          inet addr:169.254.6.254  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Memory:dffe0000-e0000000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:28 errors:0 dropped:0 overruns:0 frame:0
          TX packets:28 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1748 (1.7 KB)  TX bytes:1748 (1.7 KB)

pan0      Link encap:Ethernet  HWaddr 6e:03:8d:5c:af:51  
          inet6 addr: fe80::6c03:8dff:fe5c:af51/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:520 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:174777 (174.7 KB)

pan0:avahi Link encap:Ethernet  HWaddr 6e:03:8d:5c:af:51  
          inet addr:169.254.7.131  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1


```


cat /etc/network/interfaces
```
auto lo
iface lo inet loopback


```

cat /etc/NetworkManager/nm-system-settings.conf
```
# This file is installed into /etc/NetworkManager, and is loaded by 
# NetworkManager by default.  To override, specify: '--config file' 
# during NM startup.  This can be done by appending to DAEMON_OPTS in 
# the file:
#
# /etc/default/NetworkManager
#

[main]
plugins=ifupdown,keyfile

no-auto-default=00:19:d1:91:28:63,

[ifupdown]
managed=false


```

route -n
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
169.254.0.0     0.0.0.0         255.255.0.0     U     0      0        0 pan0
169.254.0.0     0.0.0.0         255.255.0.0     U     0      0        0 eth0

```

---

### Post by varunendra on 2010-08-13
You said you assign static IP to that computer, but it doesn't seem like that with the output.

Try
```
sudo dhclient
```If this doesn't help getting a valid IP, then try
```
sudo ifconfig eth0 192.168.0.x
(where x has to be replaced with a vacant IP address on your network)
```
**EDIT:** posting screenshots of what Network Manager shows may help making it easier. (mine is attached)

---

### Post by loboes41 on 2010-08-14
I tried the ifconfig and dhclient commands, but still no luck.

I've also tried removing the static address on the router and using dhcp instead, but still could not get a connection. (Ultimately I do need to assign a specific IP for it, but just wanted to test)

Here's a sreenshot of Network Manager while I was trying it set to automatic dhcp.

This is really driving me crazy :S

---

### Post by Iowan on 2010-08-14
> **varunendra said:**
> 
sudo ifconfig eth0 192.168.0.x
(where x has to be replaced with a vacant IP address on your network)
When you tried this, did the IP address "stick"?
Did **ifconfig -a** show the machine with an address?
(Have you tried a different cable?)
(Is it a D-Link router?)

---

### Post by loboes41 on 2010-08-14
The IP did not stick.

I've swapped out the cables, and the cables did work on my laptop running Windows. Also, the connection was working until I rebooted.

It's a Netgear WGR614 router.

---

### Post by loboes41 on 2010-08-14
Also, if it means anything, the light on the router for that slot glows orange (instead of the usual green when the connection is working) when I shut off the computer, but as soon as I turn it back on, the light goes off.

---

### Post by Iowan on 2010-08-14
> **loboes41 said:**
> Also, the connection was working until I rebooted.Rewind for a moment...
The connection was working after the **sudo ifconfig...** ?
That'd be good news - the next step would be to configure a static address via Network Manager, and see if it worked after restart/reboot.

---

### Post by loboes41 on 2010-08-14
No sorry, I meant before I started this thread. Nothing so far has worked.

---

### Post by varunendra on 2010-08-15
Hmmm....
Looks like a solution for you: [http://ubuntuforums.org/showthread.php?t=693562](http://ubuntuforums.org/showthread.php?t=693562)
(remove **avahi-autoipd** via synaptic)


Also I suspect the "no-auto-default=00:19:d1:91:28:63," line in the nm-system-settings.conf file for the inability to get IP from DHCP.

(Just as an experiment), try
```
sudo gedit /etc/NetworkManager/nm-system-settings.conf
```and add # before that line (no-auto-default......) to comment it out. Then reboot and/or use sudo dhclient to see if it can get an IP from DHCP. Before that you may need to set eth0 in nm applet to pick IP from DHCP.

As I said, this would be as an experiment only. I'm aware that you need static IP anyway :).


[B]

EDIT:[/B] The avahi interface is created perhaps only when the machine fails to get a valid IP from DHCP. So if removing the above told line can help getting IP from DHCP, then maybe you won't need to remove that package.

Another solution maybe to just up/down the interfaces for once.
```
sudo ifconfig eth0:avahi down
sudo ifconfig eth0 down
(then after waiting a few seconds for eth0 to get disabled....)
sudo ifconfig eth0 up
(one additional step you may or may not need....)
sudo dhclient (or....)
sudo ifconfig eth0 192.168.0.x
```

---

### Post by loboes41 on 2010-08-15
Still not working. I removed the avahi-autoipd and also commented out that line you mentioned.

I tried setting Network Manager to Automatic, and also assigning a static IP (both in Network Manager and on the router).

When I assign a specific IP, Network Manager tells me it is connected. However, if I ping the router, I get "Destination Host Unreachable" and cannot get out to internet. Also, the light on that router slot still does not light up. The IP I assigned does stick though if I run ifconfig.

I also tried booting from the Ubuntu Live disc I used to install the OS. I was not able to get a connection while running from the live disc either.

---

### Post by varunendra on 2010-08-16
So avahi interface has been vanished, manual IP sticked, cable tested to be fine and still no connection, not even with a live disk !! Now that's like a test of our patience.....:-?:x:evil:](*,)

As for green light on the Ethernet port, it would blink only when the bidirectional communication between both ends is established. Even If the physical connection is ok and the card is detected & operational, the green light won't lit up if the communication is not established. (well.... I've seen exceptions, but very rarely- in low-end ancient cards only).

Anyway, I need a really deep breathe and recollect facts as they are now if you don't mind & still have the patience..:-?.... 


[LIST=1]
[*]Is the current situation same as during your first post (connects randomly, fails at restart), or is it permanently disconnected?
[*]Please post the outputs of the same commands given in post #2  and #4 (please note that as per output of **route **command earlier, you didn't have a gateway defined- a possible reason for no internet.)
[*]Just for confirmation- by pinging router, you mean "**ping 192.168.0.1**" while the PCs IP is **192.168.0.[COLOR=Red]*x*[/COLOR]** - right?
[*]Is the PC directly connected to the router or via a network switch?
[*]Have you tried any other Live CD that connects successfully?
[*](I don't know what.... but feels like I'm still missing something....:-k)
[/LIST]
The 5th point is very important since if any other OS or distro succeeds connecting everytime it is booted, then it will establish the fact that there's nothing wrong with the physical connection. I'd suggest, as always, [Slax]("http://www.slax.org/") or [HBCD]("http://www.9down.com/Hiren-s-BootCD-10-6-352820/") (for trying live XP) as these testing OSes.

Also, if the situation is same as it was in you first post, please try setting MTU to 1400, restart and then post the answers to the above questions.

For setting MTU to 1400, [see here]("http://ubuntuforums.org/showthread.php?p=9718408") (the solution in this thread may also be interesting for you. When [COLOR=Red]**Iowan**[/COLOR] asked about D-link, I think he was suspicious about the same thing, and me too still am even though yours is not D-link!)

Well.... I know it is getting quite frustrating but that's what we technical guys are supposed to deal with,.... right? :). So I hope we can either get it fixed or at least reach to a convincing conclusion.

---

### Post by loboes41 on 2010-08-19
Thank you so much for your persistence!

[LIST=1]
[*]Since I posted here and started fiddling with it, it has not been able to connect at all, whereas before this, it would randomly connect if I left it alone for an hour or a few after restart.
[*]See below for command output. Also attached screenshots of current NetworkManager applet settings.
[*]Yes, that is what I meant by pinging the router.
[*]PC is connected directly to the router
[*]The Slax and HBCD boot CD's also were not able to connect
[/LIST]

Given that the HBCD boot disc was unsuccessful, should I be concerned that it is the NIC that is on the fritz? I opened the case, and it appears to be integrated into the motherboard.

sudo dhclient
```
Listening on LPF/eth0/00:19:d1:91:28:63
Sending on   LPF/eth0/00:19:d1:91:28:63
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 21
No DHCPOFFERS received.
No working leases in persistent database - sleeping.


```

dmesg | grep eth0
```
[    2.182473] 0000:00:19.0: eth0: (PCI Express:2.5GB/s:Width x1) 00:19:d1:91:28:63
[    2.182475] 0000:00:19.0: eth0: Intel(R) PRO/1000 Network Connection
[    2.182496] 0000:00:19.0: eth0: MAC: 6, PHY: 6, PBA No: 1021ff-0ff
[   24.061669] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   25.500910] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[   25.500913] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[   25.501166] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   26.240152] e1000e: eth0 NIC Link is Down
[   28.060880] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[   28.060884] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[   28.790211] e1000e: eth0 NIC Link is Down
[   30.480967] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[   30.480970] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[   31.210117] e1000e: eth0 NIC Link is Down
[   32.900885] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[   32.900888] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[   33.640116] e1000e: eth0 NIC Link is Down
[   35.270901] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[   35.270904] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[   35.990791] e1000e: eth0 NIC Link is Down
[   36.460025] eth0: no IPv6 routers present
[   37.670881] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[   37.670883] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[   38.410761] e1000e: eth0 NIC Link is Down
[   40.020899] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[   40.020902] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[   40.750760] e1000e: eth0 NIC Link is Down
[   42.431509] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[   42.431513] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[   43.150753] e1000e: eth0 NIC Link is Down
[   44.770886] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[   44.770890] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[   45.500763] e1000e: eth0 NIC Link is Down
[   47.170881] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[   47.170884] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[   47.900762] e1000e: eth0 NIC Link is Down
[   49.520905] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[   49.520907] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[   50.250760] e1000e: eth0 NIC Link is Down
[   52.130880] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[   52.130883] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[   52.860761] e1000e: eth0 NIC Link is Down
[   54.540880] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[   54.540883] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[   55.280801] e1000e: eth0 NIC Link is Down
[   57.090881] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[   57.090884] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[   57.810761] e1000e: eth0 NIC Link is Down
[   59.560880] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[   59.560883] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[   60.290743] e1000e: eth0 NIC Link is Down
[   61.930885] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[   61.930889] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[   62.660763] e1000e: eth0 NIC Link is Down
[   66.050880] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[   66.050883] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[   66.770762] e1000e: eth0 NIC Link is Down
[   68.380883] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[   68.380886] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[   69.110763] e1000e: eth0 NIC Link is Down
[   71.001570] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[   71.001574] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[   71.720763] e1000e: eth0 NIC Link is Down
[   73.341506] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[   73.341510] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[   74.070743] e1000e: eth0 NIC Link is Down
[   75.771734] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[   75.771737] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[   76.500762] e1000e: eth0 NIC Link is Down
[   78.380928] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[   78.380931] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[   79.110945] e1000e: eth0 NIC Link is Down
[   80.850904] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[   80.850907] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[   81.580763] e1000e: eth0 NIC Link is Down
[   83.270916] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[   83.270920] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[   84.010769] e1000e: eth0 NIC Link is Down
[   85.700886] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[   85.700889] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[   86.430763] e1000e: eth0 NIC Link is Down
[   88.180886] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[   88.180889] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[   88.910804] e1000e: eth0 NIC Link is Down
[   90.531551] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[   90.531555] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[   91.260865] e1000e: eth0 NIC Link is Down
[   92.951550] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[   92.951553] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[   93.680782] e1000e: eth0 NIC Link is Down
[   95.450885] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[   95.450888] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[   96.180762] e1000e: eth0 NIC Link is Down
[   97.860884] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[   97.860887] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[   98.600764] e1000e: eth0 NIC Link is Down
[  100.220884] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  100.220887] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  100.950803] e1000e: eth0 NIC Link is Down
[  102.630884] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  102.630887] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  103.350137] e1000e: eth0 NIC Link is Down
[  105.100884] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  105.100887] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  105.830783] e1000e: eth0 NIC Link is Down
[  107.470884] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  107.470887] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  108.200803] e1000e: eth0 NIC Link is Down
[  109.880884] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  109.880887] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  110.620762] e1000e: eth0 NIC Link is Down
[  112.500915] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  112.500918] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  113.230763] e1000e: eth0 NIC Link is Down
[  114.850884] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  114.850887] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  115.580763] e1000e: eth0 NIC Link is Down
[  117.200884] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  117.200888] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  117.930838] e1000e: eth0 NIC Link is Down
[  119.600885] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  119.600889] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  120.330762] e1000e: eth0 NIC Link is Down
[  121.940885] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  121.940888] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  122.670742] e1000e: eth0 NIC Link is Down
[  124.340884] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  124.340888] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  125.070802] e1000e: eth0 NIC Link is Down
[  126.820884] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  126.820887] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  127.550785] e1000e: eth0 NIC Link is Down
[  129.240907] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  129.240910] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  129.970782] e1000e: eth0 NIC Link is Down
[  131.620884] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  131.620888] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  132.350763] e1000e: eth0 NIC Link is Down
[  133.970887] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  133.970891] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  134.690746] e1000e: eth0 NIC Link is Down
[  136.371549] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  136.371553] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  137.090762] e1000e: eth0 NIC Link is Down
[  138.960875] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  138.960878] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  139.700782] e1000e: eth0 NIC Link is Down
[  141.390884] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  141.390887] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  142.120802] e1000e: eth0 NIC Link is Down
[  143.750884] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  143.750887] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  144.470782] e1000e: eth0 NIC Link is Down
[  146.230883] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  146.230886] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  146.950803] e1000e: eth0 NIC Link is Down
[  148.590896] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  148.590899] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  149.320802] e1000e: eth0 NIC Link is Down
[  150.940885] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  150.940888] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  151.670803] e1000e: eth0 NIC Link is Down
[  154.930884] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  154.930887] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  155.640762] e1000e: eth0 NIC Link is Down
[  157.260943] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  157.260946] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  157.990851] e1000e: eth0 NIC Link is Down
[  159.680886] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  159.680889] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  160.410763] e1000e: eth0 NIC Link is Down
[  162.091567] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  162.091570] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  162.810762] e1000e: eth0 NIC Link is Down
[  164.430909] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  164.430912] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  165.160763] e1000e: eth0 NIC Link is Down
[  166.830896] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  166.830899] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  167.560762] e1000e: eth0 NIC Link is Down
[  169.240884] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  169.240887] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  169.980782] e1000e: eth0 NIC Link is Down
[  171.860885] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  171.860888] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  172.590801] e1000e: eth0 NIC Link is Down
[  174.210884] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  174.210888] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  174.940763] e1000e: eth0 NIC Link is Down
[  176.550885] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  176.550888] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  177.280761] e1000e: eth0 NIC Link is Down
[  178.960908] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  178.960911] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  179.680761] e1000e: eth0 NIC Link is Down
[  181.300884] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  181.300887] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  182.030762] e1000e: eth0 NIC Link is Down
[  183.720925] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  183.720928] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  184.430763] e1000e: eth0 NIC Link is Down
[  186.050884] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  186.050887] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  186.780802] e1000e: eth0 NIC Link is Down
[  188.450886] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  188.450889] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  189.180823] e1000e: eth0 NIC Link is Down
[  190.920894] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  190.920897] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  191.651136] e1000e: eth0 NIC Link is Down
[  193.301549] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  193.301552] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  194.030292] e1000e: eth0 NIC Link is Down
[  195.770885] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  195.770889] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  196.510164] e1000e: eth0 NIC Link is Down
[  198.161565] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  198.161568] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  198.880762] e1000e: eth0 NIC Link is Down
[  202.050906] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  202.050909] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  202.770762] e1000e: eth0 NIC Link is Down
[  204.450885] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  204.450888] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  205.200762] e1000e: eth0 NIC Link is Down
[  208.360885] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  208.360888] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  209.090455] e1000e: eth0 NIC Link is Down
[  214.040883] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  214.040886] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  214.770762] e1000e: eth0 NIC Link is Down
[  216.450884] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  216.450887] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  217.190762] e1000e: eth0 NIC Link is Down
[  218.810884] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  218.810887] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  219.540802] e1000e: eth0 NIC Link is Down
[  221.300884] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  221.300887] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  222.040150] e1000e: eth0 NIC Link is Down
[  223.660886] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  223.660889] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  224.380802] e1000e: eth0 NIC Link is Down
[  226.080883] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  226.080886] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  226.810762] e1000e: eth0 NIC Link is Down
[  228.490885] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  228.490889] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  229.210802] e1000e: eth0 NIC Link is Down
[  230.890885] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  230.890888] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  231.630802] e1000e: eth0 NIC Link is Down
[  233.370865] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  233.370868] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  234.110806] e1000e: eth0 NIC Link is Down
[  235.750883] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  235.750887] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  236.480763] e1000e: eth0 NIC Link is Down
[  238.111529] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  238.111532] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  238.830782] e1000e: eth0 NIC Link is Down
[  240.520884] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  240.520888] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  241.250802] e1000e: eth0 NIC Link is Down
[  242.940885] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  242.940888] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  243.650762] e1000e: eth0 NIC Link is Down
[  245.270883] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  245.270886] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  246.000802] e1000e: eth0 NIC Link is Down
[  247.670883] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  247.670886] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  248.400763] e1000e: eth0 NIC Link is Down
[  250.020902] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  250.020905] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  250.750802] e1000e: eth0 NIC Link is Down
[  252.500885] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  252.500888] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  253.250823] e1000e: eth0 NIC Link is Down
[  255.350884] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  255.350887] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  256.090782] e1000e: eth0 NIC Link is Down
[  257.710883] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  257.710887] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  258.440802] e1000e: eth0 NIC Link is Down
[  260.110884] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  260.110887] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  260.840802] e1000e: eth0 NIC Link is Down
[  265.810883] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  265.810887] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  266.540783] e1000e: eth0 NIC Link is Down
[  268.301550] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  268.301554] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  269.040782] e1000e: eth0 NIC Link is Down
[  270.660883] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  270.660887] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  271.390804] e1000e: eth0 NIC Link is Down
[  273.080883] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  273.080886] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  273.810762] e1000e: eth0 NIC Link is Down
[  275.490884] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  275.490887] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  276.210762] e1000e: eth0 NIC Link is Down
[  280.960884] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  280.960887] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  281.680782] e1000e: eth0 NIC Link is Down
[  283.420886] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  283.420889] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  284.160802] e1000e: eth0 NIC Link is Down
[  285.970885] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  285.970888] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  286.710762] e1000e: eth0 NIC Link is Down
[  288.331570] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  288.331573] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  289.060762] e1000e: eth0 NIC Link is Down
[  290.740884] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  290.740887] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  291.480803] e1000e: eth0 NIC Link is Down
[  293.161547] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  293.161550] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  293.900763] e1000e: eth0 NIC Link is Down
[  295.580874] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  295.580877] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  296.320762] e1000e: eth0 NIC Link is Down
[  298.000884] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  298.000887] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  298.750763] e1000e: eth0 NIC Link is Down
[  300.560884] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  300.560887] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  301.280782] e1000e: eth0 NIC Link is Down
[  306.250923] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  306.250926] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  306.980782] e1000e: eth0 NIC Link is Down
[  308.651541] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  308.651544] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  309.380802] e1000e: eth0 NIC Link is Down
[  311.080884] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  311.080887] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  311.800762] e1000e: eth0 NIC Link is Down
[  313.420886] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  313.420889] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  314.150823] e1000e: eth0 NIC Link is Down
[  315.840864] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  315.840868] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  316.570763] e1000e: eth0 NIC Link is Down
[  318.270883] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  318.270886] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  319.000782] e1000e: eth0 NIC Link is Down
[  320.700907] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  320.700910] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  321.430741] e1000e: eth0 NIC Link is Down
[  323.100882] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  323.100886] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  323.830741] e1000e: eth0 NIC Link is Down
[  325.510890] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  325.510893] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  326.250842] e1000e: eth0 NIC Link is Down
[  327.930885] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  327.930888] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  328.670803] e1000e: eth0 NIC Link is Down
[  330.350884] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  330.350887] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  331.090762] e1000e: eth0 NIC Link is Down
[  332.770884] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  332.770888] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  333.510164] e1000e: eth0 NIC Link is Down
[  335.130884] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  335.130887] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  335.860782] e1000e: eth0 NIC Link is Down
[  337.530884] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  337.530887] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  338.260782] e1000e: eth0 NIC Link is Down
[  348.080882] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  348.080885] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  348.810782] e1000e: eth0 NIC Link is Down
[  350.460884] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  350.460887] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  351.190782] e1000e: eth0 NIC Link is Down
[  352.800924] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  352.800927] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  353.530762] e1000e: eth0 NIC Link is Down
[  355.200883] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  355.200886] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  355.930762] e1000e: eth0 NIC Link is Down
[  357.550884] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  357.550887] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  358.280782] e1000e: eth0 NIC Link is Down
[  360.060883] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  360.060887] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  360.780762] e1000e: eth0 NIC Link is Down
[  362.460884] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  362.460887] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  363.200802] e1000e: eth0 NIC Link is Down
[  364.840884] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  364.840887] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  365.550762] e1000e: eth0 NIC Link is Down
[  367.220883] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  367.220886] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  367.950763] e1000e: eth0 NIC Link is Down
[  369.570884] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  369.570888] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  370.300138] e1000e: eth0 NIC Link is Down
[  371.990884] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  371.990887] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  372.720761] e1000e: eth0 NIC Link is Down
[  374.420908] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  374.420912] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  375.150805] e1000e: eth0 NIC Link is Down
[  376.840907] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  376.840910] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  377.570782] e1000e: eth0 NIC Link is Down
[  379.270882] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  379.270885] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  380.000802] e1000e: eth0 NIC Link is Down
[  381.670884] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  381.670887] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  382.400802] e1000e: eth0 NIC Link is Down
[  384.080883] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  384.080886] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  384.820762] e1000e: eth0 NIC Link is Down
[  386.510884] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  386.510887] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  387.240761] e1000e: eth0 NIC Link is Down
[  388.860906] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  388.860909] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  389.590762] e1000e: eth0 NIC Link is Down
[  391.270916] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  391.270919] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  391.990782] e1000e: eth0 NIC Link is Down
[  393.600884] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  393.600887] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  394.330762] e1000e: eth0 NIC Link is Down
[  396.011390] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  396.011393] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  396.730782] e1000e: eth0 NIC Link is Down
[  398.410863] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  398.410867] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  399.160782] e1000e: eth0 NIC Link is Down
[  400.840907] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  400.840910] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  401.580770] e1000e: eth0 NIC Link is Down
[  403.320883] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  403.320886] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  404.060740] e1000e: eth0 NIC Link is Down
[  405.750884] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  405.750887] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  406.480763] e1000e: eth0 NIC Link is Down
[  408.231546] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  408.231549] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  408.960802] e1000e: eth0 NIC Link is Down
[  410.570884] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  410.570887] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  411.310781] e1000e: eth0 NIC Link is Down
[  416.340882] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  416.340885] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  417.060782] e1000e: eth0 NIC Link is Down
[  418.930884] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  418.930887] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  419.670762] e1000e: eth0 NIC Link is Down
[  421.300883] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  421.300886] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  422.020782] e1000e: eth0 NIC Link is Down
[  423.700884] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  423.700887] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  424.440802] e1000e: eth0 NIC Link is Down
[  426.050884] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  426.050887] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  426.780763] e1000e: eth0 NIC Link is Down
[  428.480907] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  428.480910] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  429.210805] e1000e: eth0 NIC Link is Down
[  430.890884] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  430.890887] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  431.610762] e1000e: eth0 NIC Link is Down
[  433.231546] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  433.231549] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  433.960802] e1000e: eth0 NIC Link is Down
[  435.630884] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  435.630887] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  436.360804] e1000e: eth0 NIC Link is Down
[  438.040882] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  438.040885] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  438.780762] e1000e: eth0 NIC Link is Down
[  440.500884] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  440.500887] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  441.230802] e1000e: eth0 NIC Link is Down
[  443.120881] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  443.120884] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  443.840761] e1000e: eth0 NIC Link is Down
[  445.590883] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  445.590886] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  446.320782] e1000e: eth0 NIC Link is Down
[  448.011391] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  448.011394] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  448.740822] e1000e: eth0 NIC Link is Down
[  450.430884] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  450.430887] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  451.170822] e1000e: eth0 NIC Link is Down
[  452.920907] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  452.920910] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  453.650781] e1000e: eth0 NIC Link is Down
[  455.410883] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  455.410886] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  456.120762] e1000e: eth0 NIC Link is Down
[  457.940884] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  457.940887] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  458.680802] e1000e: eth0 NIC Link is Down
[  460.370884] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  460.370887] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  461.100763] e1000e: eth0 NIC Link is Down
[  462.780883] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  462.780886] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  463.520762] e1000e: eth0 NIC Link is Down
[  465.141547] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  465.141550] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  465.870782] e1000e: eth0 NIC Link is Down
[  467.490883] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  467.490886] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  468.220761] e1000e: eth0 NIC Link is Down
[  469.890884] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  469.890887] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  470.620762] e1000e: eth0 NIC Link is Down
[  472.230883] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  472.230886] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  472.960763] e1000e: eth0 NIC Link is Down
[  474.660883] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  474.660886] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  475.390822] e1000e: eth0 NIC Link is Down
[  477.100882] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  477.100884] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  477.810762] e1000e: eth0 NIC Link is Down
[  479.520882] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  479.520885] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  480.240804] e1000e: eth0 NIC Link is Down
[  481.910884] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  481.910887] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  482.640762] e1000e: eth0 NIC Link is Down
[  484.261566] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  484.261569] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  484.990781] e1000e: eth0 NIC Link is Down
[  486.870883] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  486.870886] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  487.600762] e1000e: eth0 NIC Link is Down
[  489.210882] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  489.210885] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  489.940762] e1000e: eth0 NIC Link is Down
[  491.700883] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  491.700886] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  492.440762] e1000e: eth0 NIC Link is Down
[  494.060882] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  494.060885] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  494.790782] e1000e: eth0 NIC Link is Down
[  496.460884] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  496.460887] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  497.190802] e1000e: eth0 NIC Link is Down
[  498.870883] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  498.870887] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  499.610762] e1000e: eth0 NIC Link is Down
[  501.230883] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  501.230887] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  501.960763] e1000e: eth0 NIC Link is Down
[  503.650863] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  503.650866] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  504.380762] e1000e: eth0 NIC Link is Down
[  506.060907] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  506.060910] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  506.780782] e1000e: eth0 NIC Link is Down
[  508.590883] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  508.590886] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  509.320762] e1000e: eth0 NIC Link is Down
[  511.191546] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  511.191549] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  511.920763] e1000e: eth0 NIC Link is Down
[  513.820907] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  513.820910] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  514.530761] e1000e: eth0 NIC Link is Down
[  516.220883] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  516.220886] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  516.960762] e1000e: eth0 NIC Link is Down
[  518.791546] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  518.791549] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  519.510164] e1000e: eth0 NIC Link is Down
[  521.200884] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  521.200887] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  521.930762] e1000e: eth0 NIC Link is Down
[  523.560884] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  523.560887] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  524.280802] e1000e: eth0 NIC Link is Down
[  525.920885] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  525.920888] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  526.630763] e1000e: eth0 NIC Link is Down
[  528.301546] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  528.301549] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  529.030762] e1000e: eth0 NIC Link is Down
[  533.781546] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  533.781549] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  534.500742] e1000e: eth0 NIC Link is Down
[  536.240884] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  536.240887] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  536.970781] e1000e: eth0 NIC Link is Down
[  538.630883] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  538.630887] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  539.350762] e1000e: eth0 NIC Link is Down
[  541.110883] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  541.110886] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  541.820762] e1000e: eth0 NIC Link is Down
[  543.480884] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  543.480887] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  544.200761] e1000e: eth0 NIC Link is Down
[  545.900906] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  545.900909] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  546.620763] e1000e: eth0 NIC Link is Down
[  548.260883] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  548.260886] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  548.970802] e1000e: eth0 NIC Link is Down
[  550.660884] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  550.660887] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  551.390783] e1000e: eth0 NIC Link is Down
[  553.070882] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  553.070885] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  553.790843] e1000e: eth0 NIC Link is Down
[  555.410885] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  555.410888] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  556.140802] e1000e: eth0 NIC Link is Down
[  557.830883] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  557.830886] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  558.560762] e1000e: eth0 NIC Link is Down
[  560.260905] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  560.260908] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  560.990782] e1000e: eth0 NIC Link is Down
[  562.680864] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  562.680867] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  563.410782] e1000e: eth0 NIC Link is Down
[  565.110883] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  565.110886] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  565.840761] e1000e: eth0 NIC Link is Down
[  567.510885] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  567.510888] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  568.240762] e1000e: eth0 NIC Link is Down
[  569.920884] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  569.920887] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  570.660761] e1000e: eth0 NIC Link is Down
[  572.350882] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  572.350885] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  573.080762] e1000e: eth0 NIC Link is Down
[  574.700884] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  574.700887] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  575.430772] e1000e: eth0 NIC Link is Down
[  577.100883] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  577.100886] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  577.830762] e1000e: eth0 NIC Link is Down
[  579.450883] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  579.450886] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  580.180822] e1000e: eth0 NIC Link is Down
[  581.850884] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  581.850887] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  582.580762] e1000e: eth0 NIC Link is Down
[  584.260883] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  584.260886] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  585.000803] e1000e: eth0 NIC Link is Down
[  586.680884] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  586.680888] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  587.420762] e1000e: eth0 NIC Link is Down
[  589.171527] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  589.171531] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  589.900802] e1000e: eth0 NIC Link is Down
[  591.590884] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  591.590887] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  592.320822] e1000e: eth0 NIC Link is Down
[  594.080883] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  594.080886] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  594.800762] e1000e: eth0 NIC Link is Down
[  596.420883] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  596.420886] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  597.150763] e1000e: eth0 NIC Link is Down
[  599.040900] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  599.040904] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  599.760763] e1000e: eth0 NIC Link is Down
[  601.440883] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  601.440886] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  602.180802] e1000e: eth0 NIC Link is Down
[  604.050881] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  604.050884] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  604.790803] e1000e: eth0 NIC Link is Down
[  606.470883] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  606.470886] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  607.210761] e1000e: eth0 NIC Link is Down
[  609.030904] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  609.030908] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  609.770761] e1000e: eth0 NIC Link is Down
[  611.510884] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  611.510887] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  612.240762] e1000e: eth0 NIC Link is Down
[  613.890906] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  613.890909] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  614.620763] e1000e: eth0 NIC Link is Down
[  617.990883] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  617.990886] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  618.720802] e1000e: eth0 NIC Link is Down
[  620.341526] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  620.341529] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  621.070762] e1000e: eth0 NIC Link is Down
[  622.900905] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  622.900908] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  623.620761] e1000e: eth0 NIC Link is Down
[  625.270883] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  625.270886] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  626.000782] e1000e: eth0 NIC Link is Down
[  627.610908] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  627.610911] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  628.340842] e1000e: eth0 NIC Link is Down
[  633.260882] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  633.260885] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  633.990782] e1000e: eth0 NIC Link is Down
[  635.740908] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  635.740911] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  636.470762] e1000e: eth0 NIC Link is Down
[  638.220882] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  638.220885] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  638.950762] e1000e: eth0 NIC Link is Down
[  640.570883] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  640.570886] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  641.300781] e1000e: eth0 NIC Link is Down
[  642.981548] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  642.981552] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  643.700761] e1000e: eth0 NIC Link is Down
[  645.310885] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  645.310888] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  646.040802] e1000e: eth0 NIC Link is Down
[  647.740883] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  647.740887] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  648.470762] e1000e: eth0 NIC Link is Down
[  650.140882] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  650.140885] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  650.870802] e1000e: eth0 NIC Link is Down
[  652.480883] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  652.480887] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  653.210801] e1000e: eth0 NIC Link is Down
[  654.910884] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  654.910887] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  655.640782] e1000e: eth0 NIC Link is Down
[  657.320882] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  657.320885] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  658.040782] e1000e: eth0 NIC Link is Down
[  659.660885] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  659.660888] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  660.390760] e1000e: eth0 NIC Link is Down
[  662.060883] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  662.060886] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  662.790781] e1000e: eth0 NIC Link is Down
[  664.470907] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  664.470910] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  665.210821] e1000e: eth0 NIC Link is Down
[  666.890906] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  666.890909] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  667.630762] e1000e: eth0 NIC Link is Down
[  669.250925] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  669.250928] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  669.980802] e1000e: eth0 NIC Link is Down
[  671.910884] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  671.910887] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  672.640763] e1000e: eth0 NIC Link is Down
[  674.300884] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  674.300887] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  675.010788] e1000e: eth0 NIC Link is Down
[  676.690908] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  676.690911] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  677.430762] e1000e: eth0 NIC Link is Down
[  679.050882] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  679.050885] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  679.780762] e1000e: eth0 NIC Link is Down
[  681.450884] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  681.450887] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  682.180803] e1000e: eth0 NIC Link is Down
[  683.861538] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  683.861541] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  684.600760] e1000e: eth0 NIC Link is Down
[  686.220882] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  686.220885] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  686.950762] e1000e: eth0 NIC Link is Down
[  688.640883] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  688.640886] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  689.370802] e1000e: eth0 NIC Link is Down
[  691.060906] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  691.060910] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  691.770763] e1000e: eth0 NIC Link is Down
[  693.580883] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  693.580886] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  694.310762] e1000e: eth0 NIC Link is Down
[  696.201546] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  696.201549] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  696.910761] e1000e: eth0 NIC Link is Down
[  698.730884] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  698.730887] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  699.470762] e1000e: eth0 NIC Link is Down
[  701.210882] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  701.210885] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  701.940763] e1000e: eth0 NIC Link is Down
[  703.760884] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  703.760887] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  704.500764] e1000e: eth0 NIC Link is Down
[  706.260883] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  706.260886] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  706.980782] e1000e: eth0 NIC Link is Down
[  708.650885] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  708.650888] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  709.380802] e1000e: eth0 NIC Link is Down
[  710.990906] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  710.990909] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  711.720762] e1000e: eth0 NIC Link is Down
[  713.410883] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  713.410886] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  714.120762] e1000e: eth0 NIC Link is Down
[  715.800884] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  715.800887] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  716.550761] e1000e: eth0 NIC Link is Down
[  718.170883] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  718.170886] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  718.890801] e1000e: eth0 NIC Link is Down
[  720.570906] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  720.570909] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  721.290782] e1000e: eth0 NIC Link is Down
[  722.911547] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  722.911550] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  723.640762] e1000e: eth0 NIC Link is Down
[  725.310883] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  725.310886] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  726.040781] e1000e: eth0 NIC Link is Down
[  727.780887] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  727.780890] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  728.520761] e1000e: eth0 NIC Link is Down
[  730.211546] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  730.211549] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  730.940762] e1000e: eth0 NIC Link is Down
[  732.690884] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  732.690887] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  733.420761] e1000e: eth0 NIC Link is Down
[  735.030883] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  735.030887] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  735.770741] e1000e: eth0 NIC Link is Down
[  737.440907] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  737.440910] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  738.170740] e1000e: eth0 NIC Link is Down
[  739.780884] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  739.780887] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  740.510163] e1000e: eth0 NIC Link is Down
[  742.290883] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  742.290886] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  743.010770] e1000e: eth0 NIC Link is Down
[  744.630884] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  744.630887] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  745.360762] e1000e: eth0 NIC Link is Down
[  747.060884] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  747.060887] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  747.780762] e1000e: eth0 NIC Link is Down
[  749.480883] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  749.480886] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  750.210822] e1000e: eth0 NIC Link is Down
[  751.911548] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  751.911552] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  752.640761] e1000e: eth0 NIC Link is Down
[  754.310883] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  754.310886] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  755.040802] e1000e: eth0 NIC Link is Down
[  756.720883] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  756.720886] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  757.460762] e1000e: eth0 NIC Link is Down
[  759.140906] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  759.140909] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  759.880803] e1000e: eth0 NIC Link is Down
[  761.500906] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  761.500910] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  762.230802] e1000e: eth0 NIC Link is Down
[  763.901549] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  763.901552] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  764.630762] e1000e: eth0 NIC Link is Down
[  767.810906] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  767.810909] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  768.520762] e1000e: eth0 NIC Link is Down
[  770.140883] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  770.140886] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  770.870802] e1000e: eth0 NIC Link is Down
[  772.550884] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  772.550887] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  773.270802] e1000e: eth0 NIC Link is Down
[  774.900886] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  774.900889] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  775.610762] e1000e: eth0 NIC Link is Down
[  777.290882] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  777.290886] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  778.010786] e1000e: eth0 NIC Link is Down
[  779.700883] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  779.700886] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  780.440762] e1000e: eth0 NIC Link is Down
[  782.120906] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  782.120909] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  782.860762] e1000e: eth0 NIC Link is Down
[  787.490882] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  787.490885] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  788.220802] e1000e: eth0 NIC Link is Down
[  797.380882] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  797.380886] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  798.090762] e1000e: eth0 NIC Link is Down
[  801.160881] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  801.160885] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  801.880762] e1000e: eth0 NIC Link is Down
[  803.500884] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  803.500887] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  804.230802] e1000e: eth0 NIC Link is Down
[  805.921242] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  805.921246] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  806.650763] e1000e: eth0 NIC Link is Down
[  808.330882] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  808.330885] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  809.050761] e1000e: eth0 NIC Link is Down
[  813.900906] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  813.900909] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  814.620762] e1000e: eth0 NIC Link is Down
[  816.300883] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  816.300887] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  817.050802] e1000e: eth0 NIC Link is Down
[  818.660870] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  818.660873] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  819.390762] e1000e: eth0 NIC Link is Down
[  821.090906] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  821.090909] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  821.820762] e1000e: eth0 NIC Link is Down
[  823.500883] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  823.500886] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  824.220761] e1000e: eth0 NIC Link is Down
[  828.961546] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  828.961549] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  829.690761] e1000e: eth0 NIC Link is Down
[  831.430906] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  831.430910] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  832.160762] e1000e: eth0 NIC Link is Down
[  833.991567] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  833.991570] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  834.720761] e1000e: eth0 NIC Link is Down
[  836.340906] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  836.340910] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  837.060761] e1000e: eth0 NIC Link is Down
[  838.680885] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  838.680888] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  839.410762] e1000e: eth0 NIC Link is Down
[  841.110882] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  841.110885] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  841.840802] e1000e: eth0 NIC Link is Down
[  843.530883] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  843.530886] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  844.260781] e1000e: eth0 NIC Link is Down
[  845.961567] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  845.961570] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  846.690762] e1000e: eth0 NIC Link is Down
[  848.510883] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  848.510886] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  849.240762] e1000e: eth0 NIC Link is Down
[  851.190904] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  851.190907] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  851.930782] e1000e: eth0 NIC Link is Down
[  853.540884] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  853.540887] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  854.271765] e1000e: eth0 NIC Link is Down
[  855.951531] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  855.951534] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  856.670763] e1000e: eth0 NIC Link is Down
[  858.420883] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  858.420886] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  859.130762] e1000e: eth0 NIC Link is Down
[  860.800908] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  860.800911] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  861.530762] e1000e: eth0 NIC Link is Down
[  863.140882] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  863.140885] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  863.870762] e1000e: eth0 NIC Link is Down
[  865.800883] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  865.800886] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  866.530762] e1000e: eth0 NIC Link is Down
[  868.240882] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  868.240885] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  868.960785] e1000e: eth0 NIC Link is Down
[  870.600883] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  870.600886] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  871.330764] e1000e: eth0 NIC Link is Down
[  875.961528] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  875.961531] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  876.690762] e1000e: eth0 NIC Link is Down
[  878.310883] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  878.310886] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  879.040781] e1000e: eth0 NIC Link is Down
[  880.750883] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  880.750886] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  881.440763] e1000e: eth0 NIC Link is Down
[  883.060872] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  883.060875] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  883.790821] e1000e: eth0 NIC Link is Down
[  885.481548] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  885.481552] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  886.210803] e1000e: eth0 NIC Link is Down
[  887.991547] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  887.991550] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  888.710762] e1000e: eth0 NIC Link is Down
[  890.330882] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  890.330885] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  891.060802] e1000e: eth0 NIC Link is Down
[  892.730883] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  892.730886] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  893.460802] e1000e: eth0 NIC Link is Down
[  895.080883] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  895.080886] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  895.810802] e1000e: eth0 NIC Link is Down
[  897.481547] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  897.481550] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  898.210782] e1000e: eth0 NIC Link is Down
[  899.830883] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  899.830886] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  900.550761] e1000e: eth0 NIC Link is Down
[  902.380883] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  902.380886] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  903.110762] e1000e: eth0 NIC Link is Down
[  904.800884] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  904.800886] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  905.530762] e1000e: eth0 NIC Link is Down
[  907.180882] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  907.180885] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  907.910783] e1000e: eth0 NIC Link is Down
[  909.520883] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  909.520886] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  910.250822] e1000e: eth0 NIC Link is Down
[  911.950884] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  911.950887] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  912.680782] e1000e: eth0 NIC Link is Down
[  914.440907] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  914.440911] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  915.180763] e1000e: eth0 NIC Link is Down
[  916.800908] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  916.800911] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  917.530760] e1000e: eth0 NIC Link is Down
[  919.200906] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  919.200909] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  919.930781] e1000e: eth0 NIC Link is Down
[  921.540895] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  921.540898] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  922.270802] e1000e: eth0 NIC Link is Down
[  923.940864] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  923.940867] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  924.670783] e1000e: eth0 NIC Link is Down
[  926.290882] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  926.290886] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  927.020821] e1000e: eth0 NIC Link is Down
[  928.700883] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  928.700886] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  929.420762] e1000e: eth0 NIC Link is Down
[  931.160882] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  931.160885] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  931.900761] e1000e: eth0 NIC Link is Down
[  933.710883] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  933.710886] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  934.450762] e1000e: eth0 NIC Link is Down
[  936.070871] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  936.070874] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  936.800762] e1000e: eth0 NIC Link is Down
[  938.540883] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  938.540886] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  939.270761] e1000e: eth0 NIC Link is Down
[  940.930883] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  940.930887] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  941.650763] e1000e: eth0 NIC Link is Down
[  945.200907] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  945.200911] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  945.930783] e1000e: eth0 NIC Link is Down
[  947.550883] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  947.550886] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  948.280781] e1000e: eth0 NIC Link is Down
[  950.031525] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  950.031529] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  950.760762] e1000e: eth0 NIC Link is Down
[  952.420907] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  952.420910] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  953.130761] e1000e: eth0 NIC Link is Down
[  954.750883] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  954.750886] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  955.480782] e1000e: eth0 NIC Link is Down
[  957.170883] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  957.170886] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  957.900762] e1000e: eth0 NIC Link is Down
[  959.600882] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  959.600885] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  960.330761] e1000e: eth0 NIC Link is Down
[  965.041543] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  965.041546] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  965.770762] e1000e: eth0 NIC Link is Down
[  970.410862] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  970.410865] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  971.130762] e1000e: eth0 NIC Link is Down
[  972.810883] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  972.810886] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  973.550801] e1000e: eth0 NIC Link is Down
[  975.190907] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  975.190910] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  975.900763] e1000e: eth0 NIC Link is Down
[  977.610884] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  977.610887] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  978.330761] e1000e: eth0 NIC Link is Down
[  980.000908] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  980.000911] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  980.730801] e1000e: eth0 NIC Link is Down
[  985.570883] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  985.570886] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  986.300802] e1000e: eth0 NIC Link is Down
[  987.910916] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  987.910919] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  988.640763] e1000e: eth0 NIC Link is Down
[  998.880908] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  998.880911] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  999.610764] e1000e: eth0 NIC Link is Down
[ 1001.231547] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1001.231550] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1001.960783] e1000e: eth0 NIC Link is Down
[ 1003.640907] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1003.640910] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1004.380762] e1000e: eth0 NIC Link is Down
[ 1006.000885] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1006.000889] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1006.730763] e1000e: eth0 NIC Link is Down
[ 1008.420884] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1008.420887] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1009.160761] e1000e: eth0 NIC Link is Down
[ 1010.850907] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1010.850910] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1011.580761] e1000e: eth0 NIC Link is Down
[ 1013.251565] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1013.251568] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1013.980782] e1000e: eth0 NIC Link is Down
[ 1015.600884] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1015.600887] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1016.330782] e1000e: eth0 NIC Link is Down
[ 1018.090882] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1018.090885] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1018.830762] e1000e: eth0 NIC Link is Down
[ 1020.450907] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1020.450910] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1021.170762] e1000e: eth0 NIC Link is Down
[ 1022.870907] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1022.870910] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1023.600761] e1000e: eth0 NIC Link is Down
[ 1025.270883] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1025.270885] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1026.000782] e1000e: eth0 NIC Link is Down
[ 1027.740884] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1027.740887] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1028.480802] e1000e: eth0 NIC Link is Down
[ 1030.130870] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1030.130873] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1030.850762] e1000e: eth0 NIC Link is Down
[ 1040.160882] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1040.160885] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1040.900782] e1000e: eth0 NIC Link is Down
[ 1042.520872] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1042.520875] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1043.250862] e1000e: eth0 NIC Link is Down
[ 1044.930885] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1044.930888] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1045.670763] e1000e: eth0 NIC Link is Down
[ 1047.350883] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1047.350886] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1048.090761] e1000e: eth0 NIC Link is Down
[ 1049.740883] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1049.740886] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1050.440763] e1000e: eth0 NIC Link is Down
[ 1052.130892] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1052.130895] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1052.870803] e1000e: eth0 NIC Link is Down
[ 1054.540882] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1054.540886] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1055.270802] e1000e: eth0 NIC Link is Down
[ 1056.890908] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1056.890911] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1057.610762] e1000e: eth0 NIC Link is Down
[ 1059.440907] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1059.440910] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1060.170762] e1000e: eth0 NIC Link is Down
[ 1061.920885] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1061.920888] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1062.650782] e1000e: eth0 NIC Link is Down
[ 1064.260882] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1064.260885] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1064.990783] e1000e: eth0 NIC Link is Down
[ 1066.670884] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1066.670888] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1067.390763] e1000e: eth0 NIC Link is Down
[ 1069.020883] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1069.020886] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1069.740762] e1000e: eth0 NIC Link is Down
[ 1071.420884] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1071.420887] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1072.140763] e1000e: eth0 NIC Link is Down
[ 1073.760883] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1073.760886] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1074.490762] e1000e: eth0 NIC Link is Down
[ 1076.160883] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1076.160886] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1076.890762] e1000e: eth0 NIC Link is Down
[ 1078.581567] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1078.581570] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1079.310781] e1000e: eth0 NIC Link is Down
[ 1080.930907] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1080.930910] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1081.660761] e1000e: eth0 NIC Link is Down
[ 1083.330905] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1083.330908] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1084.060805] e1000e: eth0 NIC Link is Down
[ 1085.860883] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1085.860886] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1086.590822] e1000e: eth0 NIC Link is Down
[ 1088.330884] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1088.330887] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1089.060762] e1000e: eth0 NIC Link is Down
[ 1090.710863] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1090.710866] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1091.440762] e1000e: eth0 NIC Link is Down
[ 1093.120882] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1093.120885] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1093.860763] e1000e: eth0 NIC Link is Down
[ 1095.490886] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1095.490890] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1096.210802] e1000e: eth0 NIC Link is Down
[ 1097.910908] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1097.910911] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1098.630762] e1000e: eth0 NIC Link is Down
[ 1100.330882] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1100.330885] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1101.060801] e1000e: eth0 NIC Link is Down
[ 1102.750883] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1102.750886] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1103.480762] e1000e: eth0 NIC Link is Down
[ 1105.190883] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1105.190886] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1105.910762] e1000e: eth0 NIC Link is Down
[ 1107.581570] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1107.581573] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1108.310781] e1000e: eth0 NIC Link is Down
[ 1111.500883] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1111.500887] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1112.230803] e1000e: eth0 NIC Link is Down
[ 1113.990884] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1113.990887] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1114.730782] e1000e: eth0 NIC Link is Down
[ 1116.350913] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1116.350916] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1117.070762] e1000e: eth0 NIC Link is Down
[ 1118.750907] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1118.750909] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1119.470761] e1000e: eth0 NIC Link is Down
[ 1121.091538] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1121.091541] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1121.820762] e1000e: eth0 NIC Link is Down
[ 1123.510892] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1123.510895] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1124.220762] e1000e: eth0 NIC Link is Down
[ 1125.910884] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1125.910888] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1126.640762] e1000e: eth0 NIC Link is Down
[ 1128.320882] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1128.320886] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1129.070762] e1000e: eth0 NIC Link is Down
[ 1130.810907] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1130.810910] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1131.540782] e1000e: eth0 NIC Link is Down
[ 1133.231548] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1133.231551] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1133.970823] e1000e: eth0 NIC Link is Down
[ 1135.750884] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1135.750887] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1136.450762] e1000e: eth0 NIC Link is Down
[ 1138.060882] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1138.060886] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1138.790781] e1000e: eth0 NIC Link is Down
[ 1140.630907] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1140.630910] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1141.350802] e1000e: eth0 NIC Link is Down
[ 1143.001567] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1143.001571] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1143.720762] e1000e: eth0 NIC Link is Down
[ 1145.530884] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1145.530887] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1146.250221] e1000e: eth0 NIC Link is Down
[ 1147.930863] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1147.930866] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1148.680782] e1000e: eth0 NIC Link is Down
[ 1150.480883] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1150.480886] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1151.210762] e1000e: eth0 NIC Link is Down
[ 1155.950907] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1155.950910] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1156.670763] e1000e: eth0 NIC Link is Down
[ 1158.420882] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1158.420885] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1159.150761] e1000e: eth0 NIC Link is Down
[ 1160.840884] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1160.840887] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1161.580762] e1000e: eth0 NIC Link is Down
[ 1163.231548] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1163.231551] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1163.950782] e1000e: eth0 NIC Link is Down
[ 1165.650883] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1165.650887] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1166.370781] e1000e: eth0 NIC Link is Down
[ 1168.050883] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1168.050886] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1168.790782] e1000e: eth0 NIC Link is Down
[ 1170.470883] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1170.470886] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1171.220762] e1000e: eth0 NIC Link is Down
[ 1172.830864] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1172.830867] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1173.560762] e1000e: eth0 NIC Link is Down
[ 1175.261627] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1175.261630] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1175.990762] e1000e: eth0 NIC Link is Down
[ 1177.700882] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1177.700886] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1178.410761] e1000e: eth0 NIC Link is Down
[ 1180.110883] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1180.110886] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1180.840761] e1000e: eth0 NIC Link is Down
[ 1184.050904] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1184.050907] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1184.780802] e1000e: eth0 NIC Link is Down
[ 1187.870882] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1187.870885] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1188.600763] e1000e: eth0 NIC Link is Down
[ 1190.210864] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1190.210867] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1190.940762] e1000e: eth0 NIC Link is Down
[ 1192.621446] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1192.621449] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1193.340762] e1000e: eth0 NIC Link is Down
[ 1194.960884] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1194.960887] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1195.690762] e1000e: eth0 NIC Link is Down
[ 1197.450883] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1197.450886] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1198.190762] e1000e: eth0 NIC Link is Down
[ 1199.810884] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1199.810887] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1200.540782] e1000e: eth0 NIC Link is Down
[ 1202.300883] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1202.300886] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1203.040782] e1000e: eth0 NIC Link is Down
[ 1204.660884] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1204.660887] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1205.390802] e1000e: eth0 NIC Link is Down
[ 1207.070883] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1207.070886] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1207.790822] e1000e: eth0 NIC Link is Down
[ 1209.400883] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1209.400886] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1210.130784] e1000e: eth0 NIC Link is Down
[ 1212.100904] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1212.100907] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1212.820762] e1000e: eth0 NIC Link is Down
[ 1214.510887] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1214.510890] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1215.240823] e1000e: eth0 NIC Link is Down
[ 1217.030881] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1217.030884] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1217.770762] e1000e: eth0 NIC Link is Down
[ 1219.390883] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1219.390886] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1220.120762] e1000e: eth0 NIC Link is Down
[ 1221.730884] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1221.730887] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1222.460782] e1000e: eth0 NIC Link is Down
[ 1224.230883] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1224.230886] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1224.970822] e1000e: eth0 NIC Link is Down
[ 1226.710883] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1226.710887] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1227.440762] e1000e: eth0 NIC Link is Down
[ 1229.151547] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1229.151550] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1229.870802] e1000e: eth0 NIC Link is Down
[ 1231.520885] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1231.520888] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1232.240784] e1000e: eth0 NIC Link is Down
[ 1236.880882] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1236.880885] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1237.600782] e1000e: eth0 NIC Link is Down
[ 1239.220883] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1239.220887] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1239.950782] e1000e: eth0 NIC Link is Down
[ 1241.620883] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1241.620886] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1242.350762] e1000e: eth0 NIC Link is Down
[ 1244.030882] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1244.030885] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1244.770763] e1000e: eth0 NIC Link is Down
[ 1246.450907] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1246.450910] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1247.190762] e1000e: eth0 NIC Link is Down
[ 1248.940884] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1248.940887] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1249.670802] e1000e: eth0 NIC Link is Down
[ 1251.360906] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1251.360909] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1252.100761] e1000e: eth0 NIC Link is Down
[ 1253.740883] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1253.740886] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1254.470802] e1000e: eth0 NIC Link is Down
[ 1256.090882] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1256.090885] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1256.820801] e1000e: eth0 NIC Link is Down
[ 1258.490883] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1258.490886] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1259.220781] e1000e: eth0 NIC Link is Down
[ 1260.830907] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1260.830910] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1261.560762] e1000e: eth0 NIC Link is Down
[ 1263.390907] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1263.390910] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1264.120762] e1000e: eth0 NIC Link is Down
[ 1265.810883] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1265.810886] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1266.540802] e1000e: eth0 NIC Link is Down
[ 1268.190882] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1268.190885] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1268.920802] e1000e: eth0 NIC Link is Down
[ 1270.530883] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1270.530886] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1271.260883] e1000e: eth0 NIC Link is Down
[ 1272.960884] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1272.960887] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1273.690801] e1000e: eth0 NIC Link is Down
[ 1275.460885] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1275.460889] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1276.190801] e1000e: eth0 NIC Link is Down
[ 1277.810907] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1277.810910] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1278.530762] e1000e: eth0 NIC Link is Down
[ 1280.210863] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1280.210866] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1280.930762] e1000e: eth0 NIC Link is Down
[ 1282.550883] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1282.550886] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1283.280822] e1000e: eth0 NIC Link is Down
[ 1284.970924] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1284.970927] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1285.680824] e1000e: eth0 NIC Link is Down
[ 1287.300882] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1287.300885] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1288.030762] e1000e: eth0 NIC Link is Down
[ 1289.710884] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1289.710887] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1290.430741] e1000e: eth0 NIC Link is Down
[ 1292.110884] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1292.110887] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1292.850762] e1000e: eth0 NIC Link is Down
[ 1294.660883] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1294.660886] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1295.380782] e1000e: eth0 NIC Link is Down
[ 1297.001568] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1297.001571] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1297.730761] e1000e: eth0 NIC Link is Down
[ 1299.490906] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1299.490909] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1300.230801] e1000e: eth0 NIC Link is Down
[ 1301.850885] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1301.850888] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1302.580802] e1000e: eth0 NIC Link is Down
[ 1306.140885] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1306.140888] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1306.860762] e1000e: eth0 NIC Link is Down
[ 1308.480863] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1308.480866] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1309.210821] e1000e: eth0 NIC Link is Down
[ 1310.880907] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1310.880910] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1311.610802] e1000e: eth0 NIC Link is Down
[ 1313.230883] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1313.230886] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1313.960782] e1000e: eth0 NIC Link is Down
[ 1315.630883] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1315.630886] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1316.360762] e1000e: eth0 NIC Link is Down
[ 1318.040906] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1318.040909] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1318.780762] e1000e: eth0 NIC Link is Down
[ 1320.460882] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1320.460885] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1321.200813] e1000e: eth0 NIC Link is Down
[ 1322.820883] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1322.820887] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1323.550762] e1000e: eth0 NIC Link is Down
[ 1325.240883] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1325.240886] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1325.970782] e1000e: eth0 NIC Link is Down
[ 1327.650883] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1327.650886] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1328.370761] e1000e: eth0 NIC Link is Down
[ 1330.120883] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1330.120886] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1330.850762] e1000e: eth0 NIC Link is Down
[ 1332.500906] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1332.500909] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1333.220801] e1000e: eth0 NIC Link is Down
[ 1334.840885] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1334.840889] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1335.570763] e1000e: eth0 NIC Link is Down
[ 1337.271526] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1337.271530] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1338.000782] e1000e: eth0 NIC Link is Down
[ 1339.670883] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1339.670886] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1340.400760] e1000e: eth0 NIC Link is Down
[ 1343.770883] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1343.770886] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1344.500762] e1000e: eth0 NIC Link is Down
[ 1346.120907] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1346.120911] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1346.850822] e1000e: eth0 NIC Link is Down
[ 1348.670908] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1348.670911] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1349.400762] e1000e: eth0 NIC Link is Down
[ 1351.050923] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1351.050927] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1351.780802] e1000e: eth0 NIC Link is Down
[ 1353.460883] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1353.460886] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1354.200762] e1000e: eth0 NIC Link is Down
[ 1356.070881] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1356.070884] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1356.810740] e1000e: eth0 NIC Link is Down
[ 1358.490883] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1358.490886] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1359.230802] e1000e: eth0 NIC Link is Down
[ 1360.850883] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1360.850886] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1361.580803] e1000e: eth0 NIC Link is Down
[ 1363.190884] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1363.190887] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1363.920762] e1000e: eth0 NIC Link is Down
[ 1365.680889] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1365.680892] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1366.420763] e1000e: eth0 NIC Link is Down
[ 1368.040882] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1368.040885] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1368.770761] e1000e: eth0 NIC Link is Down
[ 1370.440883] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1370.440886] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1371.170762] e1000e: eth0 NIC Link is Down
[ 1372.790884] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1372.790887] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1373.520136] e1000e: eth0 NIC Link is Down
[ 1375.221495] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1375.221498] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1375.940761] e1000e: eth0 NIC Link is Down
[ 1377.640884] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1377.640887] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1378.370802] e1000e: eth0 NIC Link is Down
[ 1380.060882] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1380.060885] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1380.790782] e1000e: eth0 NIC Link is Down
[ 1382.490883] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1382.490886] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1383.220803] e1000e: eth0 NIC Link is Down
[ 1384.890883] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1384.890886] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1385.620762] e1000e: eth0 NIC Link is Down
[ 1387.231539] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1387.231542] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1387.960782] e1000e: eth0 NIC Link is Down
[ 1389.640907] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1389.640910] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1390.360762] e1000e: eth0 NIC Link is Down
[ 1391.980884] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1391.980887] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1392.710762] e1000e: eth0 NIC Link is Down
[ 1394.380884] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1394.380887] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1395.110763] e1000e: eth0 NIC Link is Down
[ 1396.730884] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1396.730887] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1397.460762] e1000e: eth0 NIC Link is Down
[ 1399.340883] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1399.340886] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1400.070761] e1000e: eth0 NIC Link is Down
[ 1401.680884] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1401.680887] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1402.410761] e1000e: eth0 NIC Link is Down
[ 1404.170883] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1404.170886] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1404.920781] e1000e: eth0 NIC Link is Down
[ 1406.530883] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1406.530886] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1407.260925] e1000e: eth0 NIC Link is Down
[ 1408.930884] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1408.930887] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1409.660762] e1000e: eth0 NIC Link is Down
[ 1411.340884] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1411.340887] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1412.080763] e1000e: eth0 NIC Link is Down
[ 1413.700886] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1413.700889] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1414.430823] e1000e: eth0 NIC Link is Down
[ 1416.130906] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1416.130909] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1416.860762] e1000e: eth0 NIC Link is Down
[ 1418.530883] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1418.530886] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1419.260314] e1000e: eth0 NIC Link is Down
[ 1422.420883] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1422.420886] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1423.150763] e1000e: eth0 NIC Link is Down
[ 1424.771548] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1424.771551] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1425.500802] e1000e: eth0 NIC Link is Down
[ 1427.190882] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1427.190886] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1427.920762] e1000e: eth0 NIC Link is Down
[ 1429.700884] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1429.700887] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1430.420762] e1000e: eth0 NIC Link is Down
[ 1432.040883] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1432.040885] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1432.770822] e1000e: eth0 NIC Link is Down
[ 1434.530884] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1434.530887] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1435.270823] e1000e: eth0 NIC Link is Down
[ 1437.080906] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1437.080909] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1437.800762] e1000e: eth0 NIC Link is Down
[ 1439.420923] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1439.420926] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1440.150762] e1000e: eth0 NIC Link is Down
[ 1441.850883] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1441.850886] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1442.570762] e1000e: eth0 NIC Link is Down
[ 1444.340906] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1444.340909] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1445.070762] e1000e: eth0 NIC Link is Down
[ 1446.820883] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1446.820886] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1447.550762] e1000e: eth0 NIC Link is Down
[ 1449.220883] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1449.220886] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1449.930741] e1000e: eth0 NIC Link is Down
[ 1451.540906] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1451.540909] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1452.270804] e1000e: eth0 NIC Link is Down
[ 1453.970906] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1453.970909] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1454.700803] e1000e: eth0 NIC Link is Down
[ 1456.370884] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1456.370888] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1457.100822] e1000e: eth0 NIC Link is Down
[ 1458.720907] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1458.720910] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1459.440762] e1000e: eth0 NIC Link is Down
[ 1461.140883] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1461.140886] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1461.870762] e1000e: eth0 NIC Link is Down
[ 1463.550862] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1463.550865] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1464.270805] e1000e: eth0 NIC Link is Down
[ 1465.880871] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1465.880874] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1466.620802] e1000e: eth0 NIC Link is Down
[ 1468.311546] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1468.311549] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1469.040802] e1000e: eth0 NIC Link is Down
[ 1470.740883] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1470.740886] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1471.470763] e1000e: eth0 NIC Link is Down
[ 1473.140884] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1473.140887] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1473.870762] e1000e: eth0 NIC Link is Down
[ 1475.550906] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1475.550909] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1476.290802] e1000e: eth0 NIC Link is Down
[ 1478.100883] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1478.100886] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1478.820762] e1000e: eth0 NIC Link is Down
[ 1480.440907] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1480.440910] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1481.170762] e1000e: eth0 NIC Link is Down
[ 1482.920885] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1482.920888] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1483.670802] e1000e: eth0 NIC Link is Down
[ 1485.281549] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1485.281552] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1486.010788] e1000e: eth0 NIC Link is Down
[ 1487.781569] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1487.781572] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1488.511143] e1000e: eth0 NIC Link is Down
[ 1490.260883] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1490.260886] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1490.990781] e1000e: eth0 NIC Link is Down
[ 1492.940885] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1492.940888] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1493.680762] e1000e: eth0 NIC Link is Down
[ 1495.301526] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1495.301529] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1496.020822] e1000e: eth0 NIC Link is Down
[ 1497.710884] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1497.710887] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1498.420763] e1000e: eth0 NIC Link is Down
[ 1500.040882] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1500.040886] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1500.770771] e1000e: eth0 NIC Link is Down
[ 1502.470884] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1502.470887] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1503.200741] e1000e: eth0 NIC Link is Down
[ 1504.870884] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1504.870887] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1505.600740] e1000e: eth0 NIC Link is Down
[ 1507.281525] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1507.281529] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1508.020821] e1000e: eth0 NIC Link is Down
[ 1509.700884] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1509.700887] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1510.440802] e1000e: eth0 NIC Link is Down
[ 1512.250924] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1512.250927] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1512.970399] e1000e: eth0 NIC Link is Down
[ 1514.590885] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1514.590889] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1515.320802] e1000e: eth0 NIC Link is Down
[ 1517.250950] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1517.250953] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1517.980782] e1000e: eth0 NIC Link is Down
[ 1519.860884] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1519.860887] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1520.590802] e1000e: eth0 NIC Link is Down
[ 1522.260883] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1522.260886] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1522.990802] e1000e: eth0 NIC Link is Down
[ 1524.600891] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1524.600894] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1525.330762] e1000e: eth0 NIC Link is Down
[ 1527.021567] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1527.021570] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1527.730762] e1000e: eth0 NIC Link is Down
[ 1529.350882] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1529.350885] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1530.080762] e1000e: eth0 NIC Link is Down
[ 1531.750887] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1531.750890] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1532.480763] e1000e: eth0 NIC Link is Down
[ 1534.100882] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1534.100886] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1534.830823] e1000e: eth0 NIC Link is Down
[ 1536.510884] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1536.510887] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1537.230763] e1000e: eth0 NIC Link is Down
[ 1540.341566] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1540.341569] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1541.040781] e1000e: eth0 NIC Link is Down
[ 1546.080883] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1546.080887] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1546.800803] e1000e: eth0 NIC Link is Down
[ 1548.480883] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1548.480886] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1549.220762] e1000e: eth0 NIC Link is Down
[ 1550.840883] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1550.840886] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1551.570802] e1000e: eth0 NIC Link is Down
[ 1553.281548] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1553.281550] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1553.990782] e1000e: eth0 NIC Link is Down
[ 1555.690883] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1555.690886] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1556.420782] e1000e: eth0 NIC Link is Down
[ 1558.110883] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1558.110886] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1558.840801] e1000e: eth0 NIC Link is Down
[ 1560.510863] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1560.510866] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1561.240762] e1000e: eth0 NIC Link is Down
[ 1563.050881] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1563.050884] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1563.770762] e1000e: eth0 NIC Link is Down
[ 1565.390884] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1565.390887] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1566.120762] e1000e: eth0 NIC Link is Down
[ 1567.800883] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1567.800886] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1568.520762] e1000e: eth0 NIC Link is Down
[ 1570.260870] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1570.260873] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1571.000782] e1000e: eth0 NIC Link is Down
[ 1572.640884] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1572.640887] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1573.370761] e1000e: eth0 NIC Link is Down
[ 1575.060884] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1575.060887] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1575.790783] e1000e: eth0 NIC Link is Down
[ 1577.410884] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1577.410887] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1578.140762] e1000e: eth0 NIC Link is Down
[ 1579.831529] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1579.831532] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1580.540781] e1000e: eth0 NIC Link is Down
[ 1582.160926] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1582.160929] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1582.890782] e1000e: eth0 NIC Link is Down
[ 1584.820908] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1584.820910] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1585.550781] e1000e: eth0 NIC Link is Down
[ 1587.190882] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1587.190885] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1587.920782] e1000e: eth0 NIC Link is Down
[ 1589.670908] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1589.670910] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1590.400762] e1000e: eth0 NIC Link is Down
[ 1592.040882] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1592.040886] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1592.770762] e1000e: eth0 NIC Link is Down
[ 1594.390883] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1594.390886] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1595.120761] e1000e: eth0 NIC Link is Down
[ 1596.790884] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1596.790887] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1597.520762] e1000e: eth0 NIC Link is Down
[ 1599.390906] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1599.390909] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1600.130762] e1000e: eth0 NIC Link is Down
[ 1601.810885] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1601.810888] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1602.550782] e1000e: eth0 NIC Link is Down
[ 1604.170883] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1604.170886] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1604.900803] e1000e: eth0 NIC Link is Down
[ 1609.650906] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1609.650910] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1610.360801] e1000e: eth0 NIC Link is Down
[ 1611.980884] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1611.980887] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1612.710762] e1000e: eth0 NIC Link is Down
[ 1614.400883] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1614.400886] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1615.110802] e1000e: eth0 NIC Link is Down
[ 1616.790883] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1616.790886] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1617.530802] e1000e: eth0 NIC Link is Down
[ 1619.220870] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1619.220873] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1619.960751] e1000e: eth0 NIC Link is Down
[ 1621.700884] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1621.700887] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1622.430763] e1000e: eth0 NIC Link is Down
[ 1624.130907] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1624.130910] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1624.860802] e1000e: eth0 NIC Link is Down
[ 1626.500884] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1626.500887] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1627.230803] e1000e: eth0 NIC Link is Down
[ 1628.850908] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1628.850911] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1629.580761] e1000e: eth0 NIC Link is Down
[ 1631.260883] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1631.260887] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1631.980782] e1000e: eth0 NIC Link is Down
[ 1633.590906] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1633.590909] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1634.320801] e1000e: eth0 NIC Link is Down
[ 1636.150908] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1636.150912] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1636.880801] e1000e: eth0 NIC Link is Down
[ 1638.570883] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1638.570886] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1639.300802] e1000e: eth0 NIC Link is Down
[ 1640.950907] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1640.950910] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1641.680802] e1000e: eth0 NIC Link is Down
[ 1643.291548] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1643.291551] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1644.020138] e1000e: eth0 NIC Link is Down
[ 1645.720882] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1645.720886] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1646.450762] e1000e: eth0 NIC Link is Down
[ 1648.210883] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1648.210886] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1648.950762] e1000e: eth0 NIC Link is Down
[ 1650.570907] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1650.570910] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1651.300823] e1000e: eth0 NIC Link is Down
[ 1652.970884] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1652.970887] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1653.700802] e1000e: eth0 NIC Link is Down
[ 1655.311546] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1655.311549] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1656.040782] e1000e: eth0 NIC Link is Down
[ 1657.720883] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1657.720886] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1658.440763] e1000e: eth0 NIC Link is Down
[ 1660.060892] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1660.060895] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1660.790782] e1000e: eth0 NIC Link is Down
[ 1662.470906] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1662.470910] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1663.190802] e1000e: eth0 NIC Link is Down
[ 1664.950865] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1664.950868] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1665.670763] e1000e: eth0 NIC Link is Down
[ 1667.500907] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1667.500910] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1668.220763] e1000e: eth0 NIC Link is Down
[ 1669.970906] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1669.970910] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1670.700782] e1000e: eth0 NIC Link is Down
[ 1672.370883] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1672.370886] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1673.100761] e1000e: eth0 NIC Link is Down
[ 1674.710895] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1674.710899] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1675.450802] e1000e: eth0 NIC Link is Down
[ 1677.610884] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1677.610887] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1678.340761] e1000e: eth0 NIC Link is Down
[ 1679.960885] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1679.960888] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1680.690762] e1000e: eth0 NIC Link is Down
[ 1682.311567] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1682.311570] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1683.040782] e1000e: eth0 NIC Link is Down
[ 1684.730907] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1684.730910] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1685.440761] e1000e: eth0 NIC Link is Down
[ 1687.070883] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1687.070886] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1687.780782] e1000e: eth0 NIC Link is Down
[ 1689.460883] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1689.460886] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1690.180763] e1000e: eth0 NIC Link is Down
[ 1691.800908] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1691.800911] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1692.530762] e1000e: eth0 NIC Link is Down
[ 1694.220882] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1694.220885] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1694.930802] e1000e: eth0 NIC Link is Down
[ 1696.680884] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1696.680887] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1697.410802] e1000e: eth0 NIC Link is Down
[ 1699.100906] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1699.100909] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1699.830762] e1000e: eth0 NIC Link is Down
[ 1701.490884] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1701.490887] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1702.200782] e1000e: eth0 NIC Link is Down
[ 1703.911570] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1703.911573] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1704.630762] e1000e: eth0 NIC Link is Down
[ 1706.371530] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1706.371534] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1707.100763] e1000e: eth0 NIC Link is Down
[ 1708.750885] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1708.750888] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1709.480763] e1000e: eth0 NIC Link is Down
[ 1711.180884] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1711.180887] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1711.900806] e1000e: eth0 NIC Link is Down
[ 1713.580887] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1713.580891] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1714.321023] e1000e: eth0 NIC Link is Down
[ 1715.940885] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1715.940888] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1716.670764] e1000e: eth0 NIC Link is Down
[ 1718.341547] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1718.341550] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1719.070763] e1000e: eth0 NIC Link is Down
[ 1720.690908] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1720.690911] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1721.420782] e1000e: eth0 NIC Link is Down
[ 1723.090864] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1723.090867] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1723.820761] e1000e: eth0 NIC Link is Down
[ 1725.431527] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1725.431530] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1726.160764] e1000e: eth0 NIC Link is Down
[ 1732.550883] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1732.550886] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1733.280782] e1000e: eth0 NIC Link is Down
[ 1735.030882] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1735.030885] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1735.760784] e1000e: eth0 NIC Link is Down
[ 1737.510884] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1737.510888] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1738.240764] e1000e: eth0 NIC Link is Down
[ 1739.850884] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1739.850887] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1740.580762] e1000e: eth0 NIC Link is Down
[ 1742.270883] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1742.270887] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1742.980803] e1000e: eth0 NIC Link is Down
[ 1744.600884] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1744.600887] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1745.330822] e1000e: eth0 NIC Link is Down
[ 1747.031526] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1747.031529] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1747.750762] e1000e: eth0 NIC Link is Down
[ 1749.431568] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1749.431571] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1750.150762] e1000e: eth0 NIC Link is Down
[ 1751.770885] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1751.770888] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1752.500762] e1000e: eth0 NIC Link is Down
[ 1754.201531] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1754.201534] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1754.930192] e1000e: eth0 NIC Link is Down
[ 1756.600885] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1756.600888] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1757.330826] e1000e: eth0 NIC Link is Down

```

ifconfig -a
```
eth0      Link encap:Ethernet  HWaddr 00:19:d1:91:28:63  
          inet6 addr: fe80::219:d1ff:fe91:2863/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:0 (0.0 B)  TX bytes:1334 (1.3 KB)
          Memory:dffe0000-e0000000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3540 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3540 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:266548 (266.5 KB)  TX bytes:266548 (266.5 KB)


```

cat /etc/network/interfaces
```
auto lo
iface lo inet loopback


```

route -n
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

```

---

### Post by grahammechanical on 2010-08-20
Other have suggested this

```
sudo lshw -C network
```Look for lines that begin
> *-networkYou should see listed all the network interfaces on your motherboard. On my system after "description" I see two ethernet interfaces. I can also see the vendor's name. This tells me that the OS has recognised that the motherboard has ethernet and so it should work. I may be wrong.

Regards.

---

### Post by loboes41 on 2010-08-21
Okay, here's the output of that:

sudo lshw -C network
```
  *-network
       description: Ethernet interface
       product: 82566DC Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 02
       serial: 00:19:d1:91:28:63
       capacity: 1GB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.0.2-k2 firmware=1.1-0 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:27 memory:dffe0000-dfffffff memory:dffdb000-dffdbfff ioport:ecc0(size=32)

```

Does this look to be in order?

---

### Post by varunendra on 2010-08-21
> **loboes41 said:**
> Given that the HBCD boot disc was unsuccessful, should I be concerned that it is the NIC that is on the fritz? I opened the case, and it appears to be integrated into the motherboard.

On MiniXP desktop, there's an icon named 'Network Support'. Did you run it before trying to connect? Your network card will be detected & configured only after running it.

> **loboes41 said:**
> [/CODE]route -n
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

```
No routes defined? That's strange...., did you wait for a few seconds before the terminal could return to the command prompt?

The snaps show you are currently trying DHCP. Make sure the 'Method' under 'IPv6 Settings' is set to 'Ignore', then try-
```
sudo ifconfig eth0 192.168.0.100
(assuming '100' is a vacant IP address on your network. Change if it isn't.)
```


**_Another Shot_:**

Now that you have Slax also, here's another possible diagnosis:
**Prerequisites:**

[LIST=1]
[*]BIOS capability to boot from network.
[*]A separate PC/Laptop with a working Ethernet interface.
[*]A network cross-cable (a straight one should also do since eth0 is auto-negotiable, but a cross-cable is recommended)
[/LIST]
**Procedure:** Connect the laptop/PC directly to your current PC using the cross-cable. Then boot that PC/laptop from Slax CD choosing "Slax as PXE server". After Slax (as PXE server) is up & running, reboot your current PC and choose (either from boot-menu or BIOS) to boot from network.

Now if its Ethernet interface is functional, it will pickup the DHCP offer from the laptop/PC and boot into Slax. If it fails, recheck if it is connected properly and if the option to boot from network **IS ENABLED in BIOS**. If all of this is okay and it still fails to pick up any DHCP offer & thus boot into Slax, then the Ethernet port has definitely got some defect. I'd suspect the port because the adapter seems okay as is evident from the above command (lshw -C network).
[COLOR=DarkRed][I]
[The worst thing (at least with me) is that I'm still unsure whether it is a software or hardware issue! Post in detail the results & we'll see if I can get anything sensible this time.][/I][/COLOR]

---

### Post by loboes41 on 2010-09-08
Neither of those worked.

Couldn't boot over network from Slax, and sudo ifconfig eth0 192.168.0.100 did not solve it.

---

### Post by maX0 on 2010-09-14
I've had very similar issue and solved it with adding following script into /etc/init.d/
```

#/bin/sh
ifconfig eth0 down
sleep 10
ifconfig eth0 up

```btw. has to be executable (chmod +x)

Actually nevermind this, it only works now if I run it manually once the boot process is over... :s

---

