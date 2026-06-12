---
title: "Wireless packet loss goes to 100% after ~20 requests"
date: 2011-09-18
forum: Networking &amp; Wireless
---

### Post by think13 on 2011-09-18
I have Comcast cable internet and I'm using a Motorola SB6120 modem connected to a Linksys WRT54GL router. My desktop is connected to the router via Ethernet and internet always works great.

However, my laptop (running Ubuntu 10.10) connects via wireless, and for each web request, packet loss seems to go up. After about 20 requests, the packet loss reaches 100%, and I can't even ping the gateway. The laptop reports that it is still connected to wireless with a strong signal.

Disconnecting and reconnecting to the access point doesn't help, as well as logging out and back in. However, after a restart, Internet works again for about 20 requests.

So far, I have tried updating the firmware on the router, setting the MTU to 1500 instead of Auto, and giving my laptop a static IP address. None of these have done anything to help the issue.

The noise level doesn't seem too high (-120dBm). Some other things which may be relevant are that the access point is open (I want to try sharing my connection with whoever wants it), and I am in an apartment building near a university, so there are tons of wireless access points in the area.

I originally thought that it was a router configuration issue, but disconnect/reconnect not working and restarting working makes me thing it may be an ubuntu issue.

Here is the output of some diagnostic commands I ran:
```
david@david-ThinkPad-T410:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     802.11bg  ESSID:"YouWouldntStealAnInternet"  Nickname:"rtl8191SEVA2"
          Mode:Managed  Frequency=2.412 GHz  Access Point: C0:C1:C0:AB:2E:42   
          Bit Rate=11 Mb/s   
          Retry:on   RTS thr:off   Fragment thr:off
          Power Management period:0us  mode:All packets received
          Link Quality=100/100  Signal level=-51 dBm  Noise level=-120 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

vboxnet0  no wireless extensions.

david@david-ThinkPad-T410:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr f0:de:f1:56:89:af  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:20 Memory:f2600000-f2620000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3819 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3819 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:192710 (192.7 KB)  TX bytes:192710 (192.7 KB)

wlan0     Link encap:Ethernet  HWaddr 68:a3:c4:29:88:32  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::6aa3:c4ff:fe29:8832/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:13408 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13507 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:11017565 (11.0 MB)  TX bytes:1947031 (1.9 MB)
          Interrupt:17 Memory:f8918000-f8918100

david@david-ThinkPad-T410:~$ ping 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
From 192.168.1.100 icmp_seq=1 Destination Host Unreachable
From 192.168.1.100 icmp_seq=4 Destination Host Unreachable
^C
--- 192.168.1.1 ping statistics ---
5 packets transmitted, 0 received, +2 errors, 100% packet loss, time 4016ms
```

---

### Post by think13 on 2011-09-18
Bumping this to get it back to the front page. 
Edit: The Quality of Service settings on my router only apply to wired connections, so I can't favor my laptop over everyone else.

I'm just gonna try adding security, and see what happens.

---

