---
title: "wireless troubles"
date: 2010-03-18
forum: Networking &amp; Wireless
---

### Post by bendable on 2010-03-18
Okay, I just got a HP mini 210 netbook and wanted to put linux on it, so I choose ubuntu, installed it and it works like a charm. Only thing is that I can't go online. As far as I can tell, the problem is that my wireless card, from Broadcom (14e4:4357)? doesn't like linux. I used ndiswrapper and installed the driver that I think is right, bcmwl6, but I still can't see any wireless connections in the network manager. Any help would be appreciated!

---

### Post by bkratz on 2010-03-19
> **bendable said:**
> Okay, I just got a HP mini 210 netbook and wanted to put linux on it, so I choose ubuntu, installed it and it works like a charm. Only thing is that I can't go online. As far as I can tell, the problem is that my wireless card, from Broadcom (14e4:4357)? doesn't like linux. I used ndiswrapper and installed the driver that I think is right, bcmwl6, but I still can't see any wireless connections in the network manager. Any help would be appreciated!

If you do have the 4357 then look at the readme on this page, yours is support by the sta driver..

[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

Also here is a thread where someone I happened to be helping gave complete instructions on installing his 4353 version, but the readme above actually gives complete directions too.

[http://ubuntuforums.org/showpost.php?p=8779364&postcount=7](http://ubuntuforums.org/showpost.php?p=8779364&postcount=7)

---

### Post by bendable on 2010-03-19
Well that worked up to a point. :\ I followed all the steps in the readme, everything seemed to be working, but all that happened was that the light for the wireless is now on (it wasn't before). It still doesn't detect any network connections. Any ideas?

---

### Post by bkratz on 2010-03-19
> **bendable said:**
> Well that worked up to a point. :\ I followed all the steps in the readme, everything seemed to be working, but all that happened was that the light for the wireless is now on (it wasn't before). It still doesn't detect any network connections. Any ideas?

Do you have a network icon in the top right of the screen. If so, if you left click on it do you see networks?  If not, is there a switch or keystroke required to turn on wireless? If you are sure that it is on drop to the terminal "applications>>accessories>>terminal" and type in

```
sudo lshw -C network
sudo iwlist scan
iwconfig
```

(the lshw is LSHW in lowercase, C in upper). Copy/paste the outputs of each back here using the code tags (#) for readability. The sudo commands will require you to enter your password which will not be visible, just hit enter when done.

---

### Post by bendable on 2010-03-19
My, I feel stupid. They are listed right in plain sight. :p Thank you so much for your help! Of course it still doesn't seem to want to connect. I pick my network (linksys), type in the password, and it tries to connect, but then a few seconds later it just asks for the password again. I'm not sure if that would be a problem with my computer or not though. If you can help me again, that would be absolutely fantastic. Here's that information you asked for in case it could help.

sudo lshw -C network

```
bendable@Dr:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 02
       serial: 00:26:9e:db:d6:07
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.13 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:27 ioport:5000(size=256) memory:50010000-50010fff(prefetchable) memory:50000000-5000ffff(prefetchable) memory:50020000-5002ffff(prefetchable)
  *-network
       description: Wireless interface
       product: Broadcom Corporation
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth1
       version: 01
       serial: c4:17:fe:11:32:37
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.60.48.36 latency=0 multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:56000000-56003fff
bendable@Dr:~$ 


```sudo iwlist scan
```
bendable@Dr:~$ sudo iwlist scan
[sudo] password for bendable: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:21:29:CF:45:50
                    ESSID:"linksys"
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:5/5  Signal level:-14 dBm  Noise level:-92 dBm
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD820050F204104A0001101044000102103B000103104700102880288028801880A880002129CF45501021000C4C696E6B73797320496E632E102300095752543136304E76321024000776322E302E3032104200033030381054000800060050F2040001101100114C696E6B737973205752543136304E7632100800020084103C000101
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 12 Mb/s
                              24 Mb/s; 48 Mb/s
          Cell 02 - Address: 00:26:5E:0D:36:F0
                    ESSID:"f862"
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:1/5  Signal level:-86 dBm  Noise level:-92 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
          Cell 03 - Address: 00:23:69:AE:2D:73
                    ESSID:"VALUEDCUSTOM-PC_Network"
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:1/5  Signal level:-89 dBm  Noise level:-92 dBm
                    IE: Unknown: DD0E0050F204104A0001101044000102
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s

bendable@Dr:~$ 


```iwconfig
```
bendable@Dr:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Nickname:""
          Access Point: Not-Associated   
          Link Quality:5  Signal level:0  Noise level:163
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

bendable@Dr:~$ 

```

EDIT: Nevermind, i was typing in the wrong password, the solution works perfectly, thanks!!

---

### Post by bkratz on 2010-03-19
> **bendable said:**
> My, I feel stupid. They are listed right in plain sight. :p Thank you so much for your help! Of course it still doesn't seem to want to connect. I pick my network (linksys), type in the password, and it tries to connect, but then a few seconds later it just asks for the password again. I'm not sure if that would be a problem with my computer or not though. If you can help me again, that would be absolutely fantastic. Here's that information you asked for in case it could help.



Well everything looks pretty much in order. Apparently the card is working well enough to see all the available networks.  You might try to remove all your encryption on the A/P ( just temporarily ) to make sure that you can connect and everything works. You did right click on the network icon and setup the wireless network for the right type of encryption, right? WPA2-psk etc. under the security tab.

---

