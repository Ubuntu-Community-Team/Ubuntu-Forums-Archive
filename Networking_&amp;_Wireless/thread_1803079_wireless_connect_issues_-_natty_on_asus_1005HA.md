---
title: "wireless connect issues - natty on asus 1005HA"
date: 2011-07-12
forum: Networking &amp; Wireless
---

### Post by wrnh on 2011-07-12
Good morning,

I've just completed a fresh install of 11.04 on an ASUS 1005HA laptop. The machine ran 10.04 successfully for many months.  My** wired ethernet connection works**. My **wireless connection - when I connect to an unprotected network** - works.** Attempts to connect to a WPA2 secured network** - which worked under 10.04 - fail.  

I've upgraded 11.04 with no visible change and looked at a bunch of forum posts that propose various random solutions. A new kernal? Adding a configuration file? Something else? Can someone walk me through the debug so I can figure out what is going on?

I am running Ubuntu 11.04 version 2.6.38-8-generic i686
[U]
here's the results of lshw -C network:[/U]

*-network
       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: 00:25:d3:45:ac:e9
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=2.6.38-8-generic firmware=N/A ip=172.16.42.2 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:fbff0000-fbffffff
[U]
ifconfig dump (when connected to open network):[/U]

[FONT=Fixedsys]wlan0     Link encap:Ethernet  HWaddr 00:25:d3:45:ac:e9  
          inet addr:172.16.42.2  Bcast:172.16.42.255  Mask:255.255.255.0
          inet6 addr: fe80::225:d3ff:fe45:ace9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:34 errors:0 dropped:0 overruns:0 frame:0
          TX packets:54 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5426 (5.4 KB)  TX bytes:13033 (13.0 KB)

_ lspci dump:_

[FONT=Fixedsys]02:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
    Subsystem: AzureWave Device 1089
    Flags: bus master, fast devsel, latency 0, IRQ 17
    Memory at fbff0000 (64-bit, non-prefetchable) [size=64K]
    Capabilities: [40] Power Management version 3
    Capabilities: [50] MSI: Enable- Count=1/1 Maskable- 64bit-
    Capabilities: [60] Express Legacy Endpoint, MSI 00
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [140] Virtual Channel
    Capabilities: [160] Device Serial Number 00-15-17-ff-ff-24-14-12
    Capabilities: [170] Power Budgeting <?>
    Kernel driver in use: ath9k
    Kernel modules: ath9k[/FONT]
____

thanks for any help on this!

- bill


[/FONT]

---

### Post by garvinrick4 on 2011-07-12
Here is a link for ath drivers

[http://ubuntuforums.org/showthread.php?t=1686282](http://ubuntuforums.org/showthread.php?t=1686282)

Read chili555 posts your driver is ath9k instead of ath5k

Look at post 8 and 10 change to ath9k.
Have seen this work in ath9k above.
If does not work you are going to have to do the compat-wireless stable thru synaptics
or from their site.
[http://linuxwireless.org/en/users/Download/stable/](http://linuxwireless.org/en/users/Download/stable/)

---

### Post by wrnh on 2011-07-12
[QUOTE=garvinrick4;11041780]Here is a link for ath drivers

[http://ubuntuforums.org/showthread.php?t=1686282](http://ubuntuforums.org/showthread.php?t=1686282)

Read chili555 posts your driver is ath9k instead of ath5k

Look at post 8 and 10 change to ath9k.
Have seen this work in ath9k above.

______

Tried the suggested "nohwcrypt" fix.  Doesn't seem to have any effect. Before I try the backport, I am going to run some experiments on my wireless router (an airport) to be sure that I don't have some other weird problem. More information to follow.

---

### Post by wrnh on 2011-07-12
More information:

I am using an Airport Extreme, V7.5.2.  I am running a wireless network with MAC access control lists and a wired network.  There are four laptops (OSX and Ubuntu), two desktops and three printers in the network. There were no changes in the network or the laptop, other than the clean install of 11.04.

When I turn off network security, I am able to connect.  When I turn on WPA/WPA2 password, I am able to connect. When I turn on WPA/WPA2 *and* MAC access control on the Airport Extreme, I **cannot** connect.  Looking at the Airport logs I can see the the troubled laptop associating with the router, getting a key installed and dissassociating over thirty seconds. 

Is this a problem with the supplicant software? Why would MAC access control (assuming I have the control list set up correctly, which I do) cause the laptop to burp when it tries to connect?

---

