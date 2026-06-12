---
title: "Wlan0 cannot connect to static Access Point"
date: 2012-09-26
forum: Networking &amp; Wireless
---

### Post by Lieyza on 2012-09-26
Hi,

I want to connect my wireless device which is wlan0 to an static access point. How can i configure my laptop?

I used Linux UBUNTU 10.04 LTS, and my access point (AP) is cisco aironet  1200 series. I configure my AP to be in static mode (do not connect to internet access, just for test-bed testing) with it i configure  the IP address to be '192.168.13.200' (masquerading mode) and the essid  name is 'mimos1'. When i run the command :

> sudo iwlist scanning                      i got some access point listed including AP (mimos1). Here shows the scanning part :

> Cell 02 - Address: 00:1D:45:AE:E9:30
                    Channel:8
                    Frequency:2.447 GHz (Channel 8)
                    Quality=70/70  Signal level=-25 dBm  
                    Encryption key[IMG]https://lqo-thequestionsnetw.netdna-ssl.com/questions/images/smilies/redface.gif[/IMG]ff
                    ESSID:"mimos1"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000002fcdcb1cd
                    Extra: Last beacon: 4988ms ago
                    IE: Unknown: 00066D696D6F7331
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 030108                      


It shows that my AP (mimos1) exist. 

Problem :

Scenario 1 : I used MN device with Window 7 system and try to connect to  the AP (mimos1). It connected as well as it get IPv6 address from this  AP which forwarded from MAG1. The IPv6 address of my MN that used window  7 system is 2001:100:6:5000:214:6cff:fe53:180a (as shows in the figure  as well). So i can assume that, there is no problem with the AP right??  Am i right?

Scenario 2 : I used MN device with ubuntu 10.04 LTS and try to connect  to the AP (mimos1) exactly same with scenario 1. After I scan, I can see that there is 'mimos1'. When I finish scan, I just click my  network manager icon and click for 'mimos1' (here, at network manager  icon, i see only one 'mimos1' listed). So when i click to connect, wlan0 will be  loading for awhile to try to be connected, but than, it drop the  connection.

How i can configure my laptop to connect to AP (mimos1) even though it  in static mode or in other name, the AP doesnt have internet access on  it, just static IP.

Another problem, when I do iwlist scanning, some AP shows that their essid name doest not match with their MAC address. Is this invited to my problem above?

Please help me

:-(


Lieyza

---

