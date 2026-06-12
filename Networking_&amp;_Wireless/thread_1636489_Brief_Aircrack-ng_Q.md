---
title: "Brief Aircrack-ng Q"
date: 2010-12-03
forum: Networking &amp; Wireless
---

### Post by Spike-57 on 2010-12-03
_**Where I'm at**_
I'm running ubuntu on
HP pavilion dm3-1060ea (I've added it to the compatibility list)
Its all worked pretty much out of the box so far.

I'm trying to get aircrack-ng up and working (Computing student at uni) 

Below is my start-up ifconfig
```
 
ifconfig
wlan0     
          Link encap:Ethernet  HWaddr 00:32:d6:4c:d7:8d  
          inet addr:10.2.5.51  Bcast:10.2.7.255  Mask:255.255.252.0
          inet6 addr: fe80::224:d6ff:fe4c:d28c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2854 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2583 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2876916 (2.8 MB)  TX bytes:449850 (449.8 KB)

```turn my card off to stop any interference
```
 
sudo ifconfig wlan0 down

```launch airomon-ng
```
 
sudo airmon-ng start wlan0 7

Found 5 processes that could cause trouble.
If airodump-ng, aireplay-ng or airtun-ng stops working after
a short period of time, you may want to kill (some of) them!

PID    Name
944    NetworkManager
952    avahi-daemon
956    avahi-daemon
1038    wpa_supplicant
2494    dhclient
Process with PID 2494 (dhclient) is running on interface wlan0

Interface    Chipset        Driver

wlan0        Intel 4965/5xxx    iwlagn - [phy0]
                (monitor mode enabled on mon0)

```another ifconfig
```
 
ifconfig
mon0     
          Link encap:UNSPEC  HWaddr 00-32-D6-4C-D7-8D-30-30-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6766 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1940261 (1.9 MB)  TX bytes:0 (0.0 B)


```**now my question** is on the above code, is this the correct information you'd expect to see for a monitor enabled card? if not can anyone point me in the right direction?

also if their is any nice people out their that could explain to me why and what it indicates when the MAC address is that long!! I might be being **nieve** (heaven forbid) but I expect them to be in the format of 00:11:22:33:44:55, my atempts at googl-ing this have been unhelpful.

---

### Post by Spike-57 on 2010-12-03
Realised it might be a lack of patch problem, even though its working, my misreading of patch for driver :P

---

### Post by Spike-57 on 2010-12-15
I'm still having problems with this! Right

     Code:
      
ifconfig
wlan0     
          Link encap:Ethernet  HWaddr 00:32:d6:4c:d7:8d  
          inet addr:10.2.5.51  Bcast:10.2.7.255  Mask:255.255.252.0
          inet6 addr: fe80::224:d6ff:fe4c:d28c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2854 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2583 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2876916 (2.8 MB)  TX bytes:449850 (449.8 KB) 
sudo ifconfig wlan0 down
sudo macchanger -m 00:11:22:33:44:55 wlan0 
sudo ifconfig wlan0 up
ifconfig
<code>
wlan0     Link encap:Ethernet  HWaddr 00:11:22:33:44:55  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:887 errors:0 dropped:0 overruns:0 frame:0
          TX packets:714 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:287887 (287.8 KB)  TX bytes:148051 (148.0 KB)

</code>
sudo airmon-ng start wlan0
<code>
Found 5 processes that could cause trouble.
If airodump-ng, aireplay-ng or airtun-ng stops working after
a short period of time, you may want to kill (some of) them!

PID    Name
863    NetworkManager
873    avahi-daemon
877    avahi-daemon
900    wpa_supplicant
1969    dhclient
Process with PID 1969 (dhclient) is running on interface wlan0


Interface    Chipset        Driver

wlan0        Intel 4965/5xxx    iwlagn - [phy0]
                (monitor mode enabled on mon0)

</code>
i read the above warning however i don't think its what is causing my issues(will bang head on wall if it is)
ifconfig
<code>
mon0      Link encap:UNSPEC  HWaddr 00-24-D6-4C-D2-8C-30-30-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2835 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:722938 (722.9 KB)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:11:22:33:44:55  
          inet addr:192.128.100.38  Bcast:192.128.100.255  Mask:255.255.255.0
          inet6 addr: fe80::211:22ff:fe33:4455/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3483 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1724 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1544212 (1.5 MB)  TX bytes:383965 (383.9 KB)
</code>
 Absolutely mental mac address for the mon0 interface, is this significant? 

sudo airodump-ng mon0

<code>
 BSSID                      PWR  Beacons    #Data, #/s  CH  MB   ENC  CIPHER AUTH ESSID
00:50:7F:99:D3:88  -127      865             997   12   5    54e. WEP   WEP                 spamola
 00:19:E3:FB:3F:34  -60        0                0       0   7      54e. WPA2 CCMP   PSK      G Unit
 


BSSID              STATION            PWR   Rate    Lost  Packets  Probes
(not associated)   00:16:44:B6:55:7C  -79    0 - 1      0        4             
00:50:7F:99:D3:88  00:11:22:33:44:55    0    0 - 1e     0        4  spamola     

</code>
my target in the router ive set up with baddd security WEP ESSID = spamola
so
sudo airodump-ng -c 5 -w spamoladumpfile --bssid 00:50:7F:99:D3:88 mon0
sudo aireplay-ng -1 600 -e spamola -a 00:50:7F:99:D3:88 -h 00:11:22:33:44:55 mon0
<code>
The interface MAC (00:24:D6:4C:D2:8C) doesn't match the specified MAC (-h).
    ifconfig mon0 hw ether 00:11:22:33:44:55
19:02:40  Waiting for beacon frame (BSSID: 00:50:7F:99:D3:88) on channel -1
19:02:40  mon0 is on channel -1, but the AP uses channel 5
</code>
now this brings me back to the unusual mac address erlier, i think im doing somthing wrong here, any pointers??

Cheers !!

p.s I had to cut out a few wireless signals that were detected because of these crazy smiley, what's the escape character for them??

---

### Post by spiky001 on 2010-12-15
Hi I,m no expert with Aircrack, what happens with the pid running I still get airodump to work but it dose cause it to stop alot of the time, saying that I use BT4 so network wont start so I dont have to kill any processes, But it dose run with eth0 connected but complains the same as you get. Ifconfig looks ok to me. Try sudo kill -9 pid

---

