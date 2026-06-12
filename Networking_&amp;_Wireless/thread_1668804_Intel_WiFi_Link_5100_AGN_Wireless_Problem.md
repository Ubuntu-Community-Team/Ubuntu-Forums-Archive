---
title: "Intel WiFi Link 5100 AGN Wireless Problem"
date: 2011-01-16
forum: Networking &amp; Wireless
---

### Post by jgreer on 2011-01-16
Hello,

I am running Ubuntu 10.10 and am pretty new  so I apologize if I am missing something obvious, but I've searched for a solution for quite a while now and am stumped.  I have an Intel WiFi Link 5100 AGN wireless card and the drivers appear to be installed correctly, but the card is not working (not picking up any wireless networks in the main Wireless menu of the taskbar.  It just says "Wireless disabled").       

Anyway, all the sorts of diagnostic tests I have seen in the forums seem normal, so I'm not sure if it's just some weird activation problem (already tried 'sudo ifconfig wlan0 up').   Also, "iwlist scan" shows that the wireless is picking up vallid networks.  I just can't connect, and the information is not showing up in any "GUI related" networking tool like I would expect.

Here is all the relevant diagnostic information:  
> 
lspci | grep Network 

03:00.0 Network controller: Intel Corporation PRO/Wireless 5100 AGN [Shiloh] Network Connection
> 
iwconfig

wlan0     IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
> 
dmesg | grep iwlagn

[   17.359780] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[   17.359784] iwlagn: Copyright(c) 2003-2010 Intel Corporation
[   17.359890] iwlagn 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   17.359920] iwlagn 0000:03:00.0: setting latency timer to 64
[   17.360003] iwlagn 0000:03:00.0: Detected Intel(R) WiFi Link 5100 AGN, REV=0x54
[   17.394021] iwlagn 0000:03:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[   17.394135] iwlagn 0000:03:00.0: irq 46 for MSI/MSI-X
[   17.433943] iwlagn 0000:03:00.0: loaded firmware version 8.24.2.12
iwlist scan is returning what looks to be a valid list of networks, but I'll save the space and only show the information about the network I am trying to join.
> 
iwlist scan

          Cell 03 - Address: 00:23:69:D0:DF:98
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=-27 dBm  
                    Encryption key:on
                    ESSID:"JJGW"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000000a577b7d6
                    Extra: Last beacon: 3208ms ago
                    IE: Unknown: 00044A4A4757
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
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
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010002004000
                    IE: Unknown: DD740050F204104A0001101044000102103B0001031047001000000000000010000000002369D0DF981021000C4C696E6B73797320496E632E10230007575254353447321024000776312E352E303010420001301054000800060050F20400011011000757525435344732100800020084103C000103
> 
uname -mr

2.6.35-24-generic i686
> 
 sudo /etc/init.d/networking restart

 * Reconfiguring network interfaces...                                          Ignoring unknown interface eth0=eth0.
                                                                         [ OK ]

I was trying to connect via the command-line so I tried:
> 
iwconfig wlan0 essid JJGW
but then setting the key didn't work by calling:
> 
iwconfig wlan0 key s:*****

Error for wireless request "Set Encode" (8B2A) :
    SET failed on device wlan0 ; Invalid argument.
which is weird because this is how the man page says to do it.  Thanks for the help.  Hope this is not information overload.

Joey

EDIT:  Forgot to post wlan0 message in the log, which may be important

> 
dmesg | grep wlan0

[   18.809066] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  888.777388] ADDRCONF(NETDEV_UP): wlan0: link is not ready


---

### Post by postenga on 2011-01-18
i got the same problem man!

---

### Post by eslam on 2011-02-03
almost the same problem 
any suggestions 

thanks in advance

---

### Post by ugm6hr on 2011-02-05
Uncertain, but perhaps look here:
[http://art.ubuntuforums.org/showthread.php?t=1672582](http://art.ubuntuforums.org/showthread.php?t=1672582)

---

### Post by eduardoconto on 2011-02-07
I have a similar problem with my Dell Vostro 1320. My *rfkill list all *output:
```

0: dell-wifi: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes

```
Apparently, there is no Fn+Fx key to enable/disable the modem. There is a switch to the it on/off that is on the on position. 
Any help is appreciated. Thank you.

EDIT: Working with the suggestion of removing the dell-laptop module on [http://art.ubuntuforums.org/showthread.php?t=1672582](http://art.ubuntuforums.org/showthread.php?t=1672582) have solved my problem, even though I had a software block too.
[URL="http://art.ubuntuforums.org/showthread.php?t=1672582"]
[/URL]

---

### Post by teddybairs1 on 2011-02-26
This might be a dumb question, but is the wireless enabled in the BIOS? I had that problem running a newly installed wifi card under Debian squeeze. It showed that everything worked, except it kept telling me that the wireless was disabled. It later dawned on me that I had disabled it in the BIOS a couple of years ago when the original wifi card quit working on me. I went into the BIOS and enabled it and everything worked fine. It was a rookie thing to do, but there you go.

---

### Post by wildmanne39 on 2012-07-07
Old thread closed.

---

