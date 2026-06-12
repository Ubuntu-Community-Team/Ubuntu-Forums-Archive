---
title: "AR2425 karmic problem"
date: 2009-11-18
forum: Networking &amp; Wireless
---

### Post by junkfer on 2009-11-18
Hi All!

I have a "two day" problem with an asus f5n note with this wifi card on karmic.

The dmesg show the following output:
jfasusf5n:~$ dmesg | grep ath
[   13.948593] ath5k 0000:05:00.0: PCI INT A -> Link[LNED] -> GSI 19 (level, low) -> IRQ 19
[   13.948603] ath5k 0000:05:00.0: setting latency timer to 64
[   13.949077] ath5k 0000:05:00.0: registered as 'phy0'
[   14.071904] ath: EEPROM regdomain: 0x60
[   14.071908] ath: EEPROM indicates we should expect a direct regpair map
[   14.071914] ath: Country alpha2 being used: 00
[   14.071916] ath: Regpair used: 0x60
[   14.697940] Registered led device: ath5k-phy0::rx
[   14.697961] Registered led device: ath5k-phy0::tx
[   14.697966] ath5k phy0: Atheros AR2425 chip found (MAC: 0xe2, PHY: 0x70)

but 

jfasusf5n:~$ ifconfig phy0
phy0: error fetching interface information: Device not found

The NetworkManager shows that the wireless network is disconnected, and shows no one accessible networks.  In the BIOS the wifi card is enabled, its led is lighting, so seems everything is fine, but car is not working. 

At the last two day i tested madwifi dirver, compact, backport-modules, but i dont know where must work correctly under karmic. Has anyone helping hands for me?

many thanks, with regards, 

                     SirFrankie

---

