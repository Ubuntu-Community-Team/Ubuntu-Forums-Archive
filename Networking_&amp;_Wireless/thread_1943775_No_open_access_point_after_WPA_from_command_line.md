---
title: "No open access point after WPA from command line"
date: 2012-03-20
forum: Networking &amp; Wireless
---

### Post by pimpimpim on 2012-03-20
Hi All,
 
I am using Ubuntu 10.04 and I want to use the command line to configure the wireless.
This is as a test so I can use the same commands later on a similar system without possibility to access the Network Manager.
It seems to be going OK and I am possible of connecting to wpa, wpa2, open and WEP protected access points.
 
However, after using wpa supplicant to connect to wifi, when I want to connect to open wifi, with the same commands that worked before, I don't receive an access point.
As I have an electronics background, I tried hitting the machine, but it didn't seem to help.
 
I know that it is possible to do this because with the Network Manager it also works.
I am relatively new to Linux so maybe I made some mistake(s).
 
The commands I am using are these:
 
```

 
root@gr-phu-0516:/home/gr-phu# ifconfig wlan0 down
root@gr-phu-0516:/home/gr-phu# killall wpa_supplicant
root@gr-phu-0516:/home/gr-phu# killall dhclient
root@gr-phu-0516:/home/gr-phu# wpa_passphrase "aaaaaaaa" aaaaaaaa > /etc/wpa_supplicant.conf
root@gr-phu-0516:/home/gr-phu# wpa_supplicant -B -Dwext -i wlan0 -c/etc/wpa_supplicant.conf -qq
root@gr-phu-0516:/home/gr-phu# iwconfig  wlan0 ap auto mode managed essid "aaaaaaaa" channel 6 key off
root@gr-phu-0516:/home/gr-phu# ifconfig  wlan0 up
root@gr-phu-0516:/home/gr-phu# dhclient  wlan0
 

```This seems all successful as I can access this forum and get the message:
 
