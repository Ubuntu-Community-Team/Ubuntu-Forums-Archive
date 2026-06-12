---
title: "Help with WUSB100 usb wireless adapter."
date: 2010-03-17
forum: Networking &amp; Wireless
---

### Post by lpstevens on 2010-03-17
Ok i have been reading several threads trying to get this WUSB100 wireless adapter to work.  I tried downloading and installing the Ralink drivers (RT2870_LinuxSTA_V2.3.0.0) and still can't get that to work.


pomai@pomai-laptop:~$ lsusb
Bus 001 Device 003: ID 0c45:62c0 Microdia Sonix USB 2.0 Camera
Bus 001 Device 002: ID 1737:0078 Linksys 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 002: ID 046d:c01e Logitech, Inc. MX518 Optical Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

pomai@pomai-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1b:00:59:00:ea  
          inet addr:0  Bcast:00.95.171.000  Mask:255.255.255.0
          inet6 addr: 0000::21b:00ff:fe00:79ea/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8152 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1169 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1929294 (1.9 MB)  TX bytes:192302 (192.3 KB)
          Interrupt:20 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

pomai@pomai-laptop:~$  iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

I'm not sure what else to do.

---

### Post by chili555 on 2010-03-17
Please let us see:```
dmesg | grep -e rt2 -e rt3
```You have a wireless interface, wlan0. Can you detach the ethernet cable, click the Network Manager icon, see your network and connect?

---

### Post by bkratz on 2010-03-17
> **chili555 said:**
> Please let us see:```
dmesg | grep -e rt2 -e rt3
```You have a wireless interface, wlan0. Can you detach the ethernet cable, click the Network Manager icon, see your network and connect?

@Chili555-- I notice that

Tx-Power=0 dBm

in the above, could that be the reason?

---

### Post by chili555 on 2010-03-17
It sure could be. Good catch!

@lpstevens

Please try:```
sudo iwconfig wlan0 txpower 15
```If this command returns an error, try again at 5 and keep increasing until you get the error. If it errors out at 5, please post the error.

---

### Post by lpstevens on 2010-03-17
Ok so I typed in :

> sudo iwconfig wlan0 txpower 15pomai@pomai-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

I checked Network Manager and i still can't see my network.

I typed in :
> dmesg | grep -e rt2 -e rt3and nothing returned.

---

### Post by lpstevens on 2010-03-17
[SOLVED]
I reinstalled Ubuntu 9.10 and followed [http://ubuntuforums.org/showthread.php?p=8591348#post8591348](http://ubuntuforums.org/showthread.php?p=8591348#post8591348).
Thanks for the help.

---

