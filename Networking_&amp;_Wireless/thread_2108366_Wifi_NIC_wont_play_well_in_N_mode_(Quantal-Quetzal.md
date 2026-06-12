---
title: "Wifi NIC wont play well in N mode (Quantal-Quetzal)"
date: 2013-01-24
forum: Networking &amp; Wireless
---

### Post by Scarberian on 2013-01-24
I am not new to Ubuntu but I have been in the microsoft world since Edgy Eft came out so bear with me.

When my router is in b/g/n mixed mode I can get WPA/WPA2 PSK authentication and apparently a local connection but not internet! I switched to b/g mode and everything is hunky dory I am online right now doing this. 

Everyone in the house is feeling withdrawl effects without N mode. The XBOX won't stream movies anymore, it just buffers endlessly. I would really like to sort this out and set the router back to some kind of N mode this week.

The vendor does offer a driver but I don't know if it is still relevant[http://www.smc.com/index.cfm?event=downloads.searchResultsDetail&localeCode=EN_USA&productCategory=5&partNumber=4220&modelNumber=1655&knowsPartNumber=false&userPartNumber=&docId=6188]("http://www.smc.com/index.cfm?event=downloads.searchResultsDetail&localeCode=EN_USA&productCategory=5&partNumber=4220&modelNumber=1655&knowsPartNumber=false&userPartNumber=&docId=6188")

I don't know where to start with that driver. How can I test it and if it breaks something how can I revert back?



NIC:
```
SMCWPCI-N2 
```

lspci:Network controller: 
```
Ralink corp. RT2800 802.11n PCI

iwconfig:
wlan0     IEEE 802.11bgn  ESSID:"***********"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: BC:14:01:31:30:B8   
          Bit Rate=1 Mb/s   Tx-Power=27 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=38/70  Signal level=-72 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:874  Invalid misc:0   Missed beacon:0
```

lsmod | grep rt2800:
```

rt2800pci              18152  0 
rt2800lib              57144  1 rt2800pci
crc_ccitt              12595  1 rt2800lib
rt2x00pci              14116  1 rt2800pci
rt2x00lib              48562  3 rt2800pci,rt2800lib,rt2x00pci
mac80211              461161  3 rt2800lib,rt2x00pci,rt2x00lib
eeprom_93cx6           13134  1 rt2800pci
```


sudo lshw -C network:
```
*-network               
       description: Wireless interface
       product: RT2800 802.11n PCI
       vendor: Ralink corp.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: wlan0
       version: 00
       serial: 00:13:f7:ca:4a:7e
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2800pci driverversion=3.5.0-17-generic firmware=0.34 ip=192.168.0.12 latency=32 link=yes maxlatency=4 mingnt=2 multicast=yes wireless=IEEE 802.11bgn
       resources: irq:21 memory:d3100000-d310ffff
```

iwlist scan:```

wlan0     Scan completed :
          Cell 01 - Address: BC:14:01:31:30:B8
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption key:on
                    ESSID:"***********"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000024a19c9c8a
                    Extra: Last beacon: 99948ms ago
                    IE: Unknown: 000B526F676572733434323337
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0106
                    IE: Unknown: 32040C183060
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 0B0503001F127A
                    IE: Unknown: DD07000C4304000000
                    IE: Unknown: 0706555320010B10
                    IE: Unknown: DD870050F204104A0001101044000102103B000103104700102880288028801880A880BC14013130B810210006484954524F4E102300094344452D33303336341024000A313530333230303030311042000C3235303131373032323235351054000800060050F20400011011000652543333353210080002210C103C0001011049000600372A000120
```


lsb_release -d:
```
Description:	Ubuntu 12.10
```

uname -mr:
```
3.5.0-17-generic i686
```

---

### Post by praseodym on 2013-01-24
Hi,

please show the chipset:
```

lspci -nnk | grep -iA2 net
dmesg | grep rt2
```
For mixed encryption try **Wicd** instead of the network-manager.

---

### Post by Scarberian on 2013-01-24
> **praseodym said:**
> Hi,

please show the chipset:
```

lspci -nnk | grep -iA2 net
dmesg | grep rt2
```
For mixed encryption try **Wicd** instead of the network-manager.


Here is the chipset:
```
Network controller [0280]: Ralink corp. RT2800 802.11n PCI [1814:0601]
	Subsystem: Device [200d:1976]
	Kernel driver in use: rt2800pci
```

dmesg | grep rt2 returns nothing 

I will try **Wicd** but are you refering to the WPA/WPA2 mix or the B/G/N mix? Both?

Thanks.

---

### Post by praseodym on 2013-01-25
Wicd works better with mixed mode. Alternatively, try this driver:
```

sudo apt-get install --reinstall linux-headers-$(uname -r) linux-headers-generic* build-essential dkms
wget http://www.pchsws.net/DATEIEN/rt2860sta.deb
sudo dpkg -i rt2860sta.deb
echo -e "blacklist rt2800pci\nblacklist rt2800lib" | sudo tee -a /etc/modprobe.d/blacklist.conf
sudo apt-get autoremove
```
Reboot

---

### Post by Scarberian on 2013-01-25
> **praseodym said:**
> Wicd works better with mixed mode. Alternatively, try this driver:
```

sudo apt-get install --reinstall linux-headers-$(uname -r) linux-headers-generic* build-essential dkms
wget http://www.pchsws.net/DATEIEN/rt2860sta.deb
sudo dpkg -i rt2860sta.deb
echo -e "blacklist rt2800pci\nblacklist rt2800lib" | sudo tee -a /etc/modprobe.d/blacklist.conf
sudo apt-get autoremove
```
Reboot
I am posting this from my iPod because after doing this, I can't detect any wifi networks. 
EDIT:On a modprobe I can't find any rt2860sta only a rt3090sta module weird

---

### Post by praseodym on 2013-01-25
Then load this one:
```

sudo modprobe rt3090sta
iwconfig
dmesg | egrep 'rt2|rt3'
sudo iwlist scan
iwlist chan
route -n
cat /etc/resolv.conf
```

---

### Post by Scarberian on 2013-01-25
> **praseodym said:**
> Then load this one:
```

sudo modprobe rt3090sta
iwconfig
dmesg | egrep 'rt2|rt3'
sudo iwlist scan
iwlist chan
route -n
cat /etc/resolv.conf
```

I'll try this tomorrow. I have since whitelisted the rt2800 driver. Do I just blacklist it again and then run the above lines to try rt3060sta?

---

### Post by kurt18947 on 2013-01-25
I'm not sure if your situation is the same as mine but I had a similar problem.  G speeds would work with WPA2, N speeds would not, wouldn't even connect. I posted a thread about my experience here:


[http://ubuntuforums.org/showthread.php?t=2107884](http://ubuntuforums.org/showthread.php?t=2107884)

I'm not sure if my solution would help you or not but I'm pleased.

---

### Post by Scarberian on 2013-01-25
> **kurt18947 said:**
> I'm not sure if your situation is the same as mine but I had a similar problem.  G speeds would work with WPA2, N speeds would not, wouldn't even connect. I posted a thread about my experience here:


[http://ubuntuforums.org/showthread.php?t=2107884](http://ubuntuforums.org/showthread.php?t=2107884)

I'm not sure if my solution would help you or not but I'm pleased.

Thank you for the input!):P However, my device is a rental from my ISP. It is a router/modem combo. I would surely become a tech-support pariah if I flashed their kit with some homebrew.

---

### Post by kurt18947 on 2013-01-31
> **Scarberian said:**
> Thank you for the input!):P However, my device is a rental from my ISP. It is a router/modem combo. I would surely become a tech-support pariah if I flashed their kit with some homebrew.

I doubt you'd win the vote for "Mr. Popularity":biggrin:. I have a similar situation, I need MoCA capability so I pretty much had to leave the ISP's router in place.  The ISP's router is N speed capable -- sorta. It maxes out at 65 Mb./sec.  I have a couple devices that are G speed only so I had to run the ActionTec MI-424WR in compatibility mode.  That seemed pretty slow compared to N speed only.  My solution was to buy a used second router with N300 hardware after making sure DD-WRT would install then configure it was a daisy chained wireless access point.  The ISP's router supports G speed devices, The Linksys WRT300N supports N speed devices.  I did reduce the transmit power on the WiFi radios so as to minimize interference with neighboring networks.  So far so good, no torches, pitchforks and clubs from either the ISP or the neighbors.

---

