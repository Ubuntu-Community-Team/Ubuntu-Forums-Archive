---
title: "Lost Wifi after upgrading to 11.04,MSI U135"
date: 2011-05-01
forum: Networking &amp; Wireless
---

### Post by per engberg on 2011-05-01
I can see my network but when trying to connect after a while I get a pop-up asking "authentication required...". If I re-enter the password the same thing happens again. The network worked fine before upgrading to 11.04 and still works on other equipment.
The network LED can be switched on/off by pressing Fn-F11, but this does not help. Disabling and re-enabling the wireless does not help.
The network card is a Ralink RT3090, the PC a MSI U135

ifconfig shows:
wlan0     Link encap:Ethernet  HWaddr 40:61:86:42:f5:84  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:6 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:522 (522.0 B)  TX bytes:2098 (2.0 KB)
 
And iwconfig shows:

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"Milbak"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on


any help would be appreciated, I'd like not to have to re-install 10.10.

---

### Post by per engberg on 2011-05-01
Update: I got it working by adding the following line to  /etc/modprobe.d/blaclist.conf

blacklist rt2800pci

and restarted. Had me sweating there for a while...:D

---

### Post by pSYcl0Ne on 2011-05-08
im having this exact same problem with msi wind u100+ live cd works fine. i reinstalled 10.10 and that was fine. i quad boot and both win7 and snow leopard work fine but funnily enough after a recent update of linux mint debian edition that started droping out too. im going to try your fix now. thanks for posting



**edit*** I just wanted to add: The above paragraph was sent via my ipod, and I am now back online after editing /etc/modprobe.d/blacklist.conf like your suggestion. 

Eureka! Cheers mate!

---

