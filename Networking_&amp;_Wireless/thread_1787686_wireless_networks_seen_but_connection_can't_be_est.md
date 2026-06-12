---
title: "wireless networks seen but connection can't be established"
date: 2011-06-21
forum: Networking &amp; Wireless
---

### Post by danpaluska on 2011-06-21
i have an old compaq machine running ubuntu.

i've tried 2 different wireless devices, 
1. usb from zonet
2. pci card from sabrent

i got them both installed and they both successfully scan and see a range of networks. but when i enter a network key, it churns for a while and then never successfully connects. this has happened to me in 2 different offices with this same machine.

for a bit boring video that shows the exact behavior, see here:
[http://www.youtube.com/watch?v=GOayRx1E9n0](http://www.youtube.com/watch?v=GOayRx1E9n0)

for kicks, i installed puppy linux and got the same type of error. i can see all the networks but can't connect. 

yes password is correct, checked and double checked. also tried on multiple different networks.

is it possible that there can be a lower level hardware issue that would cause such a failure?

thanks! i'm awfully confused by this one.

---

### Post by danpaluska on 2011-06-22
so, this maybe is not technically the right place for this but thought i would include as it is related. i tried puppy linux as well and when i run network on that, this is the logfile for the failed network connection...
i snipped a bit of the beginning where it detected a bunch of networks and i replaced passwords with *******
thanks,
dan

> Information about this interface:
 Interface: wlan0  Driver: rt61pci  Bus: pci  MacAddress: 00:0C:0A:42:19:7C
 Description: Ralink RT61 PCI PCMCIA Wireless LAN driver. 
 
STEP1a: ifconfig wlan0 up
STEP1b: iwlist wlan0 scan
wlan0     Scan completed :
  [ some stuff removed ... ]
          Cell 08 - Address: 90:84:0D:D7:55:8B
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/70  Signal level=-38 dBm  
                    Encryption key:on
                    ESSID:"Hand Works"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000001403c423741
                    Extra: Last beacon: 428ms ago
                    IE: Unknown: 000A48616E6420576F726B73
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010B
                    IE: Unknown: 0706555320010B1E
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2D1AAC4117FFFFFF0000000000000000000000000000000000000000
                    IE: Unknown: 3D160B001100000000000000000000000000000000000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101010003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C33AC4117FFFFFF0000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340B001100000000000000000000000000000000000000
                    IE: Unknown: DD1700039301710120000E90840DD7558B0B90840DD7558C95
                    IE: Unknown: DD070017F203020180
                    IE: Unknown: DD0B0017F20100010100000007
STEP1c: ifconfig wlan0 down
STEP2: iwconfig wlan0 mode managed
STEP3: iwconfig wlan0 channel 11
STEP4: iwconfig wlan0 essid "Hand Works"
STEP5: iwconfig wlan0 key restricted ****************
STEP5a: ifconfig wlan0 up

ERROR, TIMEOUT. Have not got an Access Point.
Result of 'iwconfig wlan0':
wlan0     IEEE 802.11bg  ESSID:"Hand Works"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Tx-Power=2 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          

STEP5: iwconfig wlan0 key open ****************
STEP5a: ifconfig wlan0 up

ERROR, TIMEOUT. Have not got an Access Point.
Result of 'iwconfig wlan0':
wlan0     IEEE 802.11bg  ESSID:"Hand Works"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Tx-Power=2 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          

 
*********************************************************
LAST 10 LINES of /var/log/messages:
Jun 22 18:08:59 puppypc daemon.debug dhcpcd: wlan0: executing `/lib/dhcpcd/dhcpcd-run-hooks', reason STOP
Jun 22 18:08:59 puppypc daemon.info dhcpcd: waiting for pid 12646 to exit
Jun 23 09:09:25 puppypc user.debug kernel: wlan0: direct probe to AP 90:84:0d:d7:55:8b (try 1)
Jun 23 09:09:25 puppypc user.debug kernel: wlan0: direct probe responded
Jun 23 09:09:25 puppypc user.debug kernel: wlan0: authenticate with AP 90:84:0d:d7:55:8b (try 1)
Jun 23 09:09:25 puppypc user.debug kernel: wlan0: authenticated
Jun 23 09:09:25 puppypc user.debug kernel: wlan0: associate with AP 90:84:0d:d7:55:8b (try 1)
Jun 23 09:09:25 puppypc user.debug kernel: wlan0: RX AssocResp from 90:84:0d:d7:55:8b (capab=0x431 status=40 aid=266)
Jun 23 09:09:25 puppypc user.debug kernel: wlan0: AP denied association (code=40)
Jun 23 09:09:25 puppypc user.debug kernel: wlan0: deauthenticating from 90:84:0d:d7:55:8b by local choice (reason=3)


---

