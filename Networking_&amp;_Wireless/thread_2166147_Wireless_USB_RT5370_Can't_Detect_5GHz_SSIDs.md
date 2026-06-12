---
title: "Wireless USB RT5370 Can't Detect 5GHz SSIDs"
date: 2013-08-07
forum: Networking &amp; Wireless
---

### Post by bell1996 on 2013-08-07
```
I went thru a few steps to get this far (well lots and lots of steps).

Here's my laptop setup:
Ubuntu 12.10 (64-Bit)
USB mini Dongle (RT5370)

I'm able to see the SSID's on the 2.4GHz spectrum but not the SSID's on the 5GHz spectrum. I bought a new Dlink Dual-Band AP and I am_ not _able to detect the new SSID (which I've called "dlink" to keep things simple). My really old AP is advertising two SSID's, which I can detect, but I'm sure it's only at 2.4GHz (talking 5-7 yr old AP). I can also connect to the SSID's on the 2.4GHz spectrum with no problem (it may be old but it works like a champ).

I've tried disabling wireless N functionality by adding "options iwlwifi 11n_disable=1" in the /etc/modprobe.d/iwlwifi.conf file. Still did not help.

I think this should be a pretty simple solution to this issue. 

Any suggestions would be greatly appreciated.

Here's some relevant output:

**lsusb**
Bus 002 Device 006: ID 148f:5370 Ralink Technology, Corp. RT5370 Wireless Adapter

**lsmod | grep rt**
rt5370sta             801444  1 
parport_pc             32689  0 
parport                46346  3 parport_pc,ppdev,lp

**iwconfig**
ra0       Ralink STA  ESSID:"11n-AP"  Nickname:"RT2870STA"
          Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=10/100  Signal level:0 dBm  Noise level:0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

**sudo iwlist ra0 scan**
ra0       Scan completed :
          Cell 01 - Address: 00:1F:B3:C1:D5:51
                    Protocol:802.11b/g
                    ESSID:"2WIRE101"
                    Mode:Managed
                    Frequency:2.432 GHz (Channel 5)
                    Quality=63/100  Signal level=-65 dBm  Noise level=-92 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: 00:21:59:3D:0B:60
                    Protocol:802.11b/g
                    ESSID:"SSG5"
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality=57/100  Signal level=-67 dBm  Noise level=-92 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
```

---

### Post by kurt18947 on 2013-08-08
It doesn't appear the RT5370 chip is dual frequency based on this MediaTek page:
[http://www.mediatek.com/_en/01_products/04_pro.php?sn=1007](http://www.mediatek.com/_en/01_products/04_pro.php?sn=1007)

> The RT5370 is a cost-effective, highly integrated USB Wi-Fi single chip  containing an 802.11n MAC and baseband, a 2.4 GHz RF, PA, LNA and T/R  switch on a single die. It supports a 150 Mbps PHY data rate and fully  complies with 802.11b/g/n specifications, providing feature-rich  wireless connectivity at

> 1T1R 2.4 GHz with 150 Mbps PHY data rate

Useful little adapter though, plug & play 12.10 and later, performs very well for me in 13.10,

---

### Post by bell1996 on 2013-08-08
Kurt18947, thanks for the reply. 

I did some more research and I believe you are correct. No wonder these mini/nano wireless USB's are so cheap. Only supports 2.4GHz. 

Again, thanks for the confirmation.

---

### Post by kurt18947 on 2013-08-08
> **bell1996 said:**
> Kurt18947, thanks for the reply. 

I did some more research and I believe you are correct. No wonder these mini/nano wireless USB's are so cheap. Only supports 2.4GHz. 

Again, thanks for the confirmation.

You're welcome.  Mine is fast enough for web browsing and moving modest sized (<500 Mb. or so) files to or from a router USB port based FTP server.  I guess too it depends on how much traffic & interference there is.  The only 2 chipsets I know of in the micro/nano sized USB wifi adapters are RTL8188CUS & Ralink/MediaTek RT5370.  They're both single frequency.  There is a fairly inexpensive USB adapter chipset - RTL8192SU - which I believe is supposed to handle 2 frequencies (2.4/5 ghz)  receive and 1 frequency(2.4) transmit.  I have a couple of those but haven't tried dual frequency yet.

---

### Post by wildmanne39 on 2013-08-08
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by bell1996 on 2013-08-11
Kurt18947, 

Just an FYI. I purchased the DLink DWA-171 Dual Band USB adapter ($54). It worked like a champ!! 
Just downloaded the driver, did a make install, and I was off and running. No problems. Now I can see all the SSID's (2.4 & 5 GHz) and connect to all the SSID's. Also, no issues with slow internet access. Great little adapter. I'll start a new post detailing the steps I used to get this working for the rest of the community.

---

### Post by kurt18947 on 2013-08-11
Good deal!  That might be the first dual freq adapter I've seen reported as working.  What chipset does it use?  It doesn't appear to be on wikidevi yet.

Edit:  I misspoke, I guess I used the wrong search term.  That looks like a *new* adapter/chipset.   
[http://wikidevi.com/wiki/D-Link_DWA-171_rev_A1](http://wikidevi.com/wiki/D-Link_DWA-171_rev_A1)
And Dlink has changed chip suppliers already :grin:.  A1 uses Realtek, B1 uses Mediatek/Ralink according to wikidevi.  Yes there appears to be no 'native' linux support as yet.  If D-link insists on being a moving target, it might be a while.

---

