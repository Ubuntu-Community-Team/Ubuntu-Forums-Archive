---
title: "USB Adapter 54 and Ubuntu - How to connect to internet?!"
date: 2006-07-02
forum: Networking &amp; Wireless
---

### Post by ZUHRA on 2006-07-02
...I have a problem connecting Siemens Gigaset USB Adapter 54 on Ubuntu Dapper...My AP is Siemens Gigaset SE515dsl which is connected to PC using Windows XP and I am trying to connect to it from PC using Ubuntu wireless...I am new in Ubuntu and my priority is to enable internet connection (I am from Croatia and I am using MAXadsl internet connection)  I installed USB Adapter 54 driver with ndiswrapper (after I also tried with ndisgtk)...when I type *ndiswrapper -l* it prints *hardware present*...then i tried with *modprobe ndiswrapper* (as root)...but the problem is that this usb adapter is not recognized as wlan0 interface.. it isrecognized as eth1 interface...i have found on some other forums that it's recomended to edit /etc/modprobe.d/ndiswrapper and change  alias wlan0 with alias eth1 but it does nothing...when I type** iwconfig **this is displayed: 

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b  ESSID:"zuhranet"
          Mode:Managed  Channel=14  Access Point: Invalid
          Sensitivity=0/200
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.


When I type **ifconfig** this is displayed: 

eth1      Link encap:Ethernet  HWaddr 00:30:F1:EE:67:56
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:31 errors:0 dropped:0 overruns:0 frame:0
          TX packets:31 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1956 (1.9 KiB)  TX bytes:1956 (1.9 KiB)

In configure network I typed ESSID and I am using WEP 64 bit ASCII key...Control light on usb adapter is always turned off...Thanks for your help in advance!!!

---

### Post by Stewori on 2006-08-18
Had the same problem. For me ndiswrapper worked after removing module islsm_usb from the kernel (and re-inserting ndiswrapper). For that I used modconf, but modprobe should do the job as well. For permanent remove I put the module on the blacklist.
Now I can access Siemens USB Gigaset 54. Configuring worked only by editing etc/network/interfaces, not by using wireless tools.
Unfortunately I still cant access Internet, because dhclient gets no dhcp-offers for wlan0 although everything is configured and signal-strength is at maximum.
Internet acces by static ip works, but I want to use dhcp.

Any ideas?

---

