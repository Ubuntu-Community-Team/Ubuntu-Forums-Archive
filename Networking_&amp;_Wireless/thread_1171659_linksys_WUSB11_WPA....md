---
title: "linksys WUSB11 WPA..."
date: 2009-05-27
forum: Networking &amp; Wireless
---

### Post by MJBoa on 2009-05-27
I have an old, cool and quiet machine that I want to use to control my newer, hotter and louder machine through VNC. My problem is that I only have a WUSB11 to connect it to the network, I do have a connection to the machine at the moment with ip masquerading/ICS through my new computer. But I need it untethered.
So I installed Ubuntu minimal cd to the old machine. Now I have to figure out how to get my WUSB11 to connect to my WPA network. When I do iwlist wlan0 scan it picks it up but says only:

wlan0     Scan completed :
          Cell 01 - Address: mac
                    ESSID:"name"
                    Mode:Master
                    Channel:6
                    Encryption key:on
                    Signal level=97/100  
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s

as opposed to, on my new machine with a connection to the network:

wlan0     Scan completed :
          Cell 01 - Address: mac
                    ESSID:"name"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=51/100  Signal level:-65 dBm  
                    Encryption key:on
                    IE: Unknown: num
                    IE: Unknown: num
                    IE: Unknown: num
                    IE: Unknown: num
                    IE: Unknown: num
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: num
                    IE: Unknown: num
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: num

Now this would seem to tell me that I can't use WPA with this card, being that it looks unable to detect WPA at all, but I've read threads that tell me I can. Some say I need the newest linksys firmware.
Now what can I do to get this working? Should I switch to ndiswrapper?
Remember this is being done all through the command line, no GUI bs. No desktop environments installed just X. Thanks in advance.

---

