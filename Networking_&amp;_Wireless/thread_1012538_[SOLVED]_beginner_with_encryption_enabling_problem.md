---
title: "[SOLVED] beginner with encryption enabling problem"
date: 2008-12-15
forum: Networking &amp; Wireless
---

### Post by encryption trouble on 2008-12-15
Hi there, 

I recently bought a usb wireless thingy (D-link dwa-110), and at first it did not recognize it, so I went through a few threads and got it recognized using ndiswrapper, but now the problem is that it doesn't connect to the network. When I try to connect using Wicd I get "This network requires encryption to be enabled".

iwconfig gives this:
>  iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=11 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.



and a scan does this:
> sudo iwlist wlan0 scan

wlan0     Scan completed :
          Cell 01 - Address: 00:09:5B:CA:58:AC
                    ESSID:"NETGEAR"
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=51/100  Signal level:-50 dBm  
                    Encryption key:on
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Extra:tsf=00000041806ffbeb
                    Extra: Last beacon: 88ms ago


I guess I just have to enable the right encryption somewhere in wicd but I dunno where...Can anyone help me out? 
Thanks !!

---

### Post by encryption trouble on 2008-12-17
Ok, I eventually figured it out, I just had to get into the advanced settings of wicd, in the scroll down menu that I somehow didn't see before...

---

### Post by myfigurefemale on 2009-01-09
how did you get to the advanced settings?  i have all the same things come up for me in terminal but can't seem to change anything in wicd to make it work

---

### Post by rjohns08 on 2009-01-18
The Advanced settings are configured per wireless connection. Click on the drop down button next to the name of the network that you are trying to connect to and there you will find the advanced settings button.

Hope this helps.

---

