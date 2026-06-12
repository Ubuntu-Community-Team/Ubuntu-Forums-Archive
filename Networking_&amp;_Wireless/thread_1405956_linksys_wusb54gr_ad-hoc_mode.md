---
title: "linksys wusb54gr ad-hoc mode"
date: 2010-02-13
forum: Networking &amp; Wireless
---

### Post by rabijaved on 2010-02-13
i am trying to create an ad-hoc network using a wusb54gr adapter which uses the pre installed rt73usb driver .
i used the following to create the network
sudo ifconfig wlan2 down
sudo iwconfig wlan2 mode ad-hoc
sudo iwconfig wlan2 channel 4
sudo iwconfig wlan2 essid "linksys"
sudo ifconfig wlan2 up
sudo ifconfig wlan2 169.254.0.1

initially the essid is set to "linksys" .then after every 5 sec it keeps on changing to random values . the essid field does not show when i do iwconfig after that. although i can see it when i do
sudo iwlist wlan2 scan . it shows up something like this:

 ESSID:"h*(&#65533;&#65533;:9&#65533;&#660;\&#65533;y^&#65533;&#65533;&#65533;&#65533;W&#65533;&#65533;&#65533;i&#65533;/&#65533;"
after 5 sec
 ESSID:"&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;Zl&#65533;t&#65533;&#65533;k?&#65533;keyZ&#65533;<h&#65533;&#65533;0&#65533;9`&#65533;"

and so on
the ad-hoc network does form and i am able to ping the individual ip addresses but essid keeps changing. iwspy and iwpriv commands do not work and i get an error like this
wlan2     Interface doesn't support wireless statistic collection

wlan2     no private ioctls.

does anyone have a solution ?

below is the trace of the commands

iwconfig wlan2

wlan2     IEEE 802.11bg  ESSID:"rabi"  
          Mode:Ad-Hoc  Frequency:2.427 GHz  Cell: Not-Associated   
          Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr off   Fragment thr off
          Encryption key off
          Power Management off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

iwconfig wlan2 

wlan2     IEEE 802.11bg  Mode:Ad-Hoc  Frequency:2.427 GHz  
          Cell: Not-Associated   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr off   Fragment thr off
          Encryption key off
          Power Management off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

iwlist wlan2 scan

  Cell 03 - Address: B6:47:66:B7:4D:FF
                    Channel:4
                    Frequency:2.427 GHz (Channel 4)
                    Quality=70/70  Signal level=0 dBm  
                    Encryption key off
                    ESSID:"&#65533;
                            &#65533;&#65533;&#65533;&#65533;@b&#65533;&#65533;&#65533;.&#65533;&#65533;v&#1783;TO:&#1456;$"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Ad-Hoc
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 5424ms ago
                    IE: Unknown: 0020CA0CE4CE028DA94062F593FF42082EC9DB7605DBB7544F3AD6B02400DA6E1EA5
                    IE: Unknown: 010882840B160C121824
                    IE: Unknown: 030104
                    IE: Unknown: 06020000
                    IE: Unknown: 32043048606C

---

### Post by rabijaved on 2010-02-13
...

---

### Post by rabijaved on 2010-02-13
...

---

### Post by cariboo on 2010-02-13
Please don't create multiple threads on the same subject, I have merged your three threads.

---

### Post by rabijaved on 2010-02-14
sorry internet problem .... do you know anyway i can solve this problem ?

---

