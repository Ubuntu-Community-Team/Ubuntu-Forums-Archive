---
title: "wireless help (desperate)"
date: 2010-02-05
forum: Networking &amp; Wireless
---

### Post by 26venger on 2010-02-05
heres my issue> i just bought a new alfa wireless usb. i plugged it in and it was plug and play. the problem is that my computer is right next to my wireless modem and network manager shows the signal strength as weak.

my essid is ** myquest 6323.**

code

slyco@slyco-desktop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: xx:xx:xx:xx
                  **  ESSID:"myqwest6323"**
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=23/100  Signal level:65/65  
                    Encryption key on
                    IE: Unknown: 000B6D79717765737436333233
                    IE: Unknown: 010482848B96
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32080C1218243048606C
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
IE: Unknown: DD7A0050F204104A0001101044000102103B00010310470010 8855DEDEE916BC8E2371F13AA7997212102100025449102300 064150444B3731102400043731303010420007313233343332 311054000800060050F20400011011001A416374696F6E7465 632052656769737472617220504B3530303010080002008C
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=000000710dcf2249
                    Extra: Last beacon: 80ms ago

pan0      Interface doesn't support scanning.

code

root@slyco-desktop:/home/slyco# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

my card also picks up signals a block away from me and they show up as the same signal strength as my broadband wireless highspeed modem

my wireless high speed modem uses wpa2 encryption
my wireless card supports wpa2
i have a realtek chipset

i dont know wat the problem is. maybe my wireless card needs to be modifyed so it is more sensitive. 

please reply i am in desperate need of help.:icon_frown:

---

