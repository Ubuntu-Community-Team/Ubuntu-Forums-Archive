---
title: "Connecting to a Wireless Network by Command Screen"
date: 2012-10-10
forum: Networking &amp; Wireless
---

### Post by serhancan on 2012-10-10
Hi there,
I am using my laptop's internet connection as a hotspot and trying to connect it by using my beagleboard-xm which has ubuntu 12-04 armhf running. Here is my wireless network's properties:


ubuntu@arm:/etc/network$ iwlist scan
lo        Interface doesn't support scanning.

usb0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: FE:7A:37:4A:19:CF
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=-29 dBm
                    Encryption key:on
                    ESSID:"ghostrider"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Ad-Hoc
                    Extra:tsf=000000000d1fbb47
                    Extra: Last beacon: 1843ms ago
                    IE: Unknown: 000A67686F73747269646572
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 06020000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A2C181BFF00000000000000000000000000000000000000000000
                    IE: Unknown: 3D16010800000000FF000000000000000000000000000000
                    IE: Unknown: DD09001018020000000000


I edited /etc/network/interfaces document and added my wireless network's properties:


ubuntu@arm:/etc/network$ cat interfaces 
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp
# Example to keep MAC address between reboots
#hwaddress ether DE:AD:BE:EF:CA:FE

# WiFi Example
auto wlan0
iface wlan0 inet dhcp
    wpa-ssid "ghostrider"
    wpa-psk  "34bddf67b1"


However I cannot connect to my wireless network:

ubuntu@arm:/etc/network$ iwconfig
lo        no wireless extensions.

usb0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          
eth0      no wireless extensions.


What is the problem here? Do I need to edit any other files also? (Those quotation marks should exist, right?)

Regards,
Serhan

---

### Post by serhancan on 2012-10-10
Also now I tried:

ubuntu@arm:~$ cat /etc/network/interfaces 
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp
# Example to keep MAC address between reboots
#hwaddress ether DE:AD:BE:EF:CA:FE

# WiFi Example
auto wlan0
iface wlan0 inet dhcp
    wpa-ssid "ghostrider"
    wpa-psk "bd9f5cbedb4f7aca5ca8b595386e8679d82ee63bf380c544d34542acc21892a1"

and also tried without the quotation marks: (quotation marks at the wpa-ssid stay)

wpa-psk bd9f5cbedb4f7aca5ca8b595386e8679d82ee63bf380c544d34542acc21892a1

---

