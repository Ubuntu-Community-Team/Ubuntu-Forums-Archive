---
title: "No Network connection in KDE"
date: 2009-05-31
forum: Networking &amp; Wireless
---

### Post by kevein on 2009-05-31
Hi every body,
 
I have upgraded my system from ubuntu to Kubuntu and installed KDE but I got a problem that I can't access Internet because the icon of network connection disappeared, but It's visisble in Gnome and no problem, so I can access to Internet easily using 3com usb wireless.

Can any body help me in this.
Thanks.

---

### Post by superprash2003 on 2009-05-31
post output of the following from the terminal
1)iwconfig
2)sudo iwlist scanning

---

### Post by kevein on 2009-06-01
I have did what you you advice me to do and I got this:

     user@user-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"ALFAWZ"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:1B:2F:46:6B:C4   
          Bit Rate=6 Mb/s   Tx-Power=20 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=68/100  Signal level:-41 dBm  Noise level=-85 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

user@user-desktop:~$ sudo iwlist scanning
[sudo] password for jalal: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:1B:2F:46:6B:C4
                    ESSID:"ALFAWZ"
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=71/100  Signal level:-40 dBm  Noise level=-86 dBm
                    Encryption key:on
                    IE: Unknown: 0006414C4641575A
                    IE: Unknown: 010482848B96
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0104
                    IE: Unknown: 32080C1218243048606C
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=0000004ff0d35235
                    Extra: Last beacon: 56ms ago

pan0      Interface doesn't support scanning.

---

### Post by superprash2003 on 2009-06-01
you seem to be connected to ALFAWZ.. post output of ifconfig from the terminal

---

### Post by kevein on 2009-06-02
yes but i not getting network connection and there's no Internet connected with my machine

---

### Post by superprash2003 on 2009-06-03
ifconfig output?

---

### Post by vinutux on 2009-06-03
these solution are worked 4 me

1. press Alt+f1 

2. type nm-applet in "run application"

3. notice new applet intaskbar ----- configure and connect

................DONE........................:D

...............................nice 2 help U

---

