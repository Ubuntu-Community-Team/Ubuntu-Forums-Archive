---
title: "How to enable wireless in ubuntu 9.10"
date: 2010-03-08
forum: Networking &amp; Wireless
---

### Post by emab on 2010-03-08
Hi,
recently i have installed ubuntu 9.10 on my system, it is functioning well on my system.
But there is a problem with my wireless i think. In windows i simply search for connections, choose an available connection and directly connect to network via wireless.
In ubuntu I can't see any wireless network available, when I click on network icon in top-right of screen (there is a connection, but ubuntu doesn't find it).

I think the problem is here (a partial output of lshw command):

```

...

*-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0

...

```and the output of iwconfig is:
```

root@omid-laptop:/home/omid# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

Could you please kindly help me?
I will be really pleasant
Thanks

---