### Post by chili555 on 2009-11-18
> jfasusf5n:~$ ifconfig phy0
phy0: error fetching interface information: Device not foundI don't believe phy0 is the correct interface. How about letting us see:```
ifconfig
iwconfig
```Thanks.

---

### Post by junkfer on 2009-11-18
thanks to response,

jfasusf5n:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  Mode:Managed  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
vboxnet0  no wireless extensions.

ppp0      no wireless extensions.

jfasusf5n:~$ ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:1f:c6:26:c9:f0  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:26 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:960 (960.0 B)  TX bytes:960 (960.0 B)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:89.223.173.49  P-t-P:10.64.64.64  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:16670 errors:0 dropped:0 overruns:0 frame:0
          TX packets:15784 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:14203054 (14.2 MB)  TX bytes:3297906 (3.2 MB)

wlan0     Link encap:Ethernet  HWaddr 00:15:af:9f:08:82  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


okay, maybe wlan0?

---

### Post by chili555 on 2009-11-18
> okay, maybe wlan0?Exactly. Your card seems to be working fine except it has not associated with an access point. What does this tell us?```
sudo iwlist wlan0 scan
```Thanks.

---

### Post by junkfer on 2009-11-19
Hi, thanks, yepp there is my problem:

jfasusf5n:~$ sudo iwlist wlan0 scan
[sudo] password for junkertf: 
wlan0     No scan results

jfasusf5n:~$ iwlist wlan0 scan
wlan0     No scan results

i am sure, that there must be at least 2 or 3. But if i am at home, i will reply the scan, while there is my Linksys WRT54GL router with WPA2-PSK.

Question: What is the problem, if iwlist scah shows this home network, but the networkmanager not?

---

### Post by LexRoss on 2009-11-19
Hi Ferenc,

I have the same Asus F5N laptop as you do with exact same wireless controller. And I can confirm that your wifi card is obviously working fine.
My dmesg is exactly like yours. So ath5k is the right driver, and is found in kernel/drivers/net/wireless/ath/ath5k/ath5k.ko as 'modprobe -l | grep ath' reports.

wlan0 is the correct network interface as well. The only thing is, that your wlan0 interface has no IP address assigned to it. Please make sure that the hardware wifi switch on your laptop located on the left side is switched to "on" position. Then do some checking.

1. 'ifconfig wlan0' returns:
wlan0     Link encap:Ethernet  HWaddr 00:15:af:54:a5:88  
          inet6 addr: fe80::215:afff:fe54:a588/64 Range:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:62239 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9286 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:14751546 (14.7 MB)  TX bytes:2815852 (2.8 MB)

Please note that there is IPv6 (inet6) address assigned but no IPv4 (inet) address yet.

2. 'iwlist wlan0 scan' returns:
wlan0     No scan results

while Network Manager does show wireless networks available. This is because scanning is a privileged operation, and you should run it as root,
'sudo iwlist wlan0 scan'. Then you should see the list of available networks similar to this:

wlan0     Scan completed :
          Cell 01 - Address: 00:21:91:0A:15:11
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=17/70  Signal level=-93 dBm  
                    Encryption key:on
                    ESSID:"aero"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000127409a4b6
                    Extra: Last beacon: 900ms ago
                    IE: Unknown: 00046165726F
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 32080C1218243048606C
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C334C101FFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3406000700000000000000000000000000000000000000
                    IE: Unknown: 2D1A4C101FFFFF000000000000000000000000000004000000000000
                    IE: Unknown: 3D1606001300000000000000000000000000000000000000
                    IE: Unknown: DD050050F20500
                    IE: Unknown: DD790050F204104A0001101044000102103B00010310470010FD046F0DA6293C9487EDC11E789858E71021000E442D4C696E6B2053797374656D73102300074449522D363135102400024232104200046E6F6E651054000800060050F204000110110011576972656C657373204E20526F7574657210080002008C
          Cell 02 - Address: 00:21:91:D4:14:BD
                    Channel:12
                    Frequency:2.467 GHz (Channel 12)
                    Quality=66/70  Signal level=-44 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000da45a62180
                    Extra: Last beacon: 290ms ago
                    IE: Unknown: 0000
                    IE: Unknown: 010482848B96
                    IE: Unknown: 03010C
                    IE: Unknown: 2A0100
                    IE: Unknown: 32088C129824B048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD070050F202000100
                    IE: Unknown: 050400010000
                    IE: Unknown: DD0E0050F204104A0001101044000102

Please report if wireless networks are found in your case. If they are but you cannot see them in Network Manager then create a new user, log in as that user and it should be fine. My NM applet was screwed up by Intrepid NM user configuration files.

3. Now, on my wireless router I have hidden wireless network secured by WPA Personal (WPA2 only, TKIP and AES). There is also DHCP server configured on my wireless router to serve IP addresses to both wired and wireless clients. This is essential or otherwise you would have to manually assign correct IP address to your wlan0 interface.

So I go to Network Manager applet and connect to my wireless router using "connect to hidden network" menu entry. If your network is not hidden, then you should be able to select it from the list.


In my case, the connection is established successfully and I can see a healthy 100% signal. If I right-click on NM applet and choose connection properties, then I can see the tab for my wireless connection which gives me network name (SSID), the driver being used (ath5k) and IP address obtained from my server via DHCP. Same thing is confirmed by 'ifconfig wlan0' command:

wlan0     Link encap:Ethernet  HWaddr 00:15:af:54:a5:88  
          inet addr:192.168.0.111  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::215:afff:fe54:a588/64 Range:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:62258 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9332 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:14753595 (14.7 MB)  TX bytes:2824797 (2.8 MB)

Note the "inet addr:" line with obtained IP address. If you do not have DHCP server configured on your wireless access point then you should assign IP address by hand before trying to connect:

'sudo ifconfig wlan0 inet 192.168.0.111 mask 255.255.255.0'

where IP address must belong to the same network as your access point in.

Please report 'sudo iwlist wlan0 scan' command output. I am convinced at this point that the problem is either with wireless on/off switch on your laptop or with your wireless access point misconfiguration. Waiting for your reply.

Lex

---

### Post by junkfer on 2009-11-19
this would be a hard writed message.... i dont know how to say... i am so huge lama....
sorry man's, and thanks for the time spend to solve "my problem", all wifi and bluetooth is working fine now.

"wlan0 is the correct network interface as well. The only thing is, that your wlan0 interface has no IP address assigned to it. Please make sure that the hardware wifi switch on your laptop located on the left side is switched to "on" position. Then do some checking."

so, my apologize, this is make the fuse off at me, and right now solved the problem... 

now one time many thanks, with best regards,  SirFrankie

---

