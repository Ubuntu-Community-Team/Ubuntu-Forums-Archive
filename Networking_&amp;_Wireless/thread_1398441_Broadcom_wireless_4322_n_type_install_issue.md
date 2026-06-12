---
title: "Broadcom wireless 4322 n type install issue"
date: 2010-02-04
forum: Networking &amp; Wireless
---

### Post by jdquark on 2010-02-04
Hi,

I have a 
0e:00.0 Network controller: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller (rev 01)
and have installed the driver
Broadcom 802.11 Linux STA wireless driverfor use with Broadcom's BCM4311-, BCM4312-, BCM4321-, andBCM4322-based hardware.

My ifconfig and iwconfig are posted below.  

It seems the wireless card is seen, the driver knows about it but the network does not let it operate properly.  

I saw that someone else was able to get this card working in the posts, however, I followed all the steps and had no success.  

I do have b43 in the blacklist.  

Thanks for the help ahead of time.

Are there any suggestions from the experts?  Oh, I am working on OS Ubuntu 9.10 on a dell vostro 1520, if that matters.

Cheers,
Jeff

root@jeff-laptop:~# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:24:e8:c7:50:2e  
          inet addr:192.168.1.66  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::224:e8ff:fec7:502e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:27863 errors:0 dropped:0 overruns:0 frame:0
          TX packets:26160 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:26319625 (26.3 MB)  TX bytes:4671214 (4.6 MB)
          Interrupt:32 

eth2      Link encap:Ethernet  HWaddr 00:24:2c:88:a5:54  
          inet6 addr: fe80::224:2cff:fe88:a554/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 

eth2:avahi Link encap:Ethernet  HWaddr 00:24:2c:88:a5:54  
          inet addr:169.254.7.77  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)



root@jeff-laptop:~# iwconfig 
lo        no wireless extensions.

eth0      no wireless extensions.

eth2      IEEE 802.11abgn  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:44 Mb/s   Tx-Power:off   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Power Managementmode:All packets received
          
vboxnet0  no wireless extensions.

root@jeff-laptop:~# ifconfig eth2 up
root@jeff-laptop:~# iwconfig 
lo        no wireless extensions.

eth0      no wireless extensions.

eth2      IEEE 802.11abgn  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:44 Mb/s   Tx-Power:off   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Power Managementmode:All packets received
          
vboxnet0  no wireless extensions.

root@jeff-laptop:~#

---

