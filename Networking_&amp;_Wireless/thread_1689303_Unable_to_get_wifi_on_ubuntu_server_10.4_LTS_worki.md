---
title: "Unable to get wifi on ubuntu server 10.4 LTS working"
date: 2011-02-16
forum: Networking &amp; Wireless
---

### Post by klov on 2011-02-16
I am trying to enable wifi access on Ubuntu server , which i installed on an old Thinkpad.

lspci output includes :
 Network Controller : Intel Pro Wireless 2200BG(Calexico 2)and Ethernet controller Intel 82801DB pro/100 VE (MOB) enternet controller.

when I run iwlist scan .. i get all the available ESSIDs including my router.

I tried to follow all the instructions on this link for setting up wifi [https://help.ubuntu.com/community/WifiDocs/WiFiHowTo](https://help.ubuntu.com/community/WifiDocs/WiFiHowTo) . 

iwconfig results are

lo     no wireless extensions
eth0   no wireless extensions
irda0  no wireless extensions
eth1   unassociated ESSID:"MySSID"
       Mode: Managed Frequency=2.42 GHz Access Point: Not-Associated Bit Rate=0 kb/s Tx-Power=20 dBm Sensitivity=8/0
Retry limit:7 RTS thr:off Fragment thr:off Power Management:pff Link Quality:0 Signal level:0 Noise level:0 Rx invalid nwid:0 Rx invalid crypt:0 rx invalid frag:0 Tx excessive retries:0 Invalid misc:0 Missed beacon:0

network interfaces available:
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp
wireless-essid MySSID
wireless-key XXXXXXXXXX
wireless-mode managed
wireless-channel 11

On restarting network .. I get the same message 
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
-------
-------
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 12
No DHCPOFFERS received
No working leases in persistant database - sleeping

I am still unable to ping my router
I installed wireless-tools, network-manager , DHCP3 server and updated the system. Still no access to internet.

Also the wifi light on the machine blinks, which I guess means the driver is correctly installed. 
Any help would be appreciated. 
regards
Klov

---

