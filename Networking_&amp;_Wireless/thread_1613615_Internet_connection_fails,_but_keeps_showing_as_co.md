---
title: "Internet connection fails, but keeps showing as connected"
date: 2010-11-04
forum: Networking &amp; Wireless
---

### Post by lacker on 2010-11-04
Every five or ten minutes my internet connection fails. I'm using Lucid Lynx, but was originally using Karmic Koala and this problem only appeared after I upgraded. When I disconnect from the wireless network and then reconnect, it starts working again, but it's pretty annoying.

When the connection fails, it doesn't seem to be a problem with the wireless connection because I can still ping my router (buffalo nfinity, default firmware) at 192.168.11.1 when this happens. I just can't reach anything on the outside internet. The wireless connection uses WPA2-PSK.

I'm not sure how exactly to debug from here. I'd appreciate any tips. Thanks in advance!

In case it helps, the output of iwconfig:

wlan0     IEEE 802.11abgn  ESSID:"lackerue"  
          Mode:Managed  Frequency:2.442 GHz  Access Point: 00:24:A5:AF:24:F6   
          Bit Rate=78 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=43/70  Signal level=-67 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


Output of ifconfig:

wlan0     Link encap:Ethernet  HWaddr 00:21:00:eb:85:63  
          inet addr:192.168.11.2  Bcast:192.168.11.255  Mask:255.255.255.0
          inet6 addr: fe80::221:ff:feeb:8563/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:181640 errors:0 dropped:0 overruns:0 frame:0
          TX packets:153493 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:105550845 (105.5 MB)  TX bytes:20277599 (20.2 MB)

---

### Post by ratcheer on 2010-11-04
I had the same, or very similar problem a couple of days ago. No one responded, but here is the thread I posted. It tells how I worked around the problem, but it is still a mystery to me.

[http://ubuntuforums.org/showthread.php?t=1612503](http://ubuntuforums.org/showthread.php?t=1612503)

Tim

---

### Post by lacker on 2010-11-04
For what it's worth, I tried setting "DHCP addresses only" and it did not fix the problem.

Some extra information: lshw -C network shows:


  *-network               
       description: Wireless interface
       product: AR928X Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 01
       serial: 00:21:00:eb:85:63
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k ip=192.168.11.2 latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:17 memory:f9ff0000-f9ffffff

---

