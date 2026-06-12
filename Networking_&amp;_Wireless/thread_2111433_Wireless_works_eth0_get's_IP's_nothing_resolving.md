---
title: "Wireless works eth0 get's IP's nothing resolving"
date: 2013-02-01
forum: Networking &amp; Wireless
---

### Post by TheKoolAidGuy on 2013-02-01
Alright so I am having some issues with my Ubuntu installation, I am running 12.04LTS.

As of right now I am on my Ubuntu install however I'm under my WiFi connection which functions great! However when I plug in with my ethernet cord it shows I am connected I get all the IP's and everything but I can not ping and I can't browse anywhere within my browser.

I have searched the internet high and low for a possible fix but I haven't had much for luck.

I tried to look here for a resolution to but it seems it can vary depending on the card.

---

### Post by ahallubuntu on 2013-02-01
Please open a terminal and show the output of these commands:

```
sudo lshw -C network
ifconfig

```

---

### Post by TheKoolAidGuy on 2013-02-01
```
*-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 06
       serial: 10:1f:74:0d:7d:c6
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8168e-3_0.0.4 03/27/12 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:52 ioport:2000(size=256) memory:f0004000-f0004fff memory:f0000000-f0003fff
  *-network
       description: Wireless interface
       product: RT5390 Wireless 802.11n 1T/1R PCIe
       vendor: Ralink corp.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 00
       serial: 38:59:f9:3c:58:79
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2800pci driverversion=3.2.0-29-generic firmware=0.34 ip=10.81.98.83 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:f0200000-f020ffff

```

```
eth0      Link encap:Ethernet  HWaddr 10:1f:74:0d:7d:c6  
          inet6 addr: fe80::121f:74ff:fe0d:7dc6/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:23987 errors:0 dropped:248 overruns:0 frame:0
          TX packets:565 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2049922 (2.0 MB)  TX bytes:60103 (60.1 KB)
          Interrupt:52 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4270 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4270 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:544707 (544.7 KB)  TX bytes:544707 (544.7 KB)

wlan0     Link encap:Ethernet  HWaddr 38:59:f9:3c:58:79  
          inet addr:10.81.98.83  Bcast:10.81.127.255  Mask:255.255.192.0
          inet6 addr: fe80::3a59:f9ff:fe3c:5879/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:253745 errors:0 dropped:0 overruns:0 frame:0
          TX packets:97141 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:227487049 (227.4 MB)  TX bytes:11158590 (11.1 MB)

```

P.S. it's not gonna show any ip's for eth0 right now because I have to unplug the ethernet cord in order for the Wi-Fi to work right.

---

### Post by ahallubuntu on 2013-02-01
Looks like you're not getting "all the IPs" from the wired connection - ifconfig shows you aren't getting an IP at all.

Disable wireless completely.  Unplug the ethernet cable, wait 10 seconds (or until you see connection drop for wired in Network Manager), then plug it back in. Exactly what happens?

---

### Post by TheKoolAidGuy on 2013-02-01
> I do get IP's as I stated at the end of my post I currently have it unplugged in order for my WiFi to work...however I will plug it back in and show you.


```
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 06
       serial: 10:1f:74:0d:7d:c6
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8168e-3_0.0.4 03/27/12 ip=10.80.81.83 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:52 ioport:2000(size=256) memory:f0004000-f0004fff memory:f0000000-f0003fff
  *-network
       description: Wireless interface
       product: RT5390 Wireless 802.11n 1T/1R PCIe
       vendor: Ralink corp.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 00
       serial: 38:59:f9:3c:58:79
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2800pci driverversion=3.2.0-29-generic firmware=0.34 ip=10.81.98.83 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:f0200000-f020ffff
```

```
eth0      Link encap:Ethernet  HWaddr 10:1f:74:0d:7d:c6  
          inet addr:10.80.81.83  Bcast:10.80.81.255  Mask:255.255.254.0
          inet6 addr: fe80::121f:74ff:fe0d:7dc6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:27831 errors:0 dropped:286 overruns:0 frame:0
          TX packets:709 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2354066 (2.3 MB)  TX bytes:80840 (80.8 KB)
          Interrupt:52 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4810 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4810 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:607371 (607.3 KB)  TX bytes:607371 (607.3 KB)

wlan0     Link encap:Ethernet  HWaddr 38:59:f9:3c:58:79  
          inet addr:10.81.98.83  Bcast:10.81.127.255  Mask:255.255.192.0
          inet6 addr: fe80::3a59:f9ff:fe3c:5879/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:289103 errors:0 dropped:0 overruns:0 frame:0
          TX packets:99588 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:234448707 (234.4 MB)  TX bytes:11517956 (11.5 MB)
```

---

### Post by N00b-un-2 on 2013-02-01
try deleting /etc/udev/rules.d/70-persistent-net.rules and then rebooting.

---

### Post by steeldriver on 2013-02-01
you appear to have a smaller IP range (based on the netmask / broadcast) for eth0 versus wlan0 - are you sure the router / gateway is not just outside the eth0-implied host range?

---

### Post by TheKoolAidGuy on 2013-02-01
Everything should work just fine, considering the fact that when I boot into my Windows partition on this computer everything works 100% perfect. I have also done nothing to modify any configurations on this computer everything is as it was when I installed the O.S.

Also this is on a college network so this may be why as well however wouldn't be the reason for this to not be working.

---

### Post by ahallubuntu on 2013-02-01
You're connecting to two different networks.  The wired and wireless get very different parameters.  Presumably Ubuntu is choosing the wired as the default gateway and can't get out, which is why nothing works until you unplug the ethernet cable.

Disable wireless, connect with wired and see if you can ping an IP (not a name).  Try pinging one of Google's servers:

```
ping 173.194.33.0
```

If that works, then you just have a DNS problem.  If it doesn't work, it's something else.  Then, unplug the wired, re-connect with wireless, and install traceroute:

```
sudo apt-get install traceroute
```

While you're on wireless, try a traceroute to that same IP:

```
traeceroute 173.194.33.0
```

which should produce a line for each "hop" on the network - may take a few seconds for it to complete.

Now, disable wireless again, re-connect with wired and try the traceroute again.  (might want to run it in a separate terminal window so you can compare output from the wireless one.)  Where does it get stuck?

---

### Post by TheKoolAidGuy on 2013-02-01
ping with the wired connection get's a destination host unreachable.

Doing the traceroute on the wireless goes 14 hops and gives *** after that.

The wired connection fails on the first hop and continues failing all the way through.

---

### Post by ahallubuntu on 2013-02-01
Have you tried plugging your computer into anything else besides the college network?  A spare router?  (Even if not connected to anything, just to see if you can get to the router's admin page.)  Just to figure out whether the wired card works AT ALL in Ubuntu or whether there's some issue connecting to your college network.

---

### Post by TheKoolAidGuy on 2013-02-02
Unfortunately I don't have anything else I can connect into :/

I'm not having any luck with pinging IP's except for my own and of course my loop back address.

---

### Post by SeijiSensei on 2013-02-02
First, notice that you are getting the same IP address on both interfaces.  That's a big problem right there.

The simplest solution is to turn off the wifi adapter when you are connected to the wired network.  Most computers let you do this easily with an Fn key.  Fn-F12 seems like a popular choice.  Usually this key will have a little radio tower icon on it.

---

### Post by TheKoolAidGuy on 2013-02-07
Seiji, please be sure to read the entirety of the thread, I have tried that. Thank you

---

### Post by wildmanne39 on 2013-02-07
Hi, please post the outcome of:
```
lspci -nnk | grep -iA2 net
```
I suspect that it is the driver.
Thanks

---

