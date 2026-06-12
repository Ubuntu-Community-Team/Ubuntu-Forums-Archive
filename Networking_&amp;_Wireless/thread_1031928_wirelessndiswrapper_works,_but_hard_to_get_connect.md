---
title: "wireless/ndiswrapper works, but hard to get connect"
date: 2009-01-05
forum: Networking &amp; Wireless
---

### Post by cokeonice on 2009-01-05
I am running a fresh install of Ubuntu 8.10.

I have a Netgear WG111T (USB).  

I have installed ndiswrapper and loaded the Windows driver for this wireless usb.

It works...sort of.

It does not start at startup.  The blue spinning thing spins around the two dots.  First one turns green and then the other.  The rollover message states that it is trying to get an address from my wireless router and then it fails.  Maybe one out of 20 times it actually connects.

Any ideas as to what I can do to make this thing a bit more consistent?

Thank you!

```
gomer@haspiles:~$ ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:6 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:376 (376.0 B)  TX bytes:376 (376.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:14:6c:37:88:58  
          inet addr:192.168.1.50  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::214:6cff:fe37:8858/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:791 errors:0 dropped:0 overruns:0 frame:0
          TX packets:824 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:820813 (820.8 KB)  TX bytes:150220 (150.2 KB)
```

```
im@home:~$ iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"DINKDINKDINK"  
          Mode:Managed  Frequency:2.417 GHz  Access Point: 00:1F:33:2C:D1:A6   
          Bit Rate=54 Mb/s   
          Power Management:off
          Link Quality:75/100  Signal level:-48 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.
```

```
back@you:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:14:6c:37:88:58
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+netwg11t driverversion=1.53+NETGEAR,09/05/2005,1.5.0.21 ip=192.168.1.50 multicast=yes wireless=IEEE 802.11g
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 3a:5d:4f:17:d1:b7
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
```

```
right@home:~$ iwlist scanning
lo        Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:1A:70:FB:E9:75
                    ESSID:""
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.417 GHz (Channel 2)
                    Quality:43/100  Signal level:-68 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 02 - Address: 00:13:10:96:99:87
                    ESSID:"linksys"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:21/100  Signal level:-82 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 03 - Address: 00:0F:66:C5:67:BB
                    ESSID:"home"
                    Protocol:IEEE 802.11g
                    Mode:Managed

                    Frequency:2.462 GHz (Channel 11)
                    Quality:9/100  Signal level:-90 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: 00:1F:33:2C:D1:A6
                    ESSID:"DINKDINKDINK"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.417 GHz (Channel 2)
                    Quality:59/100  Signal level:-58 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: 00:12:17:04:B8:05
                    ESSID:"sst-pr-1"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:9/100  Signal level:-90 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: 00:1E:2A:50:17:BA
                    ESSID:"NETGEAR"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:15/100  Signal level:-86 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: 00:14:6C:F8:B1:C0
                    ESSID:"NETGEAR"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:18/100  Signal level:-84 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0

pan0      Interface doesn't support scanning
```

---

### Post by Ayuthia on 2009-01-06
The only things that I see is that you are using WPA and it is on channel 2 (which is shared by another router that is close).  Have you tried connecting with the channel being something else besides 2, 6, or 11?  The other thing to check is to see if your wireless connects consistently without WPA.  If it does, you might try another network manager like wicd or see if it connects consistently if you connect to it by configuring /etc/network/interfaces.  Here is a link that might help:
[http://ubuntuforums.org/showthread.php?t=202834](http://ubuntuforums.org/showthread.php?t=202834)

---

