---
title: "Wireless Nightmare...."
date: 2009-11-30
forum: Networking &amp; Wireless
---

### Post by a-web on 2009-11-30
The longer I use Ubuntu (9.10 now) the more issues I seem to have with wireless. First it was just with WPA2 ([http://ubuntuforums.org/showthread.php?t=1303516](http://ubuntuforums.org/showthread.php?t=1303516))...  but now I am unable to connect to any wireless network, even unencrypted.

I started with network-manager, switched to wicd to try to help with WPA2...  but recently I was having problems ("Unable to Obtain IP Address") with all networks, so tried to switch back to network-manager.  I un-installed wicd and did the following at a coffee shop:
```
sudo ifconfig <interface> down
sudo dhclient -r <interface>
sudo ifconfig <interface> up
sudo iwconfig <interface> essid "ESSID_IN_QUOTES"
sudo iwconfig <interface> mode Managed
sudo dhclient <interface>
```(from [http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188))
And I got connected to the coffee shop's unsecured wireless.  Then I tried to install network-manager, went fine but after a reboot I am unable to see network-manager and unable to get back online at all.   When I enter the above code, I get this after "sudo dhclient <interface>:
```
...
Listening on LPF/wlan2/00:16:b6:f2:77:ca
Sending on LPF/wlan2/00:16:b6:f2:77:ca
Sending on Socket/fallback
DHCPDISCOVER on wlan2 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on wlan2 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on wlan2 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on wlan2 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on wlan2 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wlan2 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wlan2 to 255.255.255.255 port 67 interval 21
DHCPDISCOVER on wlan2 to 255.255.255.255 port 67 interval 8
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```I would love to be able to get connected again.  Any help out there?

---

### Post by a-web on 2009-12-01
The quagmire gets deeper and more confusing (at least for me)...

After uninstalling network manager I was able to get online to another unsecured network.  Then I reinstalled network manager, rebooted and... I am online!

But...  the icon for network manager says that I am not connected.  When I click on it, it says "Wireless Networks:  device not managed"  (By posting this I am proving to myself that I truly am connected.)

I don't think this can bode well for future connectivity and reliability of said connectivity.  Thoughts?

---

### Post by pdc124 on 2009-12-01
do it one step at a time 
with no encryption 

sudo iwconfig wlan0 ESSID="xxxx" mod managed blah blah  etc etc
and then sudo iwconfig wlan0  and see if its associated 

then get an IP address 

dhclient -d wlan0 

WPA is a bit more complex and yo get into this sort of stuff ( once youve had a long lie down) - try google 

wpa_supplicant -iwlan0  -c/etc/wpa_supplicant/wpa_supplicant.conf -dd -Dwext

---

### Post by a-web on 2009-12-01
I followed what I understood to be your instructions, pdc124, and now I am back offline....  here is my code:```
:~$ sudo ifconfig wlan2 down
:~$ sudo dhclient -r wlan2
Internet Systems Consortium DHCP Client V3.1.2
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan2/00:16:b6:f2:77:ca
Sending on   LPF/wlan2/00:16:b6:f2:77:ca
Sending on   Socket/fallback
DHCPRELEASE on wlan2 to 192.168.1.1 port 67
send_packet: Network is unreachable
send_packet: please consult README file regarding broadcast address.
:~$ sudo ifconfig wlan2 up
:~$ sudo iwconfig wlan2 essid "uuaa"
:~$ sudo iwconfig wlan2 mode Managed
:~$ sudo iwconfig wlan2
wlan2     IEEE 802.11g  ESSID:"uuaa"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:16:B6:9E:24:DF   
          Bit Rate=54 Mb/s   
          Encryption key:off
          Power Management:off
          Link Quality:59/100  Signal level:-58 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

:~$ dhclient -d wlan2
Internet Systems Consortium DHCP Client V3.1.2
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

can't create /var/lib/dhcp3/dhclient.leases: Permission denied
SIOCSIFADDR: Permission denied
SIOCSIFFLAGS: Permission denied
SIOCSIFFLAGS: Permission denied
Open a socket for LPF: Operation not permitted
:~$
```And that computer can no longer access the internet.

And I was happily connected for months, and when I "tried google" for WPA I began getting into all this mess...  oh well,  If at first you don't succeed...

---

### Post by pdc124 on 2009-12-01
SIOCSIFFLAGS: Permission denied

you need sudo .......
( or sudo bash  and then just get on with it)

---

### Post by a-web on 2009-12-01
After a reboot I am back online, network manager still insisting that I am not online...  confusion ensues.

---

### Post by pdc124 on 2009-12-01
so what is the output of sudo iwconfig wlan2

and sudo ifconfig wlan2

and sudo route -n

---

### Post by a-web on 2009-12-01
Ah-ha!  Okay...  did the steps over with an extra "sudo" in there.  I am still online, network manager still says otherwise, here is the output of "sudo dhclient -d wlan2"
```
Internet Systems Consortium DHCP Client V3.1.2
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan2/00:16:b6:f2:77:ca
Sending on   LPF/wlan2/00:16:b6:f2:77:ca
Sending on   Socket/fallback
DHCPDISCOVER on wlan2 to 255.255.255.255 port 67 interval 6
DHCPOFFER of 192.168.0.134 from 192.168.0.1
DHCPREQUEST of 192.168.0.134 on wlan2 to 255.255.255.255 port 67
DHCPACK of 192.168.0.134 from 192.168.0.1
bound to 192.168.0.134 -- renewal in 110034 seconds.


```
With a blinking cursor at the end...

---

### Post by a-web on 2009-12-01
> **pdc124 said:**
> so what is the output of sudo iwconfig wlan2

and sudo ifconfig wlan2

and sudo route -n
```
:~$ sudo iwconfig wlan2
wlan2     IEEE 802.11g  ESSID:"uuaa"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:16:B6:9E:24:DF   
          Bit Rate=54 Mb/s   
          Encryption key:off
          Power Management:off
          Link Quality:59/100  Signal level:-58 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

:~$ sudo ifconfig wlan2
wlan2     Link encap:Ethernet  HWaddr 00:16:b6:f2:77:ca  
          inet addr:192.168.0.134  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::216:b6ff:fef2:77ca/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1211 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1132 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1096063 (1.0 MB)  TX bytes:158035 (158.0 KB)
          Interrupt:11 Memory:30000000-30080000 

:~$ sudo route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 wlan2
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 wlan2
:~$ 

```

---

### Post by a-web on 2009-12-01
I was able to get Network Manager up and running properly with this link:
[https://answers.launchpad.net/ubuntu/+question/85433](https://answers.launchpad.net/ubuntu/+question/85433)

---

