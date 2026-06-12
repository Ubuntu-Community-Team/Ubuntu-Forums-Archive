---
title: "No internet connection 9.04 after router change"
date: 2009-07-23
forum: Networking &amp; Wireless
---

### Post by Netspeed on 2009-07-23
I didn't want to steal the other thread, I read the recommendations, and here's the results:  ALSO...I turned the router security off and it didn't make a difference. 
iwlist scan
> $ sudo iwlist scanning
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:18:F8:D0:42:3B
                    ESSID:"linksys"
                    Mode:Master
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=53/100  Signal level:-74 dBm  Noise level=-67 dBm
                    Encryption key:on
                    IE: Unknown: 00076C696E6B737973
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 32088C129824B048606C
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F202010100000364000027A4000041435E0061322F00
                    IE: Unknown: DD9F0050F204104A000110103B00010310470010746F4EDA81553E03B835B6520511DF251044000102102100074C696E6B737973102300204C696E6B73797320576972656C6573732D4E2047616D696E6720526F75746572102400075752543333304E104200046E6F6E651054000800060050F2040001101100204C696E6B73797320576972656C6573732D4E2047616D696E6720526F75746572100800020004
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=0000002489ff7180
                    Extra: Last beacon: 1268ms ago
          Cell 02 - Address: 00:22:3F:9E:C5:D0
                    ESSID:"TOwireless"
                    Mode:Master
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=93/100  Signal level:-37 dBm  Noise level=-67 dBm
                    Encryption key:on
                    IE: Unknown: 000A544F776972656C657373
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 030101
                    IE: Unknown: 0706555320010B1B
                    IE: Unknown: 200100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101020003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C334E101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 2D1A4E101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3401051900000000000000000000000000000000000000
                    IE: Unknown: 3D1601051900000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010000000000
                    IE: Unknown: DD820050F204104A000110104400010210570001001041000100103B00010310470010565AA94967C14C0EAA8FF349E6F593111021000D4E6574676561722C20496E632E10230007574E523230303010240007574E523230303010420004353637381054000800060050F204000110110007574E5232303030100800020084103C000103
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=00000000fa9c4180
                    Extra: Last beacon: 1108ms ago

pan0      Interface doesn't support scanning.


ifconfig
> $ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0b:cd:a8:6e:05  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20b:cdff:fea8:6e05/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:26949 errors:0 dropped:0 overruns:0 frame:0
          TX packets:18060 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:33423277 (33.4 MB)  TX bytes:1937177 (1.9 MB)
          Interrupt:10 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:844 errors:0 dropped:0 overruns:0 frame:0
          TX packets:844 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:63304 (63.3 KB)  TX bytes:63304 (63.3 KB)

wlan0     Link encap:Ethernet  HWaddr 00:0b:cd:75:cd:75  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-0B-CD-75-CD-75-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


iwconfig
> $ iwconfig
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


Thanks for any and all help!

---

### Post by Adina on 2009-07-23
are you connected to eth0 with cable? I see you get ip address on eth0.
In my experience I could not connect to eth0 and wlan0 at the same time.
If you are connected with cable try to disconnect the cable and reboot your machine and try scan for wifi network again.

---

### Post by Bucky Ball on 2009-07-23
You need to match the ESSID and the WEP or WPA key in the router to what is in your machine. On the machine, presuming the router is serving you an IP address via DHCP:

System->Admin->Network

Unlock and click your wireless device then properties. Match the details, make sure 'Enable Roaming' is off and 'Configuration' is set to 'Automatic Configuration (DHCP)'


On the router configuration, make sure the DHCP server is on and the details for your wireless setup match the ones in your machine. You can also name the router (AP or access point).

---

### Post by Netspeed on 2009-07-23
It looks like everything you suggested is in correctly. Why does the iwlist scan show the router? It has the correct channel and everything.

---

### Post by cgb on 2009-07-23
Is this the only computer on the network?  Do any other computers have internet connectivity?  If there is no internet connectivity for any computer on the network it is possible that due to the Router swap out the DSL modem is still locked to the old Router.  Some ISP's provide modem's that lock on to the mac address of the device connected and will not provide a connection to a new device unless the modem is rebooted.  If this is the case a simple power down for about 1 minute of the modem and turn back on should do the trick.  Also reboot the router after this to ensure everything is back in sync.  Hope this helps.

---

### Post by Netspeed on 2009-07-23
There are up to 3 other computers (wired) on the network. The netbook (Windows)  can access the router and my laptop (Ubuntu) will when it's wired but not wirelessly.

---

### Post by superprash2003 on 2009-07-24
i presume your able to view the "linksys" network when you click on the network symbol on the top right bar?

---

### Post by Netspeed on 2009-07-24
Fixed! Simple too....I powered down the router while leaving the computer up. Once the Netgear router came back up, the laptop found the network...WPA2 encryption and all.

---

### Post by Iowan on 2009-07-24
Sometimes it's the simple things... Congrats!

---

