---
title: "Ralink 5370 connected but no internet..."
date: 2013-05-13
forum: Networking &amp; Wireless
---

### Post by jaceleon on 2013-05-13
Hi!

currently I have installed Lubuntu 13.04, WITH Linux 3.9 kernel on my laptop, and my wifi uses the "rt2870usb" driver (my wifi device is a Ralink 5370 USB). And I am getting slow connections. So I installed the driver from ralink, and after installing and blacklisting the generic driver, network manager is connected wirelessly, and uses the "usb" driver, also my interface changed from wlan0 to ra0. ping via terminal tells me I am connected with internet, but I can't browse, nor download packages in my sudo apt-get commands. kindly help me.

thank you!

---

### Post by praseodym on 2013-05-13
Please show:
```

lsusb
lsmod
iwconfig
ifconfig -a
cat /etc/resolv.conf
route -n
sudo iwlist scan
iwlist chan
dmesg | egrep 'rt2|rt5'
```

---

### Post by jaceleon on 2013-05-14
lsusb
lsmod
iwconfig
ifconfig -a
cat /etc/resolv.conf
route -n
sudo iwlist scan
iwlist chan
dmesg | egrep 'rt2|rt5'


Bus 003 Device 002: ID 148f:5370 Ralink Technology, Corp. RT5370 Wireless Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

on my blacklist:
blacklist rt2800usb
blacklist rt2870usb
blacklist rt2x00usb
blacklist rt2x00sta
blacklist rt3xxxsta



lsmod
Module                  Size  Used by
bnep                   17852  2 
rfcomm                 38399  0 
bluetooth             215725  10 bnep,rfcomm
binfmt_misc            17292  1 
snd_intel8x0           33458  3 
snd_ac97_codec        110254  1 snd_intel8x0
thinkpad_acpi          73962  0 
ac97_bus               12670  1 snd_ac97_codec
rt5370sta             730493  1 
snd_pcm                85934  3 snd_ac97_codec,snd_intel8x0
nvram                  14029  1 thinkpad_acpi
snd_page_alloc         18398  2 snd_intel8x0,snd_pcm
snd_seq_midi           13132  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_rawmidi            25157  1 snd_seq_midi
pcmcia                 39854  0 
snd_seq                51593  2 snd_seq_midi_event,snd_seq_midi
i915                  556860  2 
psmouse                82742  0 
ppdev                  12842  0 
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
microcode              18355  0 
snd_timer              28931  3 snd_pcm,snd_seq
yenta_socket           27427  0 
pcmcia_rsrc            18367  1 yenta_socket
serio_raw              13031  0 
snd                    57014  12 snd_ac97_codec,snd_intel8x0,snd_timer,snd_pcm,snd_seq,snd_rawmidi,thinkpad_acpi,snd_seq_device
pcmcia_core            21624  3 pcmcia,pcmcia_rsrc,yenta_socket
drm_kms_helper         47306  1 i915
soundcore              12600  1 snd
drm                   237607  3 i915,drm_kms_helper
lpc_ich                16980  0 
parport_pc             27612  1 
i2c_algo_bit           13316  1 i915
shpchp                 32265  0 
video                  18955  1 i915
mac_hid                13077  0 
lp                     17455  0 
parport                40930  3 lp,ppdev,parport_pc
tg3                   154839  0 
ptp                    18232  1 tg3
pps_core               13736  1 ptp


iwconfig
ra0       Ralink STA  ESSID:"cannot tell this one"  Nickname:"RT2870STA"
          Mode:Managed  Frequency=2.462 GHz  Access Point: not giving this mac address   
          Bit Rate=121.5 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=71/100  Signal level:-73 dBm  Noise level:-88 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

lo        no wireless extensions.

eth0      no wireless extensions.



ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:06:1b:c5:84:d1  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:9 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:576 errors:0 dropped:0 overruns:0 frame:0
          TX packets:576 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:51054 (51.0 KB)  TX bytes:51054 (51.0 KB)

