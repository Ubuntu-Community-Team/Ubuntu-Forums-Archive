---
title: "Problem connecting: Netgear wg311v3 adapter / Ubuntu lucid 10.04 / Dell XPS Studio"
date: 2010-10-06
forum: Networking &amp; Wireless
---

### Post by ohhai on 2010-10-06
Hi all,

I'm having a problem getting wireless set up on ubuntu lucid using the Netgear wg311v3 wireless pci adapter. I followed the instructions in this article ([http://ja.meswilson.com/blog/2007/03/11/wg311v3-64-bit-driver/](http://ja.meswilson.com/blog/2007/03/11/wg311v3-64-bit-driver/)), using the 64-bit driver and ndiswrapper, but after getting the driver installed, "wlan0" does not show up when I run iwconfig. PLEASE HELP! Here is some more info:


```

ndiswrapper -l
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
wg311v3 : driver installed
    device (11AB:1FAA) present

``````

iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

``````

 ifconfig
eth0      Link encap:Ethernet  HWaddr a4:ba:db:fb:0b:1a  
          inet addr:192.168.1.12  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::a6ba:dbff:fefb:b1a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4081 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2716 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4240305 (4.2 MB)  TX bytes:460951 (460.9 KB)
          Interrupt:33 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:960 (960.0 B)  TX bytes:960 (960.0 B)

``````

 lspci | grep Marvell
01:00.0 Ethernet controller: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 03)


``````

uname -mr
2.6.32-24-generic x86_64

```Thanks!!

---

### Post by kreggz on 2010-10-06
In the past I have found the GUI method to work well which is documented here:

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

ndisgtk is the package

---

