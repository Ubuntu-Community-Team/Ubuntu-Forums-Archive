---
title: "Natty 11.04 wireless problems with rt2860 drivers"
date: 2011-05-05
forum: Networking &amp; Wireless
---

### Post by samsankey on 2011-05-05
I know this is a common problem but this is the first time I haven't been able to fix it by searching the forums and googling so thought I'd try posting myself.  

Basically network manager can scan the networks and attempt to connect but times out without making a connection. The problem is with WPA encryption only as WEP and open networks work.  I figured from these outputs that the rt2860sta module is running and its not conflicted:

```
lsmod | grep rt2
rt2860sta         494649  1
crc_ccitt             12595  1 rt2860sta
``````
cat /etc/modules
lp
rt2860sta
rt2860sta
```I've tried blacklisting the other rt2 drivers but that hasn't worked.

Any help much appreciated

---

### Post by maggiemonic on 2011-05-08
Same problem here... any help would be very much appreciated.

---

### Post by samsankey on 2011-05-08
I realised there's not too much info here and found the sticky on what info should be included so here's most of it.  The desktop itself is a custom build made by a company called pcspecialist in the uk.  Anywhere where the info was not related to the wireless device but to something else i've put "..." to hopefully help make things clearer.  Unfortunately in the conversion of the txt file over to my XP partition some of the formatting has gone astray which i've tried to fix but some of the indents haven't made it and there may be more returns than I found:

```
sam@sam-desktop:~$ lspci | grep 'RT2'
0b:00.0 Network controller: Ralink corp. RT2760 Wireless 802.11n 1T/2R Cardbus

sam@sam-desktop:~$ ifconfig
...
wlan0     
Link encap:Ethernet  
HWaddr 00:1f:1f:3d:07:7a  
inet6 addr: fe80::21f:1fff:fe3d:77a/64 Scope:Link
UP BROADCAST MULTICAST  MTU:1500  Metric:1
RX packets:33242 errors:0 dropped:0 overruns:0 frame:0
TX packets:264 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000 
RX bytes:4903090 (4.9 MB)  TX bytes:4608 (4.6 KB)
Interrupt:16 

sam@sam-desktop:~$ iwconfig
...
wlan0     Ralink STA  ESSID:""  Nickname:"RT2860STA"          
Mode:Auto  Frequency=2.437 GHz  Access Point: 00:21:04:C1:95:32   
          Bit Rate=1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=94/100  Signal level:0 dBm  Noise level:-97 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sam@sam-desktop:~$ lsmod | grep 'rt2'
rt2860sta             494649  1 
crc_ccitt              12595  1 rt2860sta

sam@sam-desktop:~$ dmesg | grep 'rt2'
[   20.128650] rt2860sta: module is from the staging directory, the quality is unknown, you have been warned.
[   20.133164] rt2860 0000:0b:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   21.821228] <==== rt28xx_init, Status=0
[   21.888483] <==== rt28xx_init, Status=0
[   88.498088] <==== rt28xx_init, Status=0

sam@sam-desktop:~$ sudo lshw -C network
...
*-network       
description: Wireless interface
       product: RT2760 Wireless 802.11n 1T/2R Cardbus
       vendor: Ralink corp.
       physical id: 0
       bus info: pci@0000:0b:00.0
       logical name: wlan0
       version: 00
       serial: 00:1f:1f:3d:07:7a
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2860 latency=64 maxlatency=4 mingnt=2 multicast=yes wireless=Ralink STA
       resources: irq:16 memory:fbef0000-fbefffff

sam@sam-desktop:~$ iwlist scan
...
wlan0     Scan completed :        
...
Cell 05 - Address: 00:21:04:C1:95:32
                    Protocol:802.11b/g/n
                    ESSID:"BTHomeHub2-C8KP"
                    Mode:Managed
                    Channel:6
                    Quality:100/100  Signal level:-48 dBm  Noise level:-97 dBm
                    Encryption key:on
                    Bit Rates:18 Mb/s
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          
sam@sam-desktop:~$ lsb_release -d
Description:    Ubuntu 11.04

sam@sam-desktop:~$ uname -mr
2.6.38-9-generic i686

sam@sam-desktop:~$ sudo /etc/init.d/networking restart
* Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
* Reconfiguring network interfaces...                                   [ OK ] 

sam@sam-desktop:~$ 

```

---

### Post by rhysa42 on 2011-05-11
I am also experiencing same issue

---

### Post by chili555 on 2011-05-11
> ell 05 - Address: 00:21:04:C1:95:32
                    Protocol:802.11b/g/n
                    ESSID:"BTHomeHub2-C8KP"
                    Mode:Managed
                    Channel:6
                    Quality:100/100  Signal level:-48 dBm  Noise level:-97 dBm
                    Encryption key:on
                    Bit Rates:18 Mb/s
                    IE: [COLOR="Red"]WPA Version 1[/COLOR]
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/[COLOR="Red"]WPA2 Version 1[/COLOR]
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSKI don't know whether it's wpa_supplicant, Network Manager or the driver, but mixed WPA and WPA2 mode is troublesome. If this is your router, I suggest trying either WPA or WPA2; not mixed mode. Please post back so we all can learn from your experience.

---

### Post by samsankey on 2011-05-12
It didn't work with either of the single encryptions and the dmesg result is the same.  It may just be the driver doesn't work though I would hope not because the computer's almost 2 years old.

---

### Post by samsankey on 2011-05-13
I've managed to fix it - apparently there was a BTHomeHub2 firmware update which completely screwed the routers connection to dual boot machines as the router thought it had already given the ip address that was being requested away to, in my case, windows xp and hence couldn't give the address to ubuntu.  The fix was to set a static IP up.  Needless to say I'm not happy with BT especially after earlier this year we had two weeks at internet speeds of 50kb/s because the line was broken and they just bounced us between the phone side of the company and the broadband side for ages blaming each other for the problem.  Rant over.

More details can be found [here]("http://community.bt.com/t5/BB-Speed-.../176473/page/9")

EDIT: unfortunately I spoke too soon - I have local network connection but not internet though I think this is a problem with my manual network settings.

EDIT2: as expected is was the network settings - all is well now

---

### Post by sgerrand on 2011-05-17
i would recommend blacklisting modules that aren't required for the rt2860 nic. adding the following to **/etc/modprobe.d/blacklist.conf** was enough for me:
```

blacklist rt2800pci
blacklist rt2x00pci

```

this was enough to get my wlan interface back to normal - i.e. it now resumes from sleep/connection interruptions and has no issue connecting to networks with different encryption (wep/wpa/etc). 

no issues with 'mixed mode' wpa networks either (wpa/wpa2 and aes/tkip). :)

hope that helps!

---

### Post by hma.istsupport on 2011-06-25
seems like you people can help me since by now you have tried a lot of r and d. Thank you.

I just upgraded from 10.x to 11.04. Everything is working fine except the wi-fi. I am not able to connect to any of my friends computers nor they can connect me. When I create a wireless network, they can see the network, but its strength is 0. When they create, I can see the network, I select, give the password and wait..but nothing turns out.

any help will be appreciated.

---

