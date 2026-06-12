---
title: "Aircrack / Channel -1 / Intel® PRO/Wireless 3945ABG / Ubuntu 10.10"
date: 2010-12-08
forum: Networking &amp; Wireless
---

### Post by Veehmot on 2010-12-08
Hi,

I spent all the day trying to get this app to work. From downloading Ubuntu to trying to download compat-wireless drivers.
Ok, let's begging with what I'm doing.

**[SIZE="5"]airmon-ng start[/size]**
```
jorjon@jorjon-Aspire-6920:~$ sudo airmon-ng start wlan0 11


Found 5 processes that could cause trouble.
If airodump-ng, aireplay-ng or airtun-ng stops working after
a short period of time, you may want to kill (some of) them!
-e 
PID	Name
889	avahi-daemon
890	NetworkManager
891	avahi-daemon
934	wpa_supplicant
936	dhclient


Interface	Chipset		Driver

wlan0		Intel 3945ABG	iwl3945 - [phy0]
				(monitor mode enabled on mon0)
```

**[SIZE="5"]iwconfig[/size]**
```
jorjon@jorjon-Aspire-6920:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=14 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
mon0      IEEE 802.11abg  Mode:Monitor  Tx-Power=14 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
```

**[SIZE="5"]airodump-ng[/size]**
```
jorjon@jorjon-Aspire-6920:~$ sudo airodump-ng mon0

CH  6 ][ Elapsed: 2 mins ][ 2010-12-09 01:05                                  
                                                                               
 BSSID              PWR  Beacons    #Data, #/s  CH  MB   ENC  CIPHER AUTH ESSID
                                                                               
 F0:7D:68:4F:FB:DA  -80      442        0    0   6  54e. WPA2 CCMP   PSK  dlink
 00:E0:4D:A2:91:10  -89       70        0    0   6  54   WEP  WEP         Speed
 00:23:F8:B7:4B:FF  -88       69        0    0  11  54 . WEP  WEP         vane 
                                                                               
 BSSID              STATION            PWR   Rate    Lost  Packets  Probes
```

NOTE: I leave this airodump command running, on a new terminal.

**[SIZE="5"]airodump-ng[/size]**
```
jorjon@jorjon-Aspire-6920:~$ sudo airodump-ng -c 11 --bssid 00:23:f8:b7:4b:ff -w wepdump -i mon0
 CH 11 ][ Elapsed: 4 s ][ 2010-12-09 01:07 ][ fixed channel mon0: -1           
                                                                               
 BSSID              PWR RXQ  Beacons    #Data, #/s  CH  MB   ENC  CIPHER AUTH E
                                                                               
 00:23:F8:B7:4B:FF  -89   0       23        0    0  11  54 . WEP  WEP         v
                                                                               
 BSSID              STATION            PWR   Rate    Lost  Packets  Probes 
```

NOTE: I also leave the above command running in a new terminal.

**[SIZE="5"]aireplay-ng[/size]**
```
jorjon@jorjon-Aspire-6920:~$ sudo aireplay-ng -1 0 -e vane -a 00:23:f8:b7:4b:ff -h 00:1f:3c:ac:d7:57 mon0
01:10:31  Waiting for beacon frame (BSSID: 00:23:F8:B7:4B:FF) on channel -1
01:10:32  mon0 is on channel -1, but the AP uses channel 11
```

And that is the problem. It says I'm in channel -1... And I'm stuck here... Any tip will be welcome :)

**[size="7"]More Information[/size]**

**[SIZE="5"]lspci[/size]**
```
jorjon@jorjon-Aspire-6920:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 04)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 04)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 04)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 04)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 04)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 04)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 04)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 04)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 04)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f4)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 04)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 04)
01:00.0 VGA compatible controller: nVidia Corporation G84 [GeForce 9500M GS] (rev a1)
02:00.0 Ethernet controller: Atheros Communications AR8121/AR8113/AR8114 Gigabit or Fast Ethernet (rev b0)
08:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
```

**[SIZE="5"]Kernel Version[/size]**
```
jorjon@jorjon-Aspire-6920:~$ uname -r
2.6.35-23-generic
```

**[SIZE="5"]ifconfig[/size]**
```
jorjon@jorjon-Aspire-6920:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:a0:d1:af:32:c7  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2a0:d1ff:feaf:32c7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3318 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3027 errors:0 dropped:0 overruns:0 carrier:2
          collisions:0 txqueuelen:1000 
          RX bytes:2300023 (2.3 MB)  TX bytes:477714 (477.7 KB)
          Interrupt:49 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)

mon0      Link encap:UNSPEC  HWaddr 00-1F-3C-AC-D7-57-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST NOTRAILERS RUNNING PROMISC ALLMULTI  MTU:1500  Metric:1
          RX packets:7888 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1531661 (1.5 MB)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:1f:3c:ac:d7:57  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```

**[SIZE="5"]iwlist channel[/size]**
```
jorjon@jorjon-Aspire-6920:~$ iwlist wlan0 Channel
wlan0     24 channels in total; available frequencies :
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
          Channel 36 : 5.18 GHz
          Channel 40 : 5.2 GHz
          Channel 44 : 5.22 GHz
          Channel 48 : 5.24 GHz
          Channel 52 : 5.26 GHz
          Channel 56 : 5.28 GHz
          Channel 60 : 5.3 GHz
          Channel 64 : 5.32 GHz
          Channel 149 : 5.745 GHz
          Channel 153 : 5.765 GHz
          Channel 157 : 5.785 GHz
          Channel 161 : 5.805 GHz
          Channel 165 : 5.825 GHz
          Current Frequency:2.462 GHz (Channel 11)
```

```
jorjon@jorjon-Aspire-6920:~$ iwlist mon0 Channel
mon0      24 channels in total; available frequencies :
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
          Channel 36 : 5.18 GHz
          Channel 40 : 5.2 GHz
          Channel 44 : 5.22 GHz
          Channel 48 : 5.24 GHz
          Channel 52 : 5.26 GHz
          Channel 56 : 5.28 GHz
          Channel 60 : 5.3 GHz
          Channel 64 : 5.32 GHz
          Channel 149 : 5.745 GHz
          Channel 153 : 5.765 GHz
          Channel 157 : 5.785 GHz
          Channel 161 : 5.805 GHz
          Channel 165 : 5.825 GHz
```

My guess is that iwlist should state that I'm in channel 11 for the device mon0, and you can clearly see that it's missing. Also, I downloaded compat-wireless package, throug synaptic. But I think I need to run it, but I can't figure out how. I don't know if I need those drivers.

Thanks for reading!

---

### Post by Veehmot on 2010-12-12
Well no answers... But anyway I found a workaround.
The solution is not to use
```
airmon-ng start wlan0
```
Instead of that, I do

```
* hard-lock the wireless card, eg: turn off and on the button on the keyboard
airmon-ng stop wlan
iwconfig wlan0 channel 11
iwconfig wlan0 method monitor
```

So, I don't use airmon-ng start for monitoring. And for all other operations, I use the actual card, wlan0, instead of using mon0.

---

