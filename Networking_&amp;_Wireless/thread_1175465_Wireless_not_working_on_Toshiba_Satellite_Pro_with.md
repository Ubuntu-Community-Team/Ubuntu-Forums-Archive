---
title: "Wireless not working on Toshiba Satellite Pro with 9.04"
date: 2009-06-01
forum: Networking &amp; Wireless
---

### Post by adam_ski on 2009-06-01
Hi,

I'm having problems with wireless. I've got a dual boot machine (a Toshiba Satellite Pro laptop). I can access the wireless network using Windows XP, but not from Ubuntu 9.04. My knowledge of wireless networks is very limited, but [this thread]("http://ubuntuforums.org/showthread.php?p=6183681") suggests the following information would be useful to those that do know what they're doing to figure out the problem. Cheers in advance and sorry for all the details. I'm not sure what's useful and what isn't.

```
$ lspci
``` gives me ```
00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
02:01.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 02)
02:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:04.0 Ethernet controller: Linksys, A Division of Cisco Systems [AirConn] INPROCOMM IPN 2220 Wireless LAN Adapter (rev 01)
03:00.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

```


```
$ lsub
``` gives me ```
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 1241:1111 Belkin Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```


```
ifconfig
``` gives me ```
eth0      Link encap:Ethernet  HWaddr 00:c0:9f:a7:fb:21  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2c0:9fff:fea7:fb21/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:16469 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14631 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:17252876 (17.2 MB)  TX bytes:2580847 (2.5 MB)
          Interrupt:6 Base address:0x3800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:344 errors:0 dropped:0 overruns:0 frame:0
          TX packets:344 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:27400 (27.4 KB)  TX bytes:27400 (27.4 KB)

wlan0     Link encap:Ethernet  HWaddr 00:22:6b:94:45:b9  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0:avahi Link encap:Ethernet  HWaddr 00:22:6b:94:45:b9  
          inet addr:169.254.7.102  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1

wmaster0  Link encap:UNSPEC  HWaddr 00-22-6B-94-45-B9-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```


```
$ iwconfig
``` gives me ```
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.
```


```
$ iwlist scan
``` gives me ```

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     No scan results

pan0      Interface doesn't support scanning
```


Finally, ```
$ nm-tool
``` gives me ```
NetworkManager Tool

State: connected

- Device: eth0  [Auto eth0] ----------------------------------------------------
  Type:              Wired
  Driver:            8139too
  State:             connected
  Default:           yes
  HW Address:        00:C0:9F:A7:FB:21

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.2
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            b43
  State:             unmanaged
  Default:           no
  HW Address:        00:00:00:00:00:00

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points
```

---

### Post by superprash2003 on 2009-06-01
try **sudo iwlist scanning** ( post output of this command ) , if you still see NO SCAN RESULTS [http://www.prash-babu.com/2009/05/how-to-fix-wireless-no-scan-results-in.html](http://www.prash-babu.com/2009/05/how-to-fix-wireless-no-scan-results-in.html)

---

### Post by adam_ski on 2009-06-02
*sudo iwlist scanning* gives

```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:21:63:95:EA:76
                    ESSID:"TalkTalk92e49"
                    Mode:Master
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=43/100  Signal level:-72 dBm  Noise level=-68 dBm
                    Encryption key:on
                    IE: Unknown: 000D54616C6B54616C6B3932653439
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030101
                    IE: Unknown: 2A0104
                    IE: Unknown: 32080C1218243048606C
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=000000000d5a447e
                    Extra: Last beacon: 1252ms ago

pan0      Interface doesn't support scanning.
```

---

### Post by lisati on 2009-06-02
What the scan tells me is that your machine is recognizing that there's a nearby wireless network. Do you have a network icon showing on your top panel/taskbar? Try clicking on it, and then, if it shows, clicking on the name of the network you want to connect with.

---

### Post by adam_ski on 2009-06-02
When I click on the network icon on everything is greyed out apart from the wired connection, as shown in  [this screenshot]("http://farm4.static.flickr.com/3567/3587974795_0d2d834daf_o.png"). 

I've tried entering the SSID and the WPA password for the wireless network in the network connections (System > Preferences > Network Connections and then going to the Wireless tab and clicking "Add"). That now appears to be saved in the network connections, but "never" appears next to the name [as shown here.]("http://farm4.static.flickr.com/3662/3587974799_51d079a3f0_o.png")

---

### Post by adam_ski on 2009-06-02
Thanks for the help and pointing out to me that the laptop was actually seeing the wireless network. After I realised that I followed the advice of juky in [in this thread (post #9)]("http://ubuntuforums.org/showthread.php?t=1168561") and the wireless is now working and I'm happy.

---

### Post by mariost on 2011-05-01
Please mark the thread as solved, then.

---

