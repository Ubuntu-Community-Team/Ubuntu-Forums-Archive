---
title: "dissociating by local choice reason = 3"
date: 2010-04-25
forum: Networking &amp; Wireless
---

### Post by AKG_8 on 2010-04-25
I am having the problem of intermittent wireless connectivity

When I run this comman:
dmesg | grep wlan

Results:

[   19.209113] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   48.657772] wlan0: authenticate with AP 00:22:3f:96:ff:06
[   48.662285] wlan0: authenticated
[   48.662292] wlan0: associate with AP 00:22:3f:96:ff:06
[   48.665382] wlan0: RX AssocResp from 00:22:3f:96:ff:06 (capab=0x421 status=0 aid=2)
[   48.665386] wlan0: associated
[   48.668147] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   59.624110] wlan0: no IPv6 routers present
[   93.811134] wlan0: [COLOR=Red]disassociating by local choice (reason=3)[/COLOR]
[  104.928988] wlan0: authenticate with AP 00:22:3f:96:ff:06
[  104.941268] wlan0: authenticated
[  104.941275] wlan0: associate with AP 00:22:3f:96:ff:06
[  104.951383] wlan0: RX AssocResp from 00:22:3f:96:ff:06 (capab=0x421 status=0 aid=2)
[  104.951389] wlan0: associated
[  150.812186] wlan0: d[COLOR=Red]isassociating by local choice (reason=3)
[/COLOR]
Did some search and found it mean Radio kill switch = ON .. and that might be the problem .. the Radio kill switch should be OFF .. 

Please advise how to fix it ... I have tried both wicd and network manager and updated the drivers .. the wired connection works just fine ..

Thanks

AG

---

### Post by kindred7 on 2010-04-26
Hi AKG, Had to hunt down ur other topic lol

Well i searched for your wifi card and it seems there is a bug specific to your card and wpa:
[http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg1088844.html](http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg1088844.html) 

My advice is to modify some of the settings on your router. I am unsure if you are using enterprise or personal but, try the following:
WPA Personal, AES. or WPA Enterprise AES
WPA2, any setting, AES
or go back to the dreaded WEP

let us know if that works.

