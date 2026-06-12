---
title: "little help ;)"
date: 2009-04-12
forum: Networking &amp; Wireless
---

### Post by smotko on 2009-04-12
[SIZE="3"]Ifconfig[/SIZE]
[I][SIZE="2"]
eth1      Link encap:Ethernet  HWaddr 00:21:00:0e:69:77  

          inet6 addr: fe80::221:ff:fe0e:6977/64 Scope:Link

          UP BROADCAST MULTICAST  MTU:1500  Metric:1

          RX packets:0 errors:0 dropped:0 overruns:0 frame:0

          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000 

          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

          Interrupt:21 [/SIZE]

[/I][SIZE="3"]iwconfig[/SIZE]

[I][SIZE="2"]eth1      IEEE 802.11bg  ESSID:""  Nickname:""

          [SIZE="6"][COLOR="Red"]Mode:Managed[/COLOR][/SIZE]  Frequency:2.412 GHz  Access Point: Not-Associated   

          Bit Rate:54 Mb/s   Tx-Power:32 dBm   

          Retry min limit:7   RTS thr:off   Fragment thr:off

          Power Managementmode:All packets received

          Link Quality=5/5  Signal level=0 dBm  Noise level=-57 dBm

          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0

          Tx excessive retries:0  Invalid misc:0   Missed beacon:0[/SIZE]


[/I][SIZE="3"]airmon-ng start eth1[/SIZE]
[SIZE="2"]
[I]Found 4 processes that could cause trouble.

If airodump-ng, aireplay-ng or airtun-ng stops working after

a short period of time, you may want to kill (some of) them!



PID	Name

3268	NetworkManager

3286	wpa_supplicant

3296	avahi-daemon

3297	avahi-daemon





Interface	Chipset		Driver



eth1		Unknown 		[COLOR="Red"][SIZE="6"]wl (monitor mode enabled)[/SIZE][/COLOR]
[/SIZE]

[/I]

[B][SIZE="6"]
no work :(( please send me how change manager mod in MONITOR MOD.
Thanks.[/SIZE][/B]

---

### Post by chili555 on 2009-04-12
Man, oh man! I just got a new prescription in my glasses and now you broke them! Seriously, huge fonts, bold and in red letters only do one thing for us: turn us off. Please stop.

Please open a terminal and do these commands:```
sudo /etc/init.d/NetworkManager stop
sudo ifconfig eth1 down
sudo iwconfig eth1 mode monitor
iwconfig eth1
```Is it now in monitor mode? If not, please post back quietly.

---

