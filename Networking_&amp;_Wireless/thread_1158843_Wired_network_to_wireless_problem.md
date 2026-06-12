---
title: "Wired network to wireless problem"
date: 2009-05-14
forum: Networking &amp; Wireless
---

### Post by danielsbrewer on 2009-05-14
Hello,

I have an ubuntu box with both a wireless and wired interface and I would like to use it to allow my XBMC xbox to connect to the internet.

This is he setup

Internet ---- Wireless router (192.168.0.1) ---- wlan0 ubuntu box eth0 ---- xbox

wlan0: inet addr:192.168.0.8  Bcast:192.168.0.255  Mask:255.255.255.0
eth0: inet addr:192.168.2.1  Bcast:192.168.2.255  Mask:255.255.255.0
xbox: inet addr:192.168.2.2  Bcast:192.168.2.255  Mask:255.255.255.0

Here is the route table for the ubuntu box:
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.2.0     *               255.255.255.0   U     0      0        0 eth0
192.168.0.0     *               255.255.255.0   U     0      0        0 wlan0
link-local      *               255.255.0.0     U     1000   0        0 wlan0
default         tomato.brewer.m 0.0.0.0         UG    100    0        0 wlan0

The ubuntu box can access the internet/wireless router fine.

The xbox can ping 192.168.2.1 successfully but fails when trying to ping 192.168.0.1.

This setup seems he same as [http://ubuntuforums.org/archive/index.php/t-60424.html](http://ubuntuforums.org/archive/index.php/t-60424.html) bu doesn't work.

Could you tell me where I am going wrong?

---

### Post by Peter09 on 2009-05-14
In your route command you have this line

> default         tomato.brewer.m 0.0.0.0         UG    100    0        0 wlan0

This is incorrect as it requires knowledge of the IP address of your gateway to get to your gateway .....

add this line

```
[FONT=Arial][SIZE=2]**route add default gw {IP-ADDRESS} {INTERFACE-NAME}**[/SIZE][/FONT] 
```

replacing the defaults with your data. ipaddress is that of your gateway

---

### Post by danielsbrewer on 2009-05-14
Many thanks for that.  Could you tell me where to add the route comand? I have got a server install and I use the /etc/networks/interfaces file to config the nics.

I tried just doing "sudo route add default gw 192.168.0.1 eth0" and get
SIOCADDRT: No such process

---

### Post by Peter09 on 2009-05-14
Try entering the command into a terminal

Applications->Accessories->Terminal

---

### Post by Iowan on 2009-05-14
**man route** doesn't show the interface name.>        **route add default gw mango-gw**
              adds a default route (which will  be  used  if  no  other  route
              matches).   All  packets  using  this  route  will  be gatewayed
              through "mango-gw". The device which will actually be  used  for
              that  route  depends on how we can reach "mango-gw" - the static
              route to "mango-gw" will have to be set up before.
although it DOES list it as an option:> **dev If **force  the  route to be associated with the specified device, as
              the kernel will otherwise try to determine the device on its own
              (by  checking already existing routes and device specifications,
              and where the route is added to). In most  normal  networks  you
              won&#8217;t need this.

              If  dev  If is the last option on the command line, the word dev
              may be omitted, as it&#8217;s the default. Otherwise the order of  the
              route modifiers (metric - netmask - gw - dev) doesn&#8217;t matter.


---

### Post by danielsbrewer on 2009-05-15
> **Peter09 said:**
> Try entering the command into a terminal

Applications->Accessories->Terminal

That's not that helpful I'm afraid as:
1) I am running server and so have no gui
2) Said I typed in the command and showed the error

So I tried Iowan's suggestion i.e.
sudo route add default gw 192.168.0.1 

and that was accepted and route looks like:
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.2.0     *               255.255.255.0   U     0      0        0 eth0
192.168.0.0     *               255.255.255.0   U     0      0        0 wlan0
link-local      *               255.255.0.0     U     1000   0        0 wlan0
default         tomato.brewer.m 0.0.0.0         UG    0      0        0 wlan0
default         tomato.brewer.m 0.0.0.0         UG    100    0        0 wlan0

I don't undersand where it is getting the tomato stuff from apart from DNS.

/etc/network/interfaces looks like this:
```
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet static
address 192.168.0.8
netmask 255.255.255.0
gateway 192.168.0.1
wireless-essid BrewerNet
wireless-key 63B6F3***************695CC
wireless-channel 9
wireless-mode managed

auto eth0
iface eth0 inet static
address 192.168.2.1
netmask 255.255.255.0
gateway 192.168.0.1

```

---

### Post by Peter09 on 2009-05-15
We need to see the routing information on your x-box, when you ping a machine not directily connected to the x-box it must recognize the path to use to get there.

---

### Post by danielsbrewer on 2009-05-15
I couldn' get the routing info from the xbox, so I plugged in a laptop setup in the same way.  Here is the info:
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.2.0     *               255.255.255.0   U     0      0        0 eth0
default         192.168.2.1     0.0.0.0         UG    0      0        0 eth0

```

Interestingly, it took a long time for the default line to appear.

Ping successful: 192.168.2.2, 192.168.2.1, 192.168.0.8
Ping unsuccessful: 192.168.0.1, 208.67.222.222 (opendns)

The router is running the tomato firmware.

Many thanks for looking at this I am at a complete loss.

---EDIT---

I cannot ping 192.168.2.1 from the router (192.168.0.1)

On ubuntu box the firewall is clear:
```

 sudo iptables -S
-P INPUT ACCEPT
-P FORWARD ACCEPT
-P OUTPUT ACCEPT

```

---

### Post by Peter09 on 2009-05-15
Think it works through as this ---

the Xbox can see the 192.168.2.xxx network 

I think this is the network that you have configured between the Ubuntu machine and the Xbox.

However the xbox cannot see the 192.168.0.xxx network which is the network that exists between the Ubuntu machine and the router and out to the internet.

I think you need to put a route into the Ubuntu machine that connects 192.168.2.0 to 192.168.0.0

---

