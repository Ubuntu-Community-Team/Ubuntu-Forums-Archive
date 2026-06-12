---
title: "New user here - Cant connect wirelessly, keep getting asked to enter WPA key?"
date: 2010-05-18
forum: Networking &amp; Wireless
---

### Post by KyleSmith on 2010-05-18
I just installed Ubuntu 10.4 and when I click on the network button at the top, i get a list of networks, and when i try to connect to my network it wont connect and keeps asking me for my WPA password, even though its correct. Im totally lost since im a new user, so if you could put any solutions in laymens terms, it would be much appreciated.

Thanks

---

### Post by pytheas22 on 2010-05-19
The first thing I'd recommend trying is to connect using wicd, an alternative connection manager that may work better.  You can install wicd from the Software Center, or by typing the following commands, as long as you are plugged into the Internet (if you don't have any way to plug into the Internet, let me know and I'll give instructions for installing wicd without being online):
```

sudo apt-get update
sudo apt-get install wicd
```

You can then launch wicd from the Applications>Internet menu.  Does it work any better?

If wicd won't connect you, please post the output of these commands, and let me know the name of the network you're trying to connect to:
```

dmesg | grep wlan
lshw -C Network
sudo iwlist scan
```

Also just in case you don't know where to run these commands, you can open up a terminal from the Applications>Accessories menu.  You can highlight text in the terminal and right-click to copy and paste it.

---

### Post by KyleSmith on 2010-05-19
Wicd did not seem to work. The network I am trying to connect to is FAMILY-PC_network and this is what I get running those commands:


> kyle@kyle-laptop:~$ dmesg | grep wlan
[   19.150149] ADDRCONF(NETDEV_UP): wlan0: link is not ready
kyle@kyle-laptop:~$ 
kyle@kyle-laptop:~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: NetXtreme BCM5764M Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 10
       serial: 00:26:2d:54:77:bb
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.94 firmware=5764m-v3.34 latency=0 module=tg3 multicast=yes
  *-network
       description: Wireless interface
       product: AR928X Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wmaster0
       version: 01
       serial: 00:17:c4:bd:2b:2f
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath9k latency=0 module=ath9k multicast=yes wireless=IEEE 802.11bgn
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 12:c4:6e:45:3b:db
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
kyle@kyle-laptop:~$ sudo iwlist scan
[sudo] password for kyle: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:21:91:DC:B0:D1
                    ESSID:"FAMILY-PC_Network"
                    Mode:Master
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=87/100  Signal level:-39 dBm  Noise level=-95 dBm
                    Encryption key:on
                    IE: Unknown: 001146414D494C592D50435F4E6574776F726B
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030109
                    IE: Unknown: 2A0100
                    IE: Unknown: 32080C1218243048606C
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C334C101FFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340900070000000F000000000000000000000000000000
                    IE: Unknown: 2D1A4C101FFFFF000000000000000000000000000004000000000000
                    IE: Unknown: 3D160900130000000F000000000000000000000000000000
                    IE: Unknown: DD790050F204104A0001101044000102103B000103104700103100FDE745F93A22BF003D4DC5958BBB1021000E442D4C696E6B2053797374656D73102300074449522D363235102400024332104200046E6F6E651054000800060050F204000110110011576972656C657373204E20526F7574657210080002008C
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=00000015ba67d5a8
                    Extra: Last beacon: 148ms ago
          Cell 02 - Address: 00:0F:B3:A4:3B:68
                    ESSID:"angelo"
                    Mode:Master
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=9/100  Signal level:-89 dBm  Noise level=-95 dBm
                    Encryption key:off
                    IE: Unknown: 0006616E67656C6F
                    IE: Unknown: 010582848B962C
                    IE: Unknown: 030102
                    IE: Unknown: 2A0101
                    IE: Unknown: 32080C1218243048606C
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Extra:tsf=0000003fceaefd01
                    Extra: Last beacon: 640ms ago
          Cell 03 - Address: 00:1F:33:26:A9:74
                    ESSID:"NETGEAR"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=23/100  Signal level:-80 dBm  Noise level=-95 dBm
                    Encryption key:off
                    IE: Unknown: 00074E455447454152
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180202F0000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=000001636cfb73dd
                    Extra: Last beacon: 388ms ago

pan0      Interface doesn't support scanning.

kyle@kyle-laptop:~$ 


---

### Post by pytheas22 on 2010-05-19
Please try running these commands, while plugged into the Internet:
```

sudo apt-get update
sudo apt-get install linux-backports-modules-wireless-lucid
```

This will download and install a new version of your wireless driver that may work better.  After completing the installation, please reboot, and then try connecting to your network again.  Let me know how it goes.

---

### Post by KyleSmith on 2010-05-19
When entering the second command I got this error:

> kyle@kyle-laptop:~$ sudo apt-get install linux-backports-modules-wireless-lucid
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-backports-modules-wireless-lucid
i will still reboot and see if that helped.

EDIT: The commands did not help, could it be my network card is not compatible?

---

### Post by pytheas22 on 2010-05-20
> i will still reboot and see if that helped.

EDIT: The commands did not help, could it be my network card is not compatible?

Sorry, that was a mistake on my part.  The correct commands to type should be:
```

sudo apt-get update
sudo apt-get install linux-backports-modules-wireless-lucid-generic
```

I forgot the "generic" on the end.  Please give those commands a try, then reboot and see if it helps.

Also, if you prefer a graphical interface, you could search for linux-backports-modules-wireless-lucid-generic in the Ubuntu Software Center to install the package.

Your wireless driver is named ath9k; the linux-backports-modules-wireless-lucid-generic package provides a more recent version of that driver.  With any luck, it will solve your problem.

---

### Post by KyleSmith on 2010-05-20
I've fixed it, I went into my router settings and changed my security from WPA to WEP and that solved my problem, thanks for your help.

---

