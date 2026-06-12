---
title: "sporadic internet following conversion to ubuntu from w7"
date: 2010-07-16
forum: Networking &amp; Wireless
---

### Post by abble455 on 2010-07-16
I'm really new to Ubuntu so please excuse my naiveté.  Basically, my problem is a slow and sporadic Internet.  I just moved from Windows 7 where everything worked fine, or at least at a level where I didn't notice the occasional glitch. My symptoms when running Ubuntu using Firefox and Transmission:

[LIST]
[*]    overall the speed is considerably slower -- nytimes.com used to take less than 5" to load but now takes >20-30"
[/LIST]

[LIST]
[*]    I often have to click a link twice, as the first click only leads to a 'Server not found' error
[/LIST]

[LIST]
[*]    Web pages often have formatting errors -- images don't load, links/text are set to the right of the page, etc.
[/LIST]

[LIST]
[*]    my Torrent downloads have ground to a halt -- I routinely downloaded ~200 kb/s but not it's more like 20 kb/s
[/LIST]

Here are some details...not sure if all of this is relevant for diagnosis...if somebody has an idea and needs to know more, please let me know, and I can gather more specs.

**lshw -C network**

*-network
                description: Wireless interface
                product: AR5001 Wireless Network Adapter
                vendor: Atheros Communications Inc.
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: wlan0
                version: 01
                serial: 
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical wireless logical
                configuration: broadcast=yes driver=ath5k latency=0 multicast=yes promiscuous=yes wireless=IEEE 802.11bg
                resources: irq:17 memory:fd9f0000-fd9fffff

**iwconfig**

wlan0     IEEE 802.11bg  ESSID:"2WIRE538"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: XX:XX:XX:XX:XX   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-34 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

**ifconfig**

wlan0     Link encap:Ethernet  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1039349 errors:0 dropped:0 overruns:0 frame:0
          TX packets:914892 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:937033444 (937.0 MB)  TX bytes:500202396 (500.2 MB)


Oh, I found an NSF funded study on internet service providers and other  stuff I don't understand.  They have a diagnostic tool (M-Lab) that I  ran. I ran the network application test which said TCP is incorrectly configured...e.g. not using SACK, did not  negotiate window scale.

---

### Post by abble455 on 2010-07-16
The issue appears to be Firefox.  I just installed Chrome and am browsing faster than ever.  Goodbye Firefox.

---

