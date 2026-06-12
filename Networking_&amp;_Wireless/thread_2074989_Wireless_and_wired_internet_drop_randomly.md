---
title: "Wireless and wired internet drop randomly"
date: 2012-10-22
forum: Networking &amp; Wireless
---

### Post by ggranson91 on 2012-10-22
Hi,
I recently switched over to ubuntu 12.04 from windows 7. After the switch I downloaded Broadcom Wireless STA driver from a wired connection which gave me the ability to actually get on the internet. However, although I can get on the internet it continues to drop periodically saying "Server Not Found" and a simple refresh of the page fixes the problem. Although annoying I could deal with this. But I am heavy usenet user and this makes for not being able to download things as well as any packages from the software center. I've included some information if any additional information is need let me know 

@garrett:~$ lspci | grep -i net
03:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)

garrett@garrett:~$ iwconfig
lo        no wireless extensions.

eth2      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:213  Noise level:199
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

eth0      no wireless extensions.
(my internet was working during the above "iwconfig command)

---

### Post by ggranson91 on 2012-10-23
Just trying to get this moved back up. If anyone can help me at all with this problem it would be greatly greatly appreciated!!

---

### Post by chili555 on 2012-10-25
Are you using the STA driver? There is another way to get this working that may be more effective:```
lsmod | grep -e wl -e b43
```How is your signal strength?```
sudo iwlist eth2 scan
```

---

### Post by ggranson91 on 2012-10-29
Wired -

garrett@garrett:~$ lsmod | grep -e wl -e b43
wl                   2646601  0 
lib80211               14040  2 lib80211_crypt_tkip,wl
garrett@garrett:~$ sudo iwlist eth2 scan
[sudo] password for garrett: 
eth2      Failed to read scan data : Invalid argument

and

garrett@garrett:~$ lsmod | grep -e wl -e b43
wl                   2646601  0 
lib80211               14040  2 lib80211_crypt_tkip,wl
garrett@garrett:~$ sudo iwlist eth2 scan
[sudo] password for garrett: 
eth2      Failed to read scan data : Invalid argument

---

### Post by ggranson91 on 2012-10-29
Wired -

garrett@garrett:~$ lsmod | grep -e wl -e b43
wl                   2646601  0 
lib80211               14040  2 lib80211_crypt_tkip,wl

And

garrett@garrett:~$ sudo iwlist eth2 scan
eth2      Scan completed :
          Cell 01 - Address: 00:1D:D3:AF:3B:40
                    ESSID:"HOME-3B42"
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:5/5  Signal level:-34 dBm  Noise level:-92 dBm
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD7D0050F204104A0001101044000102103B000103104700102880288028801880A880001DD3AF3B4010210005415252495310230006544738363247102400065254323836301042000831323334353637381054000800060050F204000110110012415252495320544738363220526F75746572100800020084103C000101
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 12 Mb/s
                              24 Mb/s; 48 Mb/s
          Cell 02 - Address: B8:E6:25:DE:CF:D1
                    ESSID:"2WIRE185"
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:1/5  Signal level:-81 dBm  Noise level:-92 dBm
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
          Cell 03 - Address: 34:EF:44:43:3A:D1
                    ESSID:"Mywireless"
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:1/5  Signal level:-85 dBm  Noise level:-92 dBm
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s

---

### Post by ggranson91 on 2012-10-29
Thanks for the help chili. During wired I was getting about 3.1 MB's down and was still having an issue with it dropping in and out. With wireless I was getting virtually 0 down and still dropping what little connection I had.

---

### Post by chili555 on 2012-10-29
Let's see if we can try a different, possibly better driver. Hook up the ethernet and do:```
sudo apt-get remove --purge bcmwl-kernel-source
sudo apt-get install firmware-b43-lpphy-installer
```After it finishes, reboot with the ethernet detached and let us have your report.

---

### Post by ggranson91 on 2012-10-29
WIreless Connection (still dropping) -


Code: 

> garrett@garrett:~$ lsmod | grep -e wl -e b43
b43                   342643  0 
mac80211              436455  1 b43
cfg80211              178679  2 b43,mac80211
bcma                   25651  1 b43
ssb                    50691  1 b43


Code:

> garrett@garrett:~$ sudo iwlist eth2 scan
[sudo] password for garrett: 
eth2      Interface doesn't support scanning.

---

### Post by ggranson91 on 2012-10-29
I'm not sure how u post the little code boxes that u use. I apologize for being a rookie!

---

### Post by chili555 on 2012-10-29
I suspect your wireless interface is now wlan0 or wlan-something. Check:```
iwconfig
sudo iwlist wlan0 scan [COLOR="Red"]<--or whatever wlan you found[/COLOR]
```You can highlight text and then surround them with a code box using the # button at the top of the reply box. Please see attached.

---

### Post by ggranson91 on 2012-10-29
```
garrett@garrett:~$ iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"HOME-3B42"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:1D:D3:AF:3B:40   
          Bit Rate=54 Mb/s   Tx-Power=27 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-5 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:7   Missed beacon:0

eth0      no wireless extensions.

```

```
garrett@garrett:~$ sudo iwlist wlan0 scan
[sudo] password for garrett: 
wlan0     Scan completed :
          Cell 01 - Address: 00:1D:D3:AF:3B:40
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=-5 dBm  
                    Encryption key:on
                    ESSID:"HOME-3B42"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000006f9075a0b7
                    Extra: Last beacon: 60ms ago
                    IE: Unknown: 0009484F4D452D33423432
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0106
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1A0C0016FFFF0000000000000000000000000000000C0000000000
                    IE: Unknown: 3D1601000700000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B0501000C127A
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4307000000
                    IE: Unknown: 0706555320010B10
                    IE: Unknown: DD7D0050F204104A0001101044000102103B000103104700102880288028801880A880001DD3AF3B4010210005415252495310230006544738363247102400065254323836301042000831323334353637381054000800060050F204000110110012415252495320544738363220526F75746572100800020084103C000101
          Cell 02 - Address: B8:E6:25:DE:CF:D1
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"2WIRE185"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000c91a698801
                    Extra: Last beacon: 756ms ago
                    IE: Unknown: 00083257495245313835
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 030106
                    IE: Unknown: 0706555320010B1B
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
          Cell 03 - Address: 3C:EA:4F:A8:E1:B9
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:on
                    ESSID:"2WIRE548"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000033dd5cfb181
                    Extra: Last beacon: 244ms ago
                    IE: Unknown: 00083257495245353438
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010A
                    IE: Unknown: 050400010004
                    IE: Unknown: 0706555320010B1B
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
          Cell 04 - Address: 34:EF:44:43:3A:D1
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:on
                    ESSID:"Mywireless"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000b78beac64
                    Extra: Last beacon: 108ms ago
                    IE: Unknown: 000A4D79776972656C657373
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 03010B
                    IE: Unknown: 0706555320010B1B
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0102
                    IE: Unknown: 32043048606C




```

---

### Post by chili555 on 2012-10-29
> wlan0     IEEE 802.11bg  ESSID:"HOME-3B42"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:1D:D3:AF:3B:40   
          Bit Rate=54 Mb/s   Tx-Power=27 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70Looks pretty solid!> wlan0     Scan completed :
          Cell 01 - Address: 00:1D:D3:AF:3B:40
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=-5 dBm  
                    Encryption key:on
                    ESSID:"HOME-3B42"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    IE: [COLOR="Red"]WPA Version 1[/COLOR]
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: [COLOR="Red"]IEEE 802.11i/WPA2 Version 1[/COLOR]
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    I suspect you'll have better luck with WPA2 and not WPA/WPA2 mixed mode. Can you change the setting in the router?

---

### Post by ggranson91 on 2012-10-29
Yes I can change it in the router. I'm still having terrible connection issues though. Its making the internet unusable right now

---

### Post by ggranson91 on 2012-10-29
switched the router. Connection still terrible. This is becoming very frustrating lol

---

### Post by chili555 on 2012-10-29
> **ggranson91 said:**
> switched the router. Connection still terrible. This is becoming very frustrating lolOuch! I wonder if there are any clues here:```
dmesg | grep -e b43 -e ssb
sudo cat /var/log/syslog | grep etwork
```

---

### Post by ggranson91 on 2012-10-30
Sorry for the delay I have been really tied up. 

This repeated a ton of times:

```
garrett@garrett:~$ sudo cat /var/log/syslog | grep etwork
[sudo] password for garrett: 
Oct 30 05:00:38 garrett NetworkManager[955]: <warn> nl_recvmsgs() error: (-33) Dump inconsistency detected, interrupted
``` 

and 

```
garrett@garrett:~$ dmesg | grep -e ssb
[    6.176286] ssb: Core 0 found: ChipCommon (cc 0x800, rev 0x16, vendor 0x4243)
[    6.176305] ssb: Core 1 found: IEEE 802.11 (cc 0x812, rev 0x0F, vendor 0x4243)
[    6.176323] ssb: Core 2 found: PCMCIA (cc 0x80D, rev 0x0A, vendor 0x4243)
[    6.176341] ssb: Core 3 found: PCI-E (cc 0x820, rev 0x09, vendor 0x4243)
[    6.248243] ssb: Sonics Silicon Backplane found on PCI device 0000:03:00.0

```

Thanks again for your help I've been stuck with this for weeks now lol.

---

### Post by chili555 on 2012-10-31
> NetworkManager[955]: <warn> nl_recvmsgs() error: (-33) Dump inconsistency detected, interruptedA quick Google suggests this is a VPN issue. Is this the case with you? Are there some malformed VPN settings in NM? ```
sudo cat /var/log/syslog | grep -i VPN
```We might reinstall NM:```
sudo apt-get remove --purge network-manage*
sudo apt-get install network-manager
```I suspect it's an NM problem because it affects both wired and wireless.

---

### Post by ggranson91 on 2012-10-31
Thanks Chili. I'm at work right now but ill do your suggestions as soon as I get home. I'm not sure about the VPN but it's my understanding I dont have a VPN? I'm not sure what this means. We'll have to do your tests to find out what's going on. I feel like we're getting closer!

---

### Post by chili555 on 2012-10-31
> it's my understanding I dont have a VPN? I'm not sure what this means.Like many things in life, if you don't know what it means, you undoubtedly don't have it, but let's check your syslog for sure.

---

### Post by ggranson91 on 2012-10-31
I actually mispoke, I know what a VPN is but i haven't set one up so unless i accidentally did it then no I have no VPN.

---

### Post by gzh on 2012-10-31
I seem to have the same issue.
I recognized that the time, internet is available between the drop outs, depends on the data volume transfered. (At least in my case)
If I just open some pages with text on them the internet is stable for 'a while' but if I have bigger amounts of data transfered it only lasts for a couple of seconds. It's approximately around 8mb of data.

---

### Post by ggranson91 on 2012-11-01
Ya after doing the first command I now cannot complete the second command because I have no Internet.  I cannot get on the internet at all now. How do I fix this

---

### Post by chili555 on 2012-11-02
If you are hooked up with ethernet, simply do:```
sudo dhclient eth0
```Then proceed.

---

### Post by ggranson91 on 2012-11-05
This may have fixed it. Ill report back in a day or so after I've tested it. Thanks chili

---

