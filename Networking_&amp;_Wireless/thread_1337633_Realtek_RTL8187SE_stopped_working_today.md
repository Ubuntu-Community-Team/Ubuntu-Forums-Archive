---
title: "Realtek RTL8187SE stopped working today"
date: 2009-11-25
forum: Networking &amp; Wireless
---

### Post by confused_user on 2009-11-25
I got home from work today and my wireless card will connect momentarily to my router and then it disconnects.

I am connecting from another Ubuntu 9.10 machine just fine (different hardware altogether though but same router)

I'm at wits end with this and will buy whoever can help me a pint!!!

i hope i have provided enough of the right info below.

```
matt@matt-netbook:~$ lspci | grep RTL8187SE
02:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8187SE Wireless LAN Controller (rev 22)

matt@matt-netbook:~$ ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:03:0d:b4:16:43  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:26 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:21:85:7a:cf:67  
          inet6 addr: fe80::221:85ff:fe7a:cf67/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:81 errors:0 dropped:173 overruns:0 frame:0
          TX packets:1258 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:34716 (34.7 KB)  TX bytes:85405 (85.4 KB)
          Interrupt:17 Memory:f8c00000-f8c00100 

matt@matt-netbook:~$ iwconfig 
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     802.11b/g  ESSID:"repeater-bridge1"  
          Mode:Managed  Frequency=2.427 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   
          Retry:on   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/100  Signal level=0 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

matt@matt-netbook:~$ lsmod | grep rtl
rtl8187se             200472  0 

matt@matt-netbook:~$ dmesg | grep rtl8187se
[    8.659620] rtl8187se: module is from the staging directory, the quality is unknown, you have been warned.

matt@matt-netbook:~$ dmesg | grep rtl8187se
[    8.659620] rtl8187se: module is from the staging directory, the quality is unknown, you have been warned.
matt@matt-netbook:~$ sudo lshw -C network
  
       description: Wireless interface
       product: RTL8187SE Wireless LAN Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 22
       serial: 00:21:85:7a:cf:67
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=r8180 latency=0 multicast=yes wireless=802.11b/g
       resources: irq:17 ioport:ec00(size=256) 

matt@matt-netbook:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     No scan results

matt@matt-netbook:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:16:B6:DA:66:56
                    ESSID:"repeater-bridge1"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:2
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54 
                    Quality=77/100  Signal level=-42 dBm  Noise level=-105 dBm
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 1ms ago
          Cell 02 - Address: 00:24:17:20:D3:1F
                    ESSID:"BeBox"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54 
                    Quality=44/100  Signal level=-65 dBm  Noise level=-82 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 166ms ago
          Cell 03 - Address: 00:1D:73:D9:1B:78
                    ESSID:"dd-wrt"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:2
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 11 9 12 18 24 36 48 54 
                    Quality=43/100  Signal level=-65 dBm  Noise level=-81 dBm
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 17ms ago
          Cell 04 - Address: 00:16:E6:3C:C1:72
                    ESSID:"Draytek2800a"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:4
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 9 11 6 12 18 24 36 48 54 
                    Quality=42/100  Signal level=-66 dBm  Noise level=-80 dBm
                    IE: WPA Version 1
                        Group Cipher : WEP-40
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : WEP-40
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 203ms ago

matt@matt-netbook:~$ lsb_release -d
Description:	Ubuntu 9.10

matt@matt-netbook:~$ uname -mr
2.6.31-15-generic i686

matt@matt-netbook:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                                                               [ OK ]
```

---

### Post by confused_user on 2009-11-25
OK what am i doing wrong?  :D

Can nobody help me?

---

### Post by confused_user on 2009-11-26
Perhaps a frivolous picture might tempt some of you in? 

[IMG]http://franksemails.com/pics/misc%2Dpics%2D23%2D11%2D09/image00191.jpg[/IMG]

---

### Post by confused_user on 2009-11-26
I deleted all references to the wireless router in questions from network manager and reconnected.  It worked this time.

Thanks so much for everyones help ;)

---

