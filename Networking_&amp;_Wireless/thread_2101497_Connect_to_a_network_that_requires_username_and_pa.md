---
title: "Connect to a network that requires username and password from command line"
date: 2013-01-04
forum: Networking &amp; Wireless
---

### Post by rahulht on 2013-01-04
Hi,

I wish to connect to a N/W from my project board. I have installed ubuntu server 10.0.04 on it. It does not have a GUI(which is not needed for me too). Now, I wish to connect to my campus N/W which I know demands username and password from any desktop machine.
I used the following commands :
--ifconfig wlan0 up
--iwconfig
--iwlist scan

After the scan command, I can see the networks that I can connect to, but i am not able to connect to my campus network.
The output after the scan command is :
Cell 06 - Address 5C:50:15:F7:39:20
          Channel:1
          Frequency:2.412
          Encryption key:off
          ESSID:"xxx"
          Bit Rates: .....
          Mode: Master
          Extra:tsf=000000038a6ba0e4
          Extra: Last beacon: 3388ms ago
          IE: Unknown: 0003617375
          .
          .
          .

So, I tried the command : 
iwconfig wlan0 essid xxx
I don't get any messgaes on screen.

next command :
dhclient wlan0

I just recieve the messages like :

DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 17
.
.
.

No DHCPOFFERS received.

Any help in this situation to connect to the network will be highly appreciated.
 
Thank you !

---

### Post by Rocklobster690 on 2013-01-05
WiFiHowTo - [https://help.ubuntu.com/community/WifiDocs/WiFiHowTo](https://help.ubuntu.com/community/WifiDocs/WiFiHowTo)

WifiDocs/WirelessPCMCIATroubleshooting - [https://help.ubuntu.com/community/WifiDocs/WirelessPCMCIATroubleshooting?action=show&redirect=WifiDocs%2FWiFiTroubleshooting](https://help.ubuntu.com/community/WifiDocs/WirelessPCMCIATroubleshooting?action=show&redirect=WifiDocs%2FWiFiTroubleshooting)

WirelessTroubleshootingProcedure - [https://help.ubuntu.com/community/WirelessTroubleshootingProcedure](https://help.ubuntu.com/community/WirelessTroubleshootingProcedure)

---

