---
title: "Wireless broken since upgrade from Gutsy to Hardy."
date: 2009-01-15
forum: Networking &amp; Wireless
---

### Post by yknivag on 2009-01-15
I thought I was beginning to get the hang of this, but obviously not :(

What seems like several lifetimes ago I installed Gutsy Gibbon on an HP Compaq nc6000 laptop.  After a lot of fiddling and the very kind help from a number of people on this forum, and installing WICD, I got my wireless internet working.  It was working perfectly, much more stably than on my Windoze box.

However, I broke it (somehow) when I upgraded from Gutsy to Hardy using the upgrade function in the updates wizard thing.  No problem, I thought a clean install should soon rectify that. But no, it still won't connect.

Below are all the usual bits people ask for in these kind of situations.  I tried using the GUI, gave up and went to CLI but still bo luck.

Here's what I did...

...first check what's there (with ifconfig, iwconfig, iwlist scan)...
```

gavin@wrist:~$ sudo ifconfig
[sudo] password for gavin: 
ath0      Link encap:Ethernet  HWaddr 00:11:0a:81:19:46  
          inet6 addr: fe80::211:aff:fe81:1946/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

eth0      Link encap:Ethernet  HWaddr 00:08:02:e6:9d:02  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:11 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2172 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2172 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:108600 (106.0 KB)  TX bytes:108600 (106.0 KB)

wifi0     Link encap:UNSPEC  HWaddr 00-11-0A-81-19-46-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:506 errors:0 dropped:0 overruns:0 frame:17
          TX packets:155 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:60087 (58.6 KB)  TX bytes:7130 (6.9 KB)
          Interrupt:11 

gavin@wrist:~$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

irda0     no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11a  ESSID:""  Nickname:""
          Mode:Managed  Frequency:5.66 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:14 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=0/70  Signal level=-98 dBm  Noise level=-98 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

gavin@wrist:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

irda0     Interface doesn't support scanning.

wifi0     Interface doesn't support scanning.

ath0      Scan completed :
          Cell 01 - Address: 00:18:F6:AD:78:45
                    ESSID:"BTHomeHub-DC9E"
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Quality=14/70  Signal level=-81 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:wme_ie=dd180050f2020101880003a4000027a4000042435e0062322f00
          Cell 02 - Address: 00:0F:66:EC:45:88
                    ESSID:"pelvis"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=51/70  Signal level=-44 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: 00:1F:33:75:BD:1A
                    ESSID:"SKY54505"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=39/70  Signal level=-56 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Extra:wme_ie=dd070050f202000100
          Cell 04 - Address: 00:18:4D:F4:20:F8
                    ESSID:"SKY91585"
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Quality=32/70  Signal level=-63 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Extra:wme_ie=dd180050f2020101050003a4000027a4000042435e0062322f00
                    Extra:ath_ie=dd0900037f01010024ff7f
          Cell 05 - Address: 00:1B:2F:3A:C0:9C
                    ESSID:"SKY01008"
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Quality=26/70  Signal level=-69 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Extra:wme_ie=dd180050f2020101050003a4000027a4000042435e0062322f00
                    Extra:ath_ie=dd0900037f01010024ff7f

```
Take everything down for a fresh start (and to make sure that eth0 and ath0 aren't both competing for the network - though the cable isn't plugged in)...
```

gavin@wrist:~$ sudo ifdown eth0
ifdown: interface eth0 not configured
gavin@wrist:~$ sudo ifdown ath0
ifdown: interface ath0 not configured

```
Then try and bring the wireless up...
```

gavin@wrist:~$ sudo ifup ath0

```
Check it's got the right ESSID
```

gavin@wrist:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

irda0     no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11a  ESSID:"pelvis"  Nickname:""
          Mode:Managed  Frequency:5.825 GHz  Access Point: 00:0F:66:EC:45:88   
          Bit Rate:0 kb/s   Tx-Power:14 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=-98 dBm  Noise level=-98 dBm
          Rx invalid nwid:681  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```
Try and connect
```

gavin@wrist:~$ sudo dhclient ath0
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/ath0/00:11:0a:81:19:46
Sending on   LPF/ath0/00:11:0a:81:19:46
Sending on   Socket/fallback
DHCPREQUEST of 10.0.0.100 on ath0 to 255.255.255.255 port 67
DHCPREQUEST of 10.0.0.100 on ath0 to 255.255.255.255 port 67
DHCPREQUEST of 10.0.0.100 on ath0 to 255.255.255.255 port 67
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 5
No DHCPOFFERS received.
Trying recorded lease 10.0.0.100
PING 10.0.0.2 (10.0.0.2) 56(84) bytes of data.

--- 10.0.0.2 ping statistics ---
1 packets transmitted, 0 received, +1 errors, 100% packet loss, time 0ms

No working leases in persistent database - sleeping.

```

And no luck.  It did once get a DHCP response (hence it knowing that 10.0.0.100 was it's previous address, but even then a ping of the default gateway (10.0.0.2) returned (Destination Unreachable) even though it had just got a DHCP lease from there!

lshw -C Network shows that the card is correctly claimed by the madwifi ath_pci driver (which worked perfectly in Gutsy).

```

gavin@wrist:~$ sudo lshw -C Network
  *-network:0             
       description: Wireless interface
       product: AR5212/AR5213 Multiprotocol MAC/baseband processor
       vendor: Atheros Communications Inc.
       physical id: 4
       bus info: pci@0000:02:04.0
       logical name: wifi0
       version: 01
       serial: 00:11:0a:81:19:46
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci latency=168 maxlatency=28 mingnt=10 module=ath_pci multicast=yes wireless=IEEE 802.11a
  *-network:1
       description: Ethernet interface
       product: NetXtreme BCM5705M_2 Gigabit Ethernet
       vendor: Broadcom Corporation
       physical id: e
       bus info: pci@0000:02:0e.0
       logical name: eth0
       version: 03
       serial: 00:08:02:e6:9d:02
       capacity: 1GB/s
       width: 64 bits
       clock: 66MHz
       capabilities: pm vpd msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.86 firmware=5705-v3.14 latency=64 link=no mingnt=64 module=tg3 multicast=yes port=twisted pair

```
and here's my /etc/network/interfaces file...
```

gavin@wrist:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback


iface eth0 inet dhcp



iface ath0 inet static
address 10.0.0.20
netmask 255.255.255.0
gateway 10.0.0.2
wpa-driver wext
wpa-key-mgmt WPA-PSK
wpa-proto WPA
wpa-ssid pelvis



#auto eth0

#auto ath0

```
and the card is...
```

gavin@wrist:~$ lspci | grep "Atheros"
02:04.0 Ethernet controller: Atheros Communications Inc. AR5212/AR5213 Multiprotocol MAC/baseband processor (rev 01)

```

Any thoughts on what I might change to get this working would be very much appreciated! I'm at my wits end here, and need to do this again (with another Atheros chipset) for my father at the end of the month as he's decided he wants to try Ubuntu (he borrowed my laptop and was rather impressed with easy Gnome is to navigate!)

---

### Post by yknivag on 2009-01-15
Just out of interest I disabled the WPA security on the router, removed the WPA key details from the network manager GUI (which produced this /etc/network/interfaces file)
```

gavin@wrist:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback


iface eth0 inet dhcp


iface ath0 inet dhcp
wireless-essid pelvis

auto ath0

```
and then tried to reconnect
```

gavin@wrist:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          There is already a pid file /var/run/dhclient.ath0.pid with pid 11171
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/ath0/00:11:0a:81:19:46
Sending on   LPF/ath0/00:11:0a:81:19:46
Sending on   Socket/fallback
DHCPRELEASE on ath0 to 10.0.0.2 port 67
There is already a pid file /var/run/dhclient.ath0.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/ath0/00:11:0a:81:19:46
Sending on   LPF/ath0/00:11:0a:81:19:46
Sending on   Socket/fallback
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 6
DHCPOFFER of 10.0.0.100 from 10.0.0.2
DHCPREQUEST of 10.0.0.100 on ath0 to 255.255.255.255 port 67
DHCPACK of 10.0.0.100 from 10.0.0.2
bound to 10.0.0.100 -- renewal in 35120 seconds.
                                                                         [ OK ]

```
I got a DHCP lease from my router (10.0.0.2)! :)

However a ping of the router fails :(
```

gavin@wrist:~$ ping -c5 10.0.0.2
PING 10.0.0.2 (10.0.0.2) 56(84) bytes of data.

--- 10.0.0.2 ping statistics ---
5 packets transmitted, 0 received, 100% packet loss, time 4022ms

```

---

### Post by yknivag on 2009-01-15
...and now it appears to be working and I am most confused!

I installed wicd, which didn't work either. Then uninstalled that and re-installed network-manager and now I'm connected!

Although the connection only stays up very briefly and I have to keep running:
```

sudo ifdown ath0
sudo ifup ath0

```
to get it to come back

---

### Post by yknivag on 2009-01-15
everytime it goes off I see this appear in kern.log
```

Jan 15 23:15:34 wrist kernel: [  873.883937] ADDRCONF(NETDEV_UP): ath0: link is not ready

```
it seems to be occuring quite regularly...
```

Jan 15 23:13:05 wrist kernel: [  799.167798] ADDRCONF(NETDEV_CHANGE): ath0: link becomes ready
Jan 15 23:13:15 wrist kernel: [  807.984508] ath0: no IPv6 routers present
Jan 15 23:15:13 wrist kernel: [  865.829263] ADDRCONF(NETDEV_UP): ath0: link is not ready
Jan 15 23:15:22 wrist kernel: [  869.857384] ADDRCONF(NETDEV_UP): ath0: link is not ready
Jan 15 23:15:34 wrist kernel: [  873.883937] ADDRCONF(NETDEV_UP): ath0: link is not ready

```

Is this a driver issue still? Or maybe a hardware failure?

---

### Post by yknivag on 2009-01-16
well having got thoroughly fed up of having to manually reconnect running:
```

sudo ifdown eth0
sudo ifdown ath0
sudo ifup ath0
sudo ifdown ath0
sudo ifup ath0

```
(yes the repeat really was necessary every time!)

I thought I'd try Intrepid, because I'd heard that the NM in there was better than the Hardy one.

Unfortunately I then fell victim to [this bug]("http://ubuntuforums.org/showthread.php?t=1010650") and, having not discovered that thread at the time, decided to do a clean install of Hardy again.

Hardy re-installed and now my wireless works seemlessly using the "Roaming Mode" in Network Manager!

I have absolutely no idea what changed, only that it now works!  I guess this isn't much help to anyone with the same problem, only to confirm it does work in the end!

:confused:

---

