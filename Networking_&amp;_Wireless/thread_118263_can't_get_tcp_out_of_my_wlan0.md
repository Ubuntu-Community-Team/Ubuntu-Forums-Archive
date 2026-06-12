---
title: "can't get tcp out of my wlan0"
date: 2006-01-16
forum: Networking &amp; Wireless
---

### Post by gimliy on 2006-01-16
Hello

I have a atmel based wlan usb stick and hotplug installed a driver that seems to work. I think i configured everything correctly but STILL i cannot get a single tcp packet out of my wlan interface. There is no firewall present..

Here is some input:

###  ifconfig wlan0

wlan0     Protokoll:Ethernet  Hardware Adresse 00:40:F4:AA:F3:E0
          inet Adresse:192.168.0.1  Bcast:192.168.0.255  Maske:255.255.255.0
          inet6 Adresse: fe80::240:f4ff:feaa:f3e0/64 Gültigkeitsbereich:Verbindung
          UP BROADCAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)


### iwlist wlan0 scan

iwlist wlan0 scan
wlan0     Scan completed :
          Cell 01 - Address: 02:00:96:43:31:1A
                    ESSID:"iw"
                    Mode:Ad-Hoc
                    Channel:11
                    Encryption key:off
                    Quality:0/0  Signal level:55/255  Noise level:0/0
                    Bit Rate:1 Mb/s
                    Bit Rate:2 Mb/s
                    Bit Rate:5.5 Mb/s
                    Bit Rate:11 Mb/s


### iwconfig

wlan0     IEEE 802.11-DS  ESSID:"iw"  Nickname:"okuwlan"
          Mode:Ad-Hoc  Frequency:2.462 GHz  Cell: 02:00:96:43:31:1A
          Bit Rate:11 Mb/s   Tx-Power=15 dBm
          Retry limit:8   RTS thr=1536 B   Fragment thr=1536 B
          Power Management:off
          Link Quality=0/0  Signal level=125/255  Noise level=0/0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

### sudo tcpdump -i wlan0 and ping from a second machine...


listening on wlan0, link-type EN10MB (Ethernet), capture size 96 bytes
23:53:32.278700 IP truncated-ip - 4 bytes missing! 192.168.0.2 > 192.168.0.1: ICMP echo request, id 768, seq 9728, length 40
23:53:37.285847 IP truncated-ip - 4 bytes missing! 192.168.0.2 > 192.168.0.1: ICMP echo request, id 768, seq 9984, length 40
23:53:42.293998 IP truncated-ip - 4 bytes missing! 192.168.0.2 > 192.168.0.1: ICMP echo request, id 768, seq 10240, length 40




I obviously receive packets but there is no way wlan0 will answer that :)

Help appreciated ...

---