ra0       Link encap:Ethernet  HWaddr 00:0f:54:09:36:9c  
          inet addr:192.168.1.114  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:54ff:fe09:369c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:599294 (599.2 KB)  TX bytes:45450 (45.4 KB)



cat /etc/resolv.conf
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.1.1
search domain.name



route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 ra0
192.168.1.0     0.0.0.0         255.255.255.0   U     9      0        0 ra0


sudo iwlist scan
[sudo] password for jaceleon: 
ra0       Scan completed :
          Cell 01 - Address: my own
                    Protocol:802.11b/g/n
                    ESSID:"not telling this one"
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality=52/100  Signal level=-69 dBm  Noise level=-92 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: B0:B2:DC:75:29:24
                    Protocol:802.11b/g/n
                    ESSID:"neighbors wifi"
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality=0/100  Signal level=-93 dBm  Noise level=-98 dBm
                    Encryption key:on
                    Bit Rates:150 Mb/s
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD270050F204104A000110104400010110470010BC329E001DD811B28601B0B2DC752924103C000100
          Cell 03 - Address: 50:67:F0:8F:B7:BE
                    Protocol:802.11b/g
                    ESSID:"another neighbors wifi"
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality=2/100  Signal level=-89 dBm  Noise level=-94 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.



iwlist chan
ra0       14 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Channel 14 : 2.484 GHz
          Current Frequency:2.462 GHz (Channel 11)

lo        no frequency information.

eth0      no frequency information.




dmesg | egrep 'rt2|rt5'
[   10.064746] rt5370sta: module verification failed: signature and/or required key missing - tainting kernel
[   10.068667] rtusb init rt2870 --->
[   10.075546] usbcore: registered new interface driver rt2870
[   20.163769] <==== rt28xx_init, Status=0
[   21.410755] <==== rt28xx_init, Status=0
[   22.705413] <==== rt28xx_init, Status=0
[   64.566810] <==== rt28xx_init, Status=0




active network connections
not telling my access point (default)

general
interface      802.11 WiFi (ra0)
Hardware Address  00:0F:54:09:36:9C
Drive      usb
Speed      81Mb/s
Security     WPA/WPA2

IPv4
IP Address     192.168.1.114
Broadcast Address  192.168.1.255
Subnet Mask    255.255.255.0
Default Route    192.168.1.1
Primary DNS    192.168.1.1

IPv6








