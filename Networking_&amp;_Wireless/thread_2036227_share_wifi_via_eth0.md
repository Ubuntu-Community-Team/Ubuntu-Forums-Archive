---
title: "share wifi via eth0"
date: 2012-08-01
forum: Networking &amp; Wireless
---

### Post by Kyentei on 2012-08-01
Hello all,

(Using Xubuntu 11.10)

I work at a technical and creative youth centre and we recently moved to a new place inside a schoolbuilding. Until we have our official connection, we use wireless to connect to the school's network. However, it requires an account (we have only 1) and a proxy. Thus far, I have set up a laptop that connects to the wireless network and then shares the connection through it's eth0 port (using the options in nm-applet to share a connection). The PC after that is our actual gateway, which gets an IP from the laptop, then sharing the connection to the rest of our network.

All that works now is port 80, but https is blocked by the laptop. I'm thinking nm-applet is only forwarding on port 80, but not 443. How do I fix this? (I have already troubleshooted, and know for sure the gateway is not blocking 443)

Thanks in advance!

---

### Post by daniroma on 2012-10-04
Hi! 

I use xubuntu 12.04 and try to  connect my wireless devices to wired Internet through wifi usb adapter.
Please tell me if it is possible in xubuntu (ubuntu has hotspot option to do that).

Here are outputs of usual comands:
[COLOR=DimGray]daniel@daniel-desktop:~$ lsusb[/COLOR]
[COLOR=DimGray]Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0bda:8171 Realtek Semiconductor Corp. RTL8188SU 802.11n WLAN Adapter
Bus 003 Device 002: ID 045e:00f7 Microsoft Corp. LifeCam VX-1000
Bus 002 Device 002: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)[/COLOR]

[COLOR=DarkSlateGray]daniel@daniel-desktop:~$ iwconfig
lo        no wireless extensions.

wlan0     unassociated  Nickname:"rtl_wifi"
          Mode:Ad-Hoc  Cell: Not-Associated   Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

daniel@daniel-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0c:46:b2:8e:97  
          inet addr:78.96.247.33  Bcast:78.96.247.255  Mask:255.255.252.0
          inet6 addr: fe80::20c:46ff:feb2:8e97/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:29534 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3442 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5335922 (5.3 MB)  TX bytes:511858 (511.8 KB)
          Interrupt:21 Base address:0xde00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:300 errors:0 dropped:0 overruns:0 frame:0
          TX packets:300 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:26457 (26.4 KB)  TX bytes:26457 (26.4 KB)

wlan0     Link encap:Ethernet  HWaddr 00:14:d1:d3:e8:bd  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)[/COLOR]

[COLOR=DimGray]daniel@daniel-desktop:~$ iwlist wlan0 scan
wlan0     Scan completed :
          Cell 01 - Address: 00:1E:58:0C:F6:9C
                    ESSID:"aadinicu"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:wpa_ie=dd160050f20101000050f20201000050f20201000050f202
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Extra:rsn_ie=30180100000fac020200000fac02000fac040100000fac020000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    Signal level=47/100  
          Cell 02 - Address: 02:11:87:67:DE:02
                    ESSID:"Danielwifi"
                    Protocol:IEEE 802.11bg
                    Mode:Ad-Hoc
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality:0  Signal level:0  Noise level:0[/COLOR]

Looking forward for your answer.

---

