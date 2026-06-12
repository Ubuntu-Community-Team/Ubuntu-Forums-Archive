---
title: "(eeebuntu) wifi network detected, won't connect"
date: 2009-07-25
forum: Networking &amp; Wireless
---

### Post by ferth on 2009-07-25
I just got a Asus 1005ha and decided to immediately put linux on it. I have Xubuntu on my other laptop and decided to go with eeebuntu (NBR) on this one.

Anyway, my problem after getting the ethernet working is that the wifi network is detected and shown by network manager but when I try to connect it tries connecting for twenty or thirty seconds and then just says that it's disconnected.

The only answer I've really found was installing the backports, which I did (it did get me to the point of being able to see the networks, as before that I had no wifi function), but it doesn't fix my problem.

I'll give you all the information that I can think of (which isn't much), but if you need more, ask and I'll get it to you.

[[IMG]http://img.photobucket.com/albums/v141/mukodta/th_Screenshot.jpg[/IMG]](http://smg.photobucket.com/albums/v141/mukodta/?action=view&current=Screenshot.jpg)

```
daniel@daniel-laptop:~$ sudo lshw -C network
  *-network               
       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wmaster0
       version: 01
       serial: 00:25:d3:09:b7:e8
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath9k latency=0 module=ath9k multicast=yes wireless=IEEE 802.11bgn
  *-network
       description: Ethernet interface
       product: Attansic Technology Corp.
       vendor: Attansic Technology Corp.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: c0
       serial: 00:26:18:2b:ab:d9
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=ATL1C driverversion=1.0.0.9 duplex=full firmware=L1e ip=192.168.2.5 latency=0 link=yes module=atl1e multicast=yes port=twisted pair speed=100MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: de:fd:38:51:6b:b3
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
```
```
daniel@daniel-laptop:~$ iwconfig wlan0
wlan0     IEEE 802.11bgn  ESSID:"linksys"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```
```
lspci
01:00.0 Ethernet controller: Attansic Technology Corp. Device 1062 (rev c0)
02:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network
```

I'm not sure exactly what this means, but I'll go ahead and give it to y'all just in case it's important.
```
daniel@daniel-laptop:~$ sudo ifup wlan0
Ignoring unknown interface wlan0=wlan0.
daniel@daniel-laptop:~$ sudo ifdown wlan0
ifdown: interface wlan0 not configured
```
```
daniel@daniel-laptop:~$ lsmod | grep ath9k
ath9k                 215432  0 
mac80211              171352  1 ath9k
led_class               3676  1 ath9k
```

---

### Post by superprash2003 on 2009-07-26
it looks like the network is not secure with any key?have you tried setting up static ip on your ubuntu machine? it looks like your able to connect but not able to receive an ip address from your linksys router

---

### Post by Bucky Ball on 2009-07-26
Atheros card: should be ath0 I think, not wlan0 (it is on the machine I built with Atheros wireless chipset).

Result of:

```
ifconfig
```and 

```
iwconfig
```... please.


* As above. Your router needs to be set as DHCP server to give you an IP for the network. Get into the config and check. Also check the ESSID and WEP or WPA security key on your router in the wireless section and make sure they match on your machine under System->Admin->Network

Enable roaming off;
Correct ESSID and key (matches details in router or 'AP' (access point);
Set to 'Configuration: Autoconfiguration (DHCP)'

---

### Post by ferth on 2009-07-26
```
eth0      Link encap:Ethernet  HWaddr 00:26:18:2b:ab:d9  
          inet addr:192.168.2.5  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::226:18ff:fe2b:abd9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:588 errors:0 dropped:0 overruns:0 frame:0
          TX packets:609 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:630708 (630.7 KB)  TX bytes:97786 (97.7 KB)
          Interrupt:28 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:96 errors:0 dropped:0 overruns:0 frame:0
          TX packets:96 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:7728 (7.7 KB)  TX bytes:7728 (7.7 KB)

wlan0     Link encap:Ethernet  HWaddr 00:25:d3:09:b7:e8  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-25-D3-09-B7-E8-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```
```
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"linksys"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.
```

I have no password for my router. I changed to static, but no dice.

Thanks guys.

---

### Post by Bucky Ball on 2009-07-26
```

wlan0     IEEE 802.11bgn  ESSID:"linksys"  
          Mode:Managed  Frequency:2.437 GHz  **Access Point: Not-Associated **  
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```That's your problem. There must be a detail wrong somewhere. You must make sure you router is setup as an access point. I would google:

> **Access Point: Not-Associated** Ubuntu... and see what you dig up. Have you had the machine online with an ethernet cable an gotten your updates, BTW? If not I strongly recommend you do it. You will quite possibly be offered the Restricted Drivers for your card also which will find your network for you and ask for correct key if required. But it must have an access point to recognise.

---

### Post by Cotopaxi on 2009-07-26
I have had a similar problem with network manager (in my case: k-network manager from Kubuntu).

Try the following:

1-make a wired connection to your router, 
2-open your package manager
3-install &#8220;wicd&#8221; network manager.

The wicd manager will deinstall your network manager but wicd will solve your problems!

The web page of wicd is:

[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

I hope this helps!

---

### Post by Cotopaxi on 2009-07-26
One more comment:

If you have &#8220;Firestarter&#8221; a (graphical front-end for Iptables) installed, DEINSTALL IT!

Firestarter has been blocking all internet connection attempts and I finally followed the recommendation of a forum member and deinstalled it!

If you want to have a graphical front-end for Iptables, go with &#8220;Guarddog&#8221;, it works fine.

If you want to learn more about Guarddog, here is a link to the Guarddog handbook:

[http://www.simonzone.com/software/guarddog/manual2/]("http://www.simonzone.com/software/guarddog/manual2/")

again, I hope this helps!

---

### Post by ferth on 2009-07-26
Tried wicd, no luck and I don't have firestarter installed.

Trying the google search now, hopefully I'll find something.

---

### Post by Bucky Ball on 2009-07-27
Also, if you are serving DHCP from the router, set a password. That could make a difference. You can also try with 'Enable Roaming' clicked in the 'Network' setup on the computer instead of 'Automatic Configuration (DHCP) and see if it picks up your 'Linksys' network.

---