ping [www.facebook.com](www.facebook.com)
PING star.c10r.facebook.com (31.13.77.55) 56(84) bytes of data.
64 bytes from star-01-04-sjc1.facebook.com (31.13.77.55): icmp_req=1 ttl=244 time=404 ms
64 bytes from star-01-04-sjc1.facebook.com (31.13.77.55): icmp_req=2 ttl=244 time=427 ms
64 bytes from star-01-04-sjc1.facebook.com (31.13.77.55): icmp_req=3 ttl=244 time=390 ms
64 bytes from star-01-04-sjc1.facebook.com (31.13.77.55): icmp_req=4 ttl=244 time=409 ms
64 bytes from star-01-04-sjc1.facebook.com (31.13.77.55): icmp_req=5 ttl=244 time=456 ms
64 bytes from star-01-04-sjc1.facebook.com (31.13.77.55): icmp_req=6 ttl=244 time=459 ms
64 bytes from star-01-04-sjc1.facebook.com (31.13.77.55): icmp_req=7 ttl=244 time=324 ms
64 bytes from star-01-04-sjc1.facebook.com (31.13.77.55): icmp_req=8 ttl=244 time=441 ms
64 bytes from star-01-04-sjc1.facebook.com (31.13.77.55): icmp_req=9 ttl=244 time=1369 ms
64 bytes from star-01-04-sjc1.facebook.com (31.13.77.55): icmp_req=10 ttl=244 time=375 ms
64 bytes from star-01-04-sjc1.facebook.com (31.13.77.55): icmp_req=11 ttl=244 time=361 ms
64 bytes from star-01-04-sjc1.facebook.com (31.13.77.55): icmp_req=12 ttl=244 time=298 ms
64 bytes from star-01-04-sjc1.facebook.com (31.13.77.55): icmp_req=13 ttl=244 time=361 ms
64 bytes from star-01-04-sjc1.facebook.com (31.13.77.55): icmp_req=14 ttl=244 time=404 ms
64 bytes from star-01-04-sjc1.facebook.com (31.13.77.55): icmp_req=15 ttl=244 time=485 ms
64 bytes from star-01-04-sjc1.facebook.com (31.13.77.55): icmp_req=16 ttl=244 time=402 ms
64 bytes from star-01-04-sjc1.facebook.com (31.13.77.55): icmp_req=17 ttl=244 time=489 ms
64 bytes from star-01-04-sjc1.facebook.com (31.13.77.55): icmp_req=18 ttl=244 time=394 ms
64 bytes from star-01-04-sjc1.facebook.com (31.13.77.55): icmp_req=20 ttl=244 time=396 ms
64 bytes from star-01-04-sjc1.facebook.com (31.13.77.55): icmp_req=21 ttl=244 time=409 ms
64 bytes from 31.13.77.55: icmp_req=22 ttl=244 time=413 ms
64 bytes from star-01-04-sjc1.facebook.com (31.13.77.55): icmp_req=23 ttl=244 time=440 ms
64 bytes from star-01-04-sjc1.facebook.com (31.13.77.55): icmp_req=24 ttl=244 time=465 ms
64 bytes from star-01-04-sjc1.facebook.com (31.13.77.55): icmp_req=25 ttl=244 time=417 ms
64 bytes from star-01-04-sjc1.facebook.com (31.13.77.55): icmp_req=26 ttl=244 time=513 ms
64 bytes from star-01-04-sjc1.facebook.com (31.13.77.55): icmp_req=27 ttl=244 time=376 ms
64 bytes from star-01-04-sjc1.facebook.com (31.13.77.55): icmp_req=28 ttl=244 time=387 ms
64 bytes from star-01-04-sjc1.facebook.com (31.13.77.55): icmp_req=29 ttl=244 time=411 ms
64 bytes from star-01-04-sjc1.facebook.com (31.13.77.55): icmp_req=30 ttl=244 time=401 ms
64 bytes from star-01-04-sjc1.facebook.com (31.13.77.55): icmp_req=31 ttl=244 time=439 ms
64 bytes from star-01-04-sjc1.facebook.com (31.13.77.55): icmp_req=32 ttl=244 time=432 ms
64 bytes from star-01-04-sjc1.facebook.com (31.13.77.55): icmp_req=33 ttl=244 time=255 ms
64 bytes from star-01-04-sjc1.facebook.com (31.13.77.55): icmp_req=34 ttl=244 time=367 ms
64 bytes from star-01-04-sjc1.facebook.com (31.13.77.55): icmp_req=35 ttl=244 time=386 ms
64 bytes from 31.13.77.55: icmp_req=36 ttl=244 time=484 ms
64 bytes from star-01-04-sjc1.facebook.com (31.13.77.55): icmp_req=37 ttl=244 time=499 ms
64 bytes from star-01-04-sjc1.facebook.com (31.13.77.55): icmp_req=38 ttl=244 time=404 ms
64 bytes from 31.13.77.55: icmp_req=39 ttl=244 time=469 ms
64 bytes from 31.13.77.55: icmp_req=63 ttl=244 time=13015 ms
64 bytes from 31.13.77.55: icmp_req=64 ttl=244 time=12014 ms
64 bytes from 31.13.77.55: icmp_req=65 ttl=244 time=11014 ms
64 bytes from 31.13.77.55: icmp_req=66 ttl=244 time=10014 ms
64 bytes from 31.13.77.55: icmp_req=67 ttl=244 time=9015 ms
64 bytes from 31.13.77.55: icmp_req=68 ttl=244 time=8015 ms
64 bytes from 31.13.77.55: icmp_req=69 ttl=244 time=7015 ms
64 bytes from 31.13.77.55: icmp_req=70 ttl=244 time=6015 ms
64 bytes from star-01-04-sjc1.facebook.com (31.13.77.55): icmp_req=74 ttl=244 time=2015 ms
64 bytes from star-01-04-sjc1.facebook.com (31.13.77.55): icmp_req=77 ttl=244 time=201 ms

