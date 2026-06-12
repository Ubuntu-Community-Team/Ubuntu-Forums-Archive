---
title: "total newbie! wireless card found, driver loaded, not able to connect"
date: 2012-04-22
forum: Networking &amp; Wireless
---

### Post by ruthi13 on 2012-04-22
Hi! I'm a complete newbie, just switched over from Windows XP to Ubuntu 11.10 and not missing it at all apart from the fact that I can't connect to my wireless network so am accessing this from my phone, which can connect. I've followed Ubuntu help and found that I've got a Ralink wireless card which is detected. It's got a driver assigned to it, but no access point is identified. 

When I click on the wireless symbol in top right of top toolbar, available networks are shown, I just can't connect to my usual one, and no connection is established when I ping my router's ip address.

My only way of accessing the internet at the.mo until work next week is on this phone so I can't easily copy AMD paste huge swathes of command output, but could tell you what a certain line says if needed. Sorry I'm such a newb at the moment! 
Thanks, 

Ruth

---

### Post by chili555 on 2012-04-22
Welcome to the fun world of Ubuntu! Please open a terminal and run this command:```
sudo lshw -C network
```Included in the information about your Realtek card is *driver=*rtlsomething. Please tell us what it is.

Next run:```
sudo iwlist wlan0 scan
```Does your usual network show as WPA and WPA2 mixed mode? Some wireless drivers have trouble with this. Can you change your router to WPA2 only and try again?

Here is an example of WPA2 only:> wlan0     Scan completed :
          Cell 01 - Address: xx:13:10:62:8D:xx
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=68/70  Signal level=-42 dBm  
                    Encryption key:on
                    ESSID:"GBR1"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000019eae14cfcf
                    Extra: Last beacon: 12ms ago
                    IE: Unknown: 000447425231
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/[COLOR="Red"]WPA2 Version 1[/COLOR]
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK


Finally, what happens when you try to connect? Are you asked for the WPA2 password?

---

### Post by ruthi13 on 2012-04-22
Aww, thanks for your help! I ended up trying the wireless key rather than the password, and it connected fine! So all sorted, but thanks for the welcome and swift reply :-)

---

