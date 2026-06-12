---
title: "problem with connecting to internet with wireless modem."
date: 2009-06-18
forum: Networking &amp; Wireless
---

### Post by ninjapradeep on 2009-06-18
Hi...

I am trying to connect to my modem with wireless. But i am not able to connect it. I searched in some forums but no luck. 

I think my wireless adapter is getting the signal. when I do [FONT="System"]iwlist scan[/FONT] the fallowing appears.

root:~iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:1B: DA:49:E0:3B
                    ESSID:"UTStarcom"
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=82/100  Signal level:-52 dBm  Noise level=-127 dBm
                    Encryption key: off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=0000000344ab8183
                    Extra: Last beacon: 1576ms ago

ppp0      Interface doesn't support scanning.

pan0      Interface doesn't support scanning.


and when i do iwconfig the fallowing appears.

root:~iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=15 dBm   
          Retry min limit:7   RTS thr: off   Fragment thr=2352 B   
          Encryption key: off
          Power Management: off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

ppp0      no wireless extensions.

pan0      no wireless extensions.


From the above i think my laptop is recognizing the signal but not able to connect it.

and when i change the file /etc/NetworkManager/nm-system-settings.conf managed=true it recognizes the modem and i am able to connect to modem. but i am not able to connect to internet.Find me a solution. 

I want to know how this works. Suggest me some sites to learn about this.

---

### Post by papangul on 2009-06-18
You may try the alternative network manager wicd:
[http://ubuntuforums.org/showthread.php?t=1150797](http://ubuntuforums.org/showthread.php?t=1150797)

Sometimes, a bad DNS server is set as default,in that case you will get your routers admin page but not be able to browse the internet, if you suspect that - then set opendns as your DNS server:
[https://www.opendns.com/start/device/ubuntu](https://www.opendns.com/start/device/ubuntu)

---

