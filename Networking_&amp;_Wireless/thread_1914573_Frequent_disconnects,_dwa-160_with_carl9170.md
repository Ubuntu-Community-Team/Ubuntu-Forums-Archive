---
title: "Frequent disconnects, dwa-160 with carl9170"
date: 2012-01-24
forum: Networking &amp; Wireless
---

### Post by Rodiath on 2012-01-24
Hi!

I'm new to this linux business and having a rough time figuring out something. 
My internet seems to work well when it works, and I would say of the time it does. 
Often though, I get disconnected, and this is where the trouble starts. Edit: Actually it seems to be happening all the time now :x (maybe when it is under greater load, like torrents + streaming or something)
Usually it reconnects and loses connection again seconds later. This can resolve itself on its own, or go on and on for a long time, sometimes a whole day. Is this just a signal issue or are my drivers messed up somehow?

iwconfig wlan0 gives me:

wlan0     IEEE 802.11abgn  ESSID:"casaemdal"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:21:96:4C:B2:C0   
          Bit Rate=48 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=31/70  Signal level=-79 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:5  Invalid misc:23   Missed beacon:0

ifconfig wlan0 gives me:

wlan0     Link encap:Ethernet  HWaddr fc:75:16:86:52:d2  
          inet addr:192.168.10.105  Bcast:192.168.10.255  Mask:255.255.255.0
          inet6 addr: fe80::fe75:16ff:fe86:52d2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4954 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2919 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2642527 (2.6 MB)  TX bytes:676428 (676.4 KB)

sudo lshw -C network, the info about the wireless, says:

*-network
       description: Wireless interface
       physical id: 1
       bus info: usb@1:2
       logical name: wlan0
       serial: fc:75:16:86:52:d2
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=carl9170 driverversion=3.0.0-15-generic-pae firmware=1.9.2 ip=192.168.10.105 link=yes multicast=yes wireless=IEEE 802.11abgn


I am running ubuntu 11.10, the wireless card is D-Link System DWA-160 Xtreme N Dual Band USB Adapter(rev.A2) [Atheros AR9001U-(2)NG]

Help would be greatly appreciated!

---

### Post by Rodiath on 2012-02-04
I am thinking perhaps it could be that carl9170 is causing the device to overheat under load, so that it turns itself off. Change of driver maybe?

---