EDIT:
Try this as well [http://www.jpdw.org/blog/intel-wireless-broken-ubuntu-904](http://www.jpdw.org/blog/intel-wireless-broken-ubuntu-904)

---

### Post by AKG_8 on 2010-04-26
Hi Kindred ..

thanks so much for your reply

right now I am using the network without any password .. just because of fear of all these problems with encryption ..

Please advise

AkG

---

### Post by kindred7 on 2010-04-26
Well since it connects without encryption we are safe to say the problem is rly the wpa. Have you attempted to use any of the other encryptions i listed?

---

### Post by AKG_8 on 2010-04-26
actually I meant .. I have only tried so far using wireless without encryption .. and having all these problems using that ... never got so far as to use any encryption .. I would be very happy to just to get this unencrypted network running ..

---

### Post by kindred7 on 2010-04-26
alright this makes things a lot harder. have u tried the link i placed in my edit [http://www.jpdw.org/blog/intel-wireless-broken-ubuntu-904](http://www.jpdw.org/blog/intel-wireless-broken-ubuntu-904) ?

---

### Post by AKG_8 on 2010-04-27
Hi kindred

I tried those command in the link you posted

but this command (i have iwl3945 driver installed in my laptop)
sudo modprobe iwl3945 11n_disable=1 11n_disable50=1

it gave me this error
FATAL: Error inserting iwl3945 (/lib/modules/2.6.31-20-generic/kernel/drivers/net/wireless/iwlwifi/iwl3945.ko): Unknown symbol in module, or unknown parameter (see dmesg)

I have read some things about using ndiswrapper to access internet .. do you have any idea how to install it and use it ??

---

### Post by kindred7 on 2010-04-27
the driver for ndiswrapper is here [http://sourceforge.net/projects/ndiswrapper/](http://sourceforge.net/projects/ndiswrapper/)

the how to is here as well, [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

heres a tutorial video, [http://www.linuxjournal.com/content/how-install-and-use-NDISwrapper-video](http://www.linuxjournal.com/content/how-install-and-use-NDISwrapper-video)

Based on what ive read u basically use ndiswrapper as a layer between the windows driver and the linux kernel. Not sure about my terminology but i think u get the point.

I dont recall building my own drivers using ndiswrapper. So if anyone else has experience with Ndiswrapper, please feel free to help.

---

### Post by AKG_8 on 2010-04-28
Thanks a ton kindred .. I will post the progess ..

---

### Post by P4man on 2010-04-28
to install ndiswrapper in ubuntu, just go to ubuntu software center and install "windows wireless drivers" It will show up in system > adminstration > windows wireless drivers.

There you can install a windows driver for your card.

Please note, I have not checked on your card, I dont know if this is the best solution, but I saw links to ndiswrapper source files, and just wanted to spare you the headaches of installing it the hard way.

---

### Post by P4man on 2010-04-28
Okay, maybe Im missing something here, but nowhere do I see what wifi card you have? If you posted it, I missed it. Can you provide the output of

lspci

before we try the ndiswrapper way?

---

### Post by AKG_8 on 2010-04-28
Hi p4man .. here is the result of the lspci command ..


abhishek@abhishek-laptop:~$ lspci

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
05:05.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
05:05.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
05:05.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 0a)
05:05.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 05)
05:05.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
05:08.0 Ethernet controller: Intel Corporation PRO/100 VE Network Connection (rev 02)

---

### Post by P4man on 2010-04-29
That card is well supported under ubuntu, there should be no need for ndiswrapper. Can you post the output of

```
  sudo iwlist scan
```

Im guessing you might just have  interference from another network. Perhaps try changing the frequency (channel) on your router?

---

### Post by AKG_8 on 2010-04-29
H P4Man,

Here the resutls for the 'sudo iwlist scan' you asked me to do 

abhishek@abhishek-laptop:~$ sudo iwlist scan
[sudo] password for abhishek: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:23:69:BC:22:BC
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=41/70  Signal level=-69 dBm  
                    Encryption key:on
                    ESSID:"silverfox"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000002991838ba
                    Extra: Last beacon: 1804ms ago
                    IE: Unknown: 000973696C766572666F78
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030103
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180201F0000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 02 - Address: 00:22:3F:06:C6:2B
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=49/70  Signal level=-61 dBm  
                    Encryption key:on
                    ESSID:"jarlsberger"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000822724d469e
                    Extra: Last beacon: 1664ms ago
                    IE: Unknown: 000B6A61726C73626572676572
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 030106
                    IE: Unknown: 0706555320010B1B
                    IE: Unknown: 200100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0102
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101820003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010011FF7F
          Cell 03 - Address: 00:21:29:87:E3:B3
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption key:on
                    ESSID:"Rudolph Krispie"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000002ade0c72321
                    Extra: Last beacon: 1640ms ago
                    IE: Unknown: 000F5275646F6C7068204B726973706965
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD7E0050F204104A0001101044000102103B00010310470010138140001DD211B29FFFC67E816B4BFB102100074C696E6B73797310230006526F7574657210240007575254353447321042000C4353563030483442343433321054000800060050F204000110110011576972656C6573732D4720526F75746572100800020088
                    IE: Unknown: DD090010180201F4000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: 00:0D:88:20:0D:86
                    Channel:4
                    Frequency:2.427 GHz (Channel 4)
                    Quality=49/70  Signal level=-61 dBm  
                    Encryption key:on
                    ESSID:"4-STAR PRODUCTIONS"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Mode:Master
                    Extra:tsf=0000000356da3108
                    Extra: Last beacon: 1728ms ago
                    IE: Unknown: 0012342D535441522050524F44554354494F4E53
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030104
          Cell 05 - Address: 00:22:3F:96:FF:06
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/70  Signal level=-22 dBm  
                    Encryption key:off
                    ESSID:"network_416"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000006e04ad71ec
                    Extra: Last beacon: 1572ms ago
                    IE: Unknown: 000B6E6574776F726B5F343136
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 03010B
                    IE: Unknown: 0706555320010B1B
                    IE: Unknown: 200100
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101830003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F0101002CFF7F
                    IE: Unknown: DD1A00037F030100000000223F96FF0606223F96FF0664002C012C08

pan0      Interface doesn't support scanning.


Please advise ..

Thanks a lot ...

AkG

---

### Post by AKG_8 on 2010-04-29
Forgot to mention in my previos msg .. my network is 'network_416'

---

### Post by P4man on 2010-04-30
I see nothing wrong there. Might be worth trying WiCD  instead of network-manager. You can find it in the repo's,

---

### Post by AKG_8 on 2010-04-30
Hi P4man and kindred ..

changing the frequency i.e the channel of the router helped .. Thanks a lot for your suggestions .. :-)

---

### Post by giostark on 2010-08-19
Hi all,
Im on opensuse 11.2 64bit and after some upgrade of some packs i had the same problem with networkmanager.
I have to admit that change the frequency of the router make it to work again.
BUT is absolutely BAD that things like this happens in the 2010 when we have fantadesktop with ultra effects.I spend lots of time for found in internet the solution. :mad:
The networkmanager have always trouble. 3 things are important in the networking of linux ,and one give serious trouble ... damn.

---

