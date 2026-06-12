---
title: "VPNC and setting Hardware/MAC address"
date: 2010-05-27
forum: Networking &amp; Wireless
---

### Post by Improvisor on 2010-05-27
Is it possible to set/spoof the hardware address of the tun0 interface when using vpnc?

I use vpnc with no issues to connect to my company's VPN, but we have recently installed a Cisco NAC server to control access to the servers in the CoLo.  Since I am running Ubuntu, the only way I am able to get access through the Cisco NAC is to have my MAC address whitelisted.  This works fine if I use the real Cisco VPN client.  I can connect and that connection creates a HWaddr.  For example, output from ifconfig -a:
```

cipsec0   Link encap:Ethernet  HWaddr 00:0b:fc:d8:bb:8f  
          inet addr:192.168.1.88  Mask:255.255.255.0
          NOARP  MTU:1500  Metric:1
          RX packets:231 errors:0 dropped:0 overruns:0 frame:0
          TX packets:311 errors:0 dropped:4 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:54680 (54.6 KB)  TX bytes:35987 (35.9 KB)

```I have that HWaddr whitelisted and I am golden.  However, the Cicsco VPN client on 10.04 is behaving a bit wonky, so lately I've been using VPNC.  But when I connect to my company's VPN using VPNC the tunnel connection looks like this:
```

tun0      Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00  
          inet addr:192.168.1.84  P-t-P:192.168.1.84  Mask:255.255.255.0
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```The HWaddr is all zeros, which the Cisco NAC server doesn't like, so I can't get access.  

So, any way to spoof that HWaddr using VPNC configurations?

Thanks.

---