---

### Post by praseodym on 2013-05-14
Please change the encryption mode to WPA2-AES (CCMP), not TKIP and the channel to fixed "1"

---

### Post by jaceleon on 2013-05-14
> **praseodym said:**
> Please change the encryption mode to WPA2-AES (CCMP), not TKIP and the channel to fixed "1"

I can't do that, since I'm not responsible for the router....


Anyways, I got these:

```
jaceleon@Vanguard:~$ curl -I google.com.phHTTP/1.1 301 Moved Permanently
Location: http://www.google.com.ph/
Content-Type: text/html; charset=UTF-8
Date: Tue, 14 May 2013 16:44:38 GMT
Expires: Thu, 13 Jun 2013 16:44:38 GMT
Cache-Control: public, max-age=2592000
Server: gws
Content-Length: 222
X-XSS-Protection: 1; mode=block
X-Frame-Options: SAMEORIGIN


jaceleon@Vanguard:~$ nslookup google.com.ph
Server:		127.0.1.1
Address:	127.0.1.1#53


Non-authoritative answer:
Name:	google.com.ph
Address: 122.2.128.246
Name:	google.com.ph
Address: 122.2.128.247
Name:	google.com.ph
Address: 122.2.128.251
Name:	google.com.ph
Address: 122.2.128.212
Name:	google.com.ph
Address: 122.2.128.216
Name:	google.com.ph
Address: 122.2.128.217
Name:	google.com.ph
Address: 122.2.128.221
Name:	google.com.ph
Address: 122.2.128.222
Name:	google.com.ph
Address: 122.2.128.226
Name:	google.com.ph
Address: 122.2.128.227
Name:	google.com.ph
Address: 122.2.128.231
Name:	google.com.ph
Address: 122.2.128.232
Name:	google.com.ph
Address: 122.2.128.236
Name:	google.com.ph
Address: 122.2.128.237
Name:	google.com.ph
Address: 122.2.128.241
Name:	google.com.ph
Address: 122.2.128.242


jaceleon@Vanguard:~$ ip addr list | grep ra0
4: ra0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP qlen 1000
    inet 192.168.1.114/24 brd 192.168.1.255 scope global ra0
jaceleon@Vanguard:~$ cat /etc/resolv.conf
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.1.1
search domain.name

jaceleon@Vanguard:~$ nslookup google.com.ph
Server:		127.0.1.1
Address:	127.0.1.1#53


Non-authoritative answer:
Name:	google.com.ph
Address: 58.69.77.82
Name:	google.com.ph
Address: 58.69.77.83
Name:	google.com.ph
Address: 58.69.77.84
Name:	google.com.ph
Address: 58.69.77.85
Name:	google.com.ph
Address: 58.69.77.86
Name:	google.com.ph
Address: 58.69.77.87
Name:	google.com.ph
Address: 58.69.77.88
Name:	google.com.ph
Address: 58.69.77.89
Name:	google.com.ph
Address: 58.69.77.90
Name:	google.com.ph
Address: 58.69.77.91
Name:	google.com.ph
Address: 58.69.77.92
Name:	google.com.ph
Address: 58.69.77.93




```

---

### Post by praseodym on 2013-05-14
Ok. Remove the current networkmanager wireless profile and create a new one using "ra0"

---

