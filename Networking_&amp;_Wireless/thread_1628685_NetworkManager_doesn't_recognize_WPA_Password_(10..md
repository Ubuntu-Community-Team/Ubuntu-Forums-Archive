---
title: "NetworkManager doesn't recognize WPA Password (10.04)"
date: 2010-11-23
forum: Networking &amp; Wireless
---

### Post by teknosalsero on 2010-11-23
Hi all,

I'm stumped and can use some help.  Here are some facts and some output.  Any help would be greatly appreciated.

[LIST]
[*]I have a Netgear MA101 Rev. B that I'd like to get working on my Ubuntu 10.04 machine
[*]I've installed the at76 usb drivers and can see local wireless networks using both "iwlist scan" and NetworkManager
[*]I have a hidden SSID that I'm using w/ WPA encryption
[*]The problem: Everytime I enter my password correctly (ASCII text) using NetworkManager, my PC thinks for a bit and then asks for it again
[/LIST]  

Some terminal outputs:
> desenna@desenna-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11b  ESSID:"MDS"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
desenna@desenna-desktop:~$ sudo iwlist scan
[sudo] password for desenna: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
...
          Cell 02 - Address: 00:22:6B:99:80:30
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=24/100  Signal level=24/100  
                    Encryption key:on
                    ESSID:"MDS"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000001c3f897183
                    Extra: Last beacon: 328ms ago
                    IE: Unknown: 00034D4453
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030102
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A1E181AFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1602051700000000000000000000000000000000000000
                    IE: Unknown: 7F0101
                    IE: Unknown: DD720050F204104A0001101044000102103B0001031047001000226B99802E00226B99802E0400E8001021000C4C696E6B73797320496E632E102300075752543136304E1024000876312E30312E3232104200033030301054000800060050F2040001101100075752543136304E100800020088
                    IE: Unknown: DD090010180204F4010000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C331E181AFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3402051700000000000000000000000000000000000000

...



Anything else I can provide?

Mike

---

### Post by twodogsdad on 2010-12-08
Hello Mike,
I'm having a similar problem. Have you received any response or figured out the solution?

Thanks,
Cal

---

