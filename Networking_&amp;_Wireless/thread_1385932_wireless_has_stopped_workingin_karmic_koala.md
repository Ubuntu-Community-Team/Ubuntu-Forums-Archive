---
title: "wireless has stopped workingin karmic koala"
date: 2010-01-20
forum: Networking &amp; Wireless
---

### Post by claracc on 2010-01-20
Today my wireless has stopped working. 

I have a laptop hp6720s with network controller: Intel corporation PRO/Wireless 3945 ABG [Golan] Network connection (rev 02), dual boot vista/ubuntu 9.10, fully updated (kernel 2.6.31-17). I use a router edimax BR-6204 wg to use the net with other laptop.

Till now i have using wicd for controll wireless without any problem, internet was quick and responsive. (Quick connection without any failure).

But today the internet was very slow and wireless starts to connect and disconnects intermitently, doing it unusable. This was what occured when i upgraded from jaunty to karmic and used the network manager from gnome, but then i fix the problem installing wicd.

Now wicd behaves in the same way as gnome-network-manager.

If i connect directly the computer to the router by wire, i have internet and everything works perfectly.

How i can fix the wireless?. How i can do it works with ubuntu 9.10 and?.

Thanks in advance.

---

### Post by claracc on 2010-01-21
Bump...?

I add more information.

I have done an iwlist scanning and i obtain:

clara@clara1:/var/log/wicd$ iwlist scanning
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:1F:1F:04:AB:41
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=61/70  Signal level=-49 dBm  
                    Encryption key:on
                    ESSID:"WIRELESS_SANTANDER"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000006a7121d6c
                    Extra: Last beacon: 38988ms ago
                    IE: Unknown: 0012574952454C4553535F53414E54414E444552
                    IE: Unknown: 010882840B160C121824
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD0700E04C01020300

clara@clara1:/var/log/wicd$ 

What does it mean IE: Unknown?. Could be there the problem?.

If I run iwconfig, i obtain:

clara@clara1:/var/log/wicd$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:"WIRELESS_SANTANDER"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:1F:1F:04:AB:41   
          Bit Rate=11 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-35 dBm  Noise level=-127 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

clara@clara1:/var/log/wicd$ 

Please, could someone help?

---

