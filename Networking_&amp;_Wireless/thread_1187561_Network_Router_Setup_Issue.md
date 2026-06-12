---
title: "Network Router Setup Issue"
date: 2009-06-14
forum: Networking &amp; Wireless
---

### Post by bendavis77 on 2009-06-14
A couple of days ago my router was having connectivity issues through both direct line and wireless connect.  To my knowledge, no settings were changed.  I can connect with a direct line from my desktop computer to the cable modem and everything works fine.  However, when I bring a router into the situation nothing works.  I've trolled posts for any resolutions for the issue but I've come up short in the resolution department.

I've had the cable company come out to check my signal and it is perfect.  I've tried two different routers (Linksys & Belkin), and the same issue persists.

When I connect to my router (Linksys WRT54G2) with a direct line I receive notification onscreen that "Auto eth0 connection established."  However I can not connect with firefox to the web.  Very frustrating.  However, I can connect to the router setup screen.

Router setup via 192.168.1.1 settings:

Automatic Config DHCP
Subnet Mask 255.255.255.0
Basic Wireless Setting: Manual Configuration, Mixed Wireless Network Mode, Enable SSID

In the 'Status' tab of the router config (under Auto Configuration DHCP) I do notice that the IP address, and subnet mask are all zeros if this is any significance.

Some info for when direct line is plugged into router:

1.  using Ubunty 9.04
 
2.  "sudo vi /etc/network/interfaces" shows:
auto lo
iface lo inet loopback

3.  "route" shows:
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     1      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0

4.  "if config" shows:
eth0      Link encap:Ethernet  HWaddr 00:11:11:47:de:ea  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::211:11ff:fe47:deea/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:88344 errors:0 dropped:0 overruns:0 frame:0
          TX packets:23706 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:22917538 (22.9 MB)  TX bytes:5437169 (5.4 MB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:61 errors:0 dropped:0 overruns:0 frame:0
          TX packets:61 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5228 (5.2 KB)  TX bytes:5228 (5.2 KB)

wlan0     Link encap:Ethernet  HWaddr 00:14:a5:d5:9a:5b  
          inet6 addr: fe80::214:a5ff:fed5:9a5b/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-14-A5-D5-9A-5B-61-35-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

5.  I have gone in through GRUB and used the option to repair as well.

Any assistance the community can be offer would be much appreciated.

---

### Post by Iowan on 2009-06-14
**route** doesn't show a gateway...
Although you can add one with **route add default gw** - it seems curious that the router doesn't provide that information.

---

### Post by bendavis77 on 2009-06-15
> **Iowan said:**
> **route** doesn't show a gateway...
Although you can add one with **route add default gw** - it seems curious that the router doesn't provide that information.

Still does not get the internet operational, thanks though.  I added a default gateway, but a couple bizarre things happened.  The gateway that entered one time appears twice.  The second odd piece is that it lists the first 2 gateways quickly... then there's a 15sec pause and then it lists the duplicate default gateways that i added.

Route now says:

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     1      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0
default         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
default         192.168.1.1     0.0.0.0         UG    0      0        0 eth0

---

### Post by jhannah on 2009-06-17
Is it possible you ran the route add default gw command more than once? You can actually have more than one default gateway but it is almost always a mistake. You can delete one of them by running:

```
route del default
```

That being said, it sounds like there is still something else going on. Are you able to ping the default gateway? This should work with or without the default route in place since you are directly connected to that network. If you cannot reach the default gateway, check out the ARP table as well to see if your machine is learning the MAC address for it:

```
arp -na
```

Considering your DHCP server didn't give you a default gateway, there is a good chance you also do not have any name servers setup. What are the contents of /etc/resolv.conf?

Lastly, the delay is probably just in name resolution, try running the below and see if that speeds it up:

```
route -n
```

---

### Post by alphacrucis2 on 2009-06-17
> **bendavis77 said:**
> 
Router setup via 192.168.1.1 settings:

Automatic Config DHCP
Subnet Mask 255.255.255.0
Basic Wireless Setting: Manual Configuration, Mixed Wireless Network Mode, Enable SSID

In the 'Status' tab of the router config (under Auto Configuration DHCP) I do notice that the IP address, and subnet mask are all zeros if this is any significance.



I would say that is of great significance if it applies to the upstream link.. Your router can't talk upstream if it has no IP address. You say that if you plug your PC in direct to the cable modem everything works? Are you using the same cable to connect  between the modem and router that you used between the modem and PC? If not then I would suspect the cable.

---

### Post by bendavis77 on 2009-06-18
jhannah...

I probably did put the command for Default GW 2x with all the different solutions I was trying.

ping 192.168.1.1 shows:
64 bytes from 192.168.1.1: icmp_seq=2 ttl=64 time=0.825 ms

/etc/resolv.conf shows:
# Generated by NetworkManager
nameserver 192.168.1.1

route -n does take that delay away


alphacrucis2...
Good thinking, but I neglected to say that I've tried ruling out the cables as well.  Sorry I forgot to mention that.

---

