---
title: "eth0 doesn't work? wlan0 only connects when...?"
date: 2011-02-18
forum: Networking &amp; Wireless
---

### Post by adduds on 2011-02-18
K so weird problem...

My LAN was a bit sluggy today other users noticed too...so simple fix reboot hardware, unplugged router, and dsl modem....

when all the lights came back on I connect to eth0 (which connects fine)....But have no internet connect through firefox also pings don't work

so i connected to my wireless network through my wireless pci card.....still nothing....but i remembered i'm still connected to eth0 so i disconnected from that and my net works again? 

It's the only way i can get my internet to work? Is by using my wireless why won't my eth0 work?

ifconfig:
```
adam@desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:14:2a:e9:15:0b  
          inet6 addr: fe80::214:2aff:fee9:150b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9195 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6623 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7741960 (7.7 MB)  TX bytes:599588 (599.5 KB)
          Interrupt:23 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:82 errors:0 dropped:0 overruns:0 frame:0
          TX packets:82 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:6132 (6.1 KB)  TX bytes:6132 (6.1 KB)

wlan0     Link encap:Ethernet  HWaddr 00:15:e9:84:e5:92  
          inet addr:192.168.0.103  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::215:e9ff:fe84:e592/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4880 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4487 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4720837 (4.7 MB)  TX bytes:721209 (721.2 KB)

```

iwconfig:
```

adam@desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"lifeportal"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 1C:AF:F7:DF:AF:6B   
          Bit Rate=1 Mb/s   Tx-Power=27 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-36 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

edit: note i have tried re-booting my computer with all hardware powered down

---

### Post by grahammechanical on 2011-02-18
Compare the listing from ifconfig. Do you see anything that will give you a clue. Both eth0 and wlan0 have UP BROADCAST RUNNING MULTICAST. If eth0 was not working you would not see RUNNING.

wlan0 has a inet addr and a inet6 addr but eth0 only has inet6 addr. The inet addr is the IP address of your modem/router. You are not connected to the modem/router by ethernet cable. You are connected by wireless. 

Plug the ethernet cable back in and switch off the modem, wait a few seconds and switch it back on. What happens? Check to see if you have both Enable Networking and Enable Wireless ticked. Right click the icon.

Regards.

---

### Post by adduds on 2011-02-19
> **grahammechanical said:**
>  BROADCAST RUNNING MULTICAST. If eth0 was not working you would not see RUNNING.

You are not connected to the modem/router by ethernet cable. You are connected by wireless. 

Plug the ethernet cable back in and switch off the modem, wait a few seconds and switch it back on. What happens? Check to see if you have both Enable Networking and Enable Wireless ticked. Right click the icon.
Regards.

neat info about broadcast running didn't know that

I am connected through a hardware ethernet cable....

both enable networking and wireless are ticked

so basically my box isn't getting an ip address from my router??

this is with my eth0 connection active

> adam@desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:14:2a:e9:15:0b  
          inet addr:192.168.0.100  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::214:2aff:fee9:150b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:147 errors:0 dropped:0 overruns:0 frame:0
          TX packets:158 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:15111 (15.1 KB)  TX bytes:21296 (21.2 KB)
          Interrupt:23 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:52 errors:0 dropped:0 overruns:0 frame:0
          TX packets:52 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:12244 (12.2 KB)  TX bytes:12244 (12.2 KB)

wlan0     Link encap:Ethernet  HWaddr 00:15:e9:84:e5:92  
          inet addr:192.168.0.103  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::215:e9ff:fe84:e592/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:526 errors:0 dropped:0 overruns:0 frame:0
          TX packets:531 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:496879 (496.8 KB)  TX bytes:82665 (82.6 KB)


---

