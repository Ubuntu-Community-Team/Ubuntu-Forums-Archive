---
title: "Need troubleshooting help with AR5001 in Karmic"
date: 2009-11-28
forum: Networking &amp; Wireless
---

### Post by wbreslin951 on 2009-11-28
hey guys wuts up, ill try to make this short and sweet. I installed the madwifi driver for my AR5001 and for some reason its still not working. It won't scan for networks, it's not showing up in if or iwconfig at all, I'm at a complete loss here. I'm pretty sure it's supposed to show up as ath0 in iwconfig. Here's a few terminal outputs to possibly help you guys, thanks for the advice

lspci -nn:

02:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR5001 Wireless Network Adapter [168c:001c] (rev 01)

ifconfig:

eth0      Link encap:Ethernet  HWaddr 00:1f:16:6c:5e:0a  
          inet addr:192.168.1.24  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:16ff:fe6c:5e0a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:19257 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11950 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:14393694 (14.3 MB)  TX bytes:1675231 (1.6 MB)
          Interrupt:28 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:36 errors:0 dropped:0 overruns:0 frame:0
          TX packets:36 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2160 (2.1 KB)  TX bytes:2160 (2.1 KB)

iwconfig:

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by chili555 on 2009-11-28
> wlan0 IEEE 802.11bg ESSID:""
Mode:Managed Frequency:2.412 GHz Access Point: Not-Associated
Tx-Power=off
Retry long limit:7 RTS thr:off Fragment thr:off
Power Management:off
Link Quality:0 Signal level:0 Noise level:0
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0I believe this is it. If you reboot with the ethernet cable removed, can you see it in Network Manager? Can you connect?

---

### Post by wbreslin951 on 2009-11-28
> **chili555 said:**
> I believe this is it. If you reboot with the ethernet cable removed, can you see it in Network Manager? Can you connect?

its working? wow, wierd. now, here's the question of the day, good GUI internet connection sharing program? i need it so that i can hook my xbox up thru ethernet to my comp then my comp to the net thru wireless

---

### Post by chili555 on 2009-11-28
> internet connection sharing I suggest a new thread, referencing this subject. Glad your wireless is working as expected.

---

