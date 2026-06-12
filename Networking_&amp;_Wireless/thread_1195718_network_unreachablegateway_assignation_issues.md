---
title: "network unreachable/gateway assignation issues"
date: 2009-06-24
forum: Networking &amp; Wireless
---

### Post by dai_bach on 2009-06-24
Hi,

I've recently installed the 64-bit version of 9.04 on a Dell Precision T7500 but am having a few issues with a connexion to the local network.  If I try pinging a arbitrary site, say [www.google.com](www.google.com), I get an error message informing me that the network is unreachable.  The problems seem to stem from an inability to assign a gateway in the IPv4 Settings.  Using System > Preferences > Network Connections fails to change it from the default value of 0.0.0.0.  I've found a workaround by typing the following commands in a shell just after startup:
```
ifconfig eth0 x.x.x.29
```
then 
```
route add -net 0.0.0.0 netmask 0.0.0.0 gw x.x.x.254
```
where x.x.x.29 and x.x.x.254 are my IP address and gateway, obviously.

This is all very well, but there must be a better solution than this.  Can anyone diagnose this initial problem?  At the very least, what can be done to avoid having to enter these commands at EVERY startup?  Please bare in mind that I'm a linux 'noob', so please be explicit in your responses!

Many thanks,
DB

p.s. my network card info is as follows:
```
*-network               
       description: Ethernet interface
       product: NetXtreme BCM5761 Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth0
       version: 10
       serial: 00:23:ae:90:51:56
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.94 firmware=5761-v3.68 ip=x.x.x.29 latency=0 module=tg3 multicast=yes
```

---

### Post by jhannah on 2009-06-24
Did you add the route for 0.0.0.0/0 under the 'Routes' button in NetworkManager? If not, that might do the trick but you can always use /etc/network/interfaces to setup your interface as well. To do so, simply remove the configuration from NetworkManager for your interface and use the template below:

```

auto eth0
iface eth0 inet static
  address **x.x.x.29**
  netmask **255.255.255.0**
  gateway **x.x.x.254**

```

Keep in mind you will need to put your nameservers in /etc/resolv.conf. Once done, just restart networking with:

```
/etc/init.d/networking restart
```

Let me know if that helps.

---

### Post by dai_bach on 2009-06-24
I'm pretty sure I tried adding the route through NetworkManager/NetworkConnections, and all that happened was the parameters boxes blanked themselves as soon as they had been filled in.  I've just tried again, and the network parameters don't seem to be vanishing anymore.  However, when I type "route" into a terminal, there are no gateway flags and I'm back to the same issue when pinging a site.
```
route
  Kernel IP routing table
  Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
  x.x.x.0         *               255.255.255.0   U     1      0        0 eth0
  link-local      *               255.255.0.0     U     1000   0        0 eth0
```

I will try your other method and report back with the results...

---

### Post by dai_bach on 2009-06-25
So the results are:
1) Network notification icon (in the tool bar) shows no activity, although I still have network access.  I guess this is due to not using NetworkManager to manage connections?
2) The result of typing "route" in a shell is as follows:
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
x.x.x.0         *               255.255.255.0   U     0      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0
default         x.x.x.254       0.0.0.0         UG    100    0        0 eth0

```
This output is similar to what I was receiving entering the two commands in my original post, except that the Metric value was 0.
3) I can no longer access my mail server.  This problem persists even if I do
```
sudo route del default
```
and then add the two lines as per the original post.

---

### Post by catalin.soare on 2009-09-16
[FONT=Arial][SIZE=2]I am having similar routing problems with Ubuntu 9.04, X64:
Whenever I start up my system, the Internet won't work unless I do:
[/SIZE][/FONT]```
sudo route add default gw 192.168.1.254
```[FONT=Arial][SIZE=2]
I tried to alter /etc/network/interfaces, but with no luck. After restart, it doesn't work. executing route prints:
[/SIZE][/FONT]```
catalin@lolinux:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     0      0        0 wlan0

```[FONT=Arial][SIZE=2]After I manually add the gateway, everything is fine, and route prints another gateway:
[/SIZE][/FONT]```
catalin@lolinux:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     0      0        0 wlan0
default         dsldevice.lan   0.0.0.0         UG    0      0        0 wlan0
```[FONT=Arial][SIZE=2]
Is there any difference from what I altered and the kernel routing table? If there is, how do I modify that? Or would a startup script be a better solution?
[/SIZE][/FONT]

---