```

There is already a pid file /var/run/dhclient.pid with pid 3651
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/
 
Listening on LPF/wlan0/00:24:b2:dc:fb:77
Sending on   LPF/wlan0/00:24:b2:dc:fb:77
Sending on   Socket/fallback
DHCPREQUEST of 192.168.43.81 on wlan0 to 255.255.255.255 port 67
DHCPACK of 192.168.43.81 from 192.168.43.1
bound to 192.168.43.81 -- renewal in 1535 seconds.

```Then I try to connect to another connection with open wifi (in this case it is physically the same Access Point, but that doesn't seem to make a difference):
 
```

 
root@gr-phu-0516:/home/gr-phu# ifconfig wlan0 down
root@gr-phu-0516:/home/gr-phu# killall wpa_supplicant
root@gr-phu-0516:/home/gr-phu# killall dhclient
root@gr-phu-0516:/home/gr-phu# iwconfig  wlan0 ap auto mode managed essid "aaaaaaa" channel 6 key open
root@gr-phu-0516:/home/gr-phu# ifconfig  wlan0 up
root@gr-phu-0516:/home/gr-phu# dhclient wlan0
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/
 
Listening on LPF/wlan0/00:24:b2:dc:fb:77
Sending on   LPF/wlan0/00:24:b2:dc:fb:77
Sending on   Socket/fallback
DHCPREQUEST of 192.168.1.75 on wlan0 to 255.255.255.255 port 67
DHCPREQUEST of 192.168.1.75 on wlan0 to 255.255.255.255 port 67
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 16
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
No DHCPOFFERS received.
Trying recorded lease 192.168.43.81
PING 192.168.43.1 (192.168.43.1) 56(84) bytes of data.
 
--- 192.168.43.1 ping statistics ---
1 packets transmitted, 0 received, 100% packet loss, time 0ms
 

```I am using an Atheros USB stick as hardware.
 
Maybe some other useful information:
 
```

 
root@gr-phu-0516:/home/gr-phu# iwconfig 
lo        no wireless extensions.
 
eth0      no wireless extensions.
 
wlan0     IEEE 802.11bg  ESSID:"aaaaaaa"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
 
root@gr-phu-0516:/home/gr-phu# ifconfig 
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:28 errors:0 dropped:0 overruns:0 frame:0
          TX packets:28 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2512 (2.5 KB)  TX bytes:2512 (2.5 KB)
 
wlan0     Link encap:Ethernet  HWaddr 00:24:b2:dc:fb:77  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:2961 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2482 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2365908 (2.3 MB)  TX bytes:516367 (516.3 KB)
 
root@gr-phu-0516:/home/gr-phu# iwlist wlan0 scan
wlan0     Scan completed :
 (...)
          Cell 04 - Address: 98:0C:82:92:F5:48
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=-16 dBm  
                    Encryption key:off
                    ESSID:"aaaaaaa"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000000200991ac
                    Extra: Last beacon: 608ms ago
                    IE: Unknown: 000761616161616161
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A0C1019FF00000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606080000000000000000000000000000000000000000
                    IE: Unknown: DD09001018020000000000
 (...)

```When I remove the USB stick between the operations, I do get an Access Point and ip-address, so I suspect that some process is still running somewhere (?). However, to eject and insert the stick is not really an option.
 
Connecting to WEP and WPA protected Access Points is not a problem, only open has this issue.
 
Thanks in advance,
 
pim

---

### Post by chili555 on 2012-03-20
I don't know the exact answer, but I love a mystery and I have a few suggestions:> # wlan0 downThis means nothing. I think you want:```
[COLOR="Red"]ifconfig[/COLOR] wlan0 down
```> iwconfig  wlan0 ap auto mode managed essid "aaaaaaa" channel 6 key openThis is a bit busy. I suggest:```
iwconfig wlan0 essid aaaaaaa key [COLOR="Red"]off[/COLOR]
```I will be interested in your results.

---

### Post by pimpimpim on 2012-03-21
Thank you for your response. 
 
I see I made a mistake copying the line "#ifconfig wlan down". I will edit the topic opening.
 
I now tried with "off" instead of "open".
I got the same result: no access point.
 
I also tried manually setting the Access Point, but even then it still says "Not-Associated".

---

### Post by chili555 on 2012-03-21
Do the system logs hold any clues?```
sudo cat /var/log/syslog | grep -e etwork -e wlan | tail -n20
```

---

### Post by pimpimpim on 2012-03-23
```

root@gr-phu-0516:/home/gr-phu/workspace/imwifi# sudo cat /var/log/syslog | grep -e etwork -e wlan | tail -20
Mar 23 14:31:54 gr-phu-0516 avahi-daemon[593]: Withdrawing address record for 192.168.1.75 on wlan0.
Mar 23 14:31:54 gr-phu-0516 avahi-daemon[593]: Joining mDNS multicast group on interface wlan0.IPv4 with address 192.168.1.75.
Mar 23 14:31:54 gr-phu-0516 avahi-daemon[593]: New relevant interface wlan0.IPv4 for mDNS.
Mar 23 14:31:54 gr-phu-0516 avahi-daemon[593]: Registering new address record for 192.168.1.75 on wlan0.IPv4.
Mar 23 14:31:54 gr-phu-0516 avahi-daemon[593]: Interface wlan0.IPv4 no longer relevant for mDNS.
Mar 23 14:31:54 gr-phu-0516 avahi-daemon[593]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 192.168.1.75.
Mar 23 14:31:54 gr-phu-0516 avahi-daemon[593]: Withdrawing address record for 192.168.1.75 on wlan0.
Mar 23 14:31:57 gr-phu-0516 avahi-daemon[593]: Joining mDNS multicast group on interface wlan0.IPv4 with address 192.168.1.75.
Mar 23 14:31:57 gr-phu-0516 kernel: [21638.859582] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Mar 23 14:31:57 gr-phu-0516 avahi-daemon[593]: New relevant interface wlan0.IPv4 for mDNS.
Mar 23 14:31:57 gr-phu-0516 avahi-daemon[593]: Registering new address record for 192.168.1.75 on wlan0.IPv4.
Mar 23 14:31:57 gr-phu-0516 avahi-daemon[593]: Withdrawing address record for 192.168.1.75 on wlan0.
Mar 23 14:31:57 gr-phu-0516 avahi-daemon[593]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 192.168.1.75.
Mar 23 14:31:57 gr-phu-0516 avahi-daemon[593]: Interface wlan0.IPv4 no longer relevant for mDNS.
Mar 23 14:31:57 gr-phu-0516 dhclient: Listening on LPF/wlan0/00:24:b2:dc:fb:77
Mar 23 14:31:57 gr-phu-0516 dhclient: Sending on   LPF/wlan0/00:24:b2:dc:fb:77
Mar 23 14:32:00 gr-phu-0516 dhclient: DHCPREQUEST of 192.168.1.75 on wlan0 to 255.255.255.255 port 67
Mar 23 14:32:05 gr-phu-0516 dhclient: DHCPREQUEST of 192.168.1.75 on wlan0 to 255.255.255.255 port 67
Mar 23 14:32:17 gr-phu-0516 dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
Mar 23 14:32:24 gr-phu-0516 dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10


```Nr 75 was the ip-addres for the WPA system in this case.

The active processes started after inserting the USB-stick:

```
 

root@gr-phu-0516:/home/gr-phu/workspace/imwifi# ps -aef | tail -n10
gr-phu   14387     1 19 14:35 ?        00:01:59 /usr/lib/firefox-10.0.2/firefox
root     14540   243  0 14:43 ?        00:00:00 udevd --daemon
root     14542   243  0 14:43 ?        00:00:00 udevd --daemon
root     14544     2  0 14:43 ?        00:00:00 [phy2]
root     14545  1104  0 14:43 ?        00:00:00 /usr/lib/hal/hald-addon-rfkill-killswitch
root     14548  1104  0 14:43 ?        00:00:00 /usr/lib/hal/hald-addon-leds
root     14634     1  0 14:43 ?        00:00:00 dhclient3 -e IF_METRIC=100 -pf /var/run/dhclient.wlan0.pid -lf /var/lib/dhcp3/dhclient.wlan0.leases wlan0
root     14672     1  0 14:43 ?        00:00:00 /usr/sbin/sshd -D
root     14853 14095  0 14:45 pts/0    00:00:00 ps -aef
root     14854 14095  0 14:45 pts/0    00:00:00 tail -n10


```

---

### Post by sparta351988 on 2012-03-23
Guys please guide me to use Tata Photon Plus Wireless Broadband  Connection on my Computer with UBUNTU 10.04 LTS.

I am trying to connect it but still its not getting connected to the Internet

---

### Post by chili555 on 2012-03-23
> **sparta351988 said:**
> Guys please guide me to use Tata Photon Plus Wireless Broadband  Connection on my Computer with UBUNTU 10.04 LTS.

I am trying to connect it but still its not getting connected to the InternetYour question is completely unrelated to the original post. I suggest you start your own new thread.

---

### Post by chili555 on 2012-03-23
> /var/lib/dhcp3/dhclient.wlan0.leasesI wonder if this is the key. Just to satisfy an old tinkerer, please try preceding your commands with this:```
echo "" > /var/lib/dhcp3/dhclient.wlan0.leases
```I think that will blank the file and not allow dhclient to look for old IP addresses, ESSIDs, etc. 

You could also try:```
rm /var/lib/dhcp3/dhclient.wlan0.leases
```

I suspect part of the difficulty is this:> Then I try to connect to another connection with open wifi (in this case **it is physically the same Access Point**,If it has the same ESSID and MAC address, maybe it's confusing the system. 

As I said, I don't know the exact answer, but I love a mystery.

---

