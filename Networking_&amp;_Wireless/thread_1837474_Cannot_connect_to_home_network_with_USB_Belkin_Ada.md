---
title: "Cannot connect to home network with USB Belkin Adapter"
date: 2011-09-01
forum: Networking &amp; Wireless
---

### Post by mcfc4eva on 2011-09-01
Hi,

I am having trouble connecting to my router using a Belkin USB Wireless Adapter.

I could connect fine yesterday and with no changes made it suddenly won't connect now.

It finds available networks, and I can connect to my neighbours unsecured networks fine (although it's a bit slow) but when I try connecting to my own network (WEP2 secured) it times out. I know that the network is running and the password is correct as I have a couple of Windows PC's connected without problems. I have tried deleting the "remembered" preferences for the network and rebooting before retrying to connect, at least half a dozen times.

I also have installed something called WICD, which I read is useful but the same thing happens. However, using WICD sometimes the error comes up as incorrect password or 'cannot obtain ip'. Again, I am 100% sure the password is correct.

I am using a [Belkin N Wireless USB Adapter]("http://www.amazon.co.uk/Belkin-N-Wireless-USB-Adapter/dp/B000WKXK00") and a [Belkin N150 Enhanced Router]("http://www.belkin.com/IWCatProductPage.process?Product_Id=492429").

Any suggestions?

Thanks
--Mike

[SIZE="1"]Please note I am new to Ubuntu (and all Linux for that matter) so I just about understand how to open terminal, I'm completely bamboozled by all the commands so bear with me :)[/SIZE]

---

### Post by wildmanne39 on 2011-09-01
Hi, if you installed wicd you need to make sure you uninstalled network manager.

I just finished with another person that installed wicd and he had to set a static ip address with wicd it would not get it automatically.

Please run these commands and post the results here, just copy and paste them into the terminal.
```
sudo lshw -C network
```
```
nm-tool
```
```
lsusb
```
```
iwconfig
```
```
rfkill list all
```
```
dmesg | grep wlan0
```
Thank you

---

### Post by mcfc4eva on 2011-09-02
Hi wildmanne39,

For some reason I managed to connect to my network first time using WICD (Network Manager is uninstalled).

Whilst I am connected, I have run the commands you asked and displayed the results below and in a moment I will reboot my system to make sure it didn't connect on a fluke.

> ```
sudo lshw -C network
```
```
  *-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 3
       bus info: pci@0000:02:03.0
       logical name: eth0
       version: 10
       serial: 00:01:6c:18:57:31
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=32 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10Mbit/s
       resources: irq:16 ioport:ee00(size=256) memory:fdeff000-fdeff0ff
  *-network
       description: Wireless interface
       physical id: 1
       bus info: usb@1:6
       logical name: wlan0
       serial: 00:1c:df:6a:48:ed
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rt2800usb driverversion=2.6.38-11-generic firmware=0.12 ip=192.168.2.3 link=yes multicast=yes wireless=IEEE 802.11bgn

```

> ```
nm-tool
```
```
NetworkManager Tool

State: connected

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            8139too
  State:             unavailable
  Default:           no
  HW Address:        00:01:6C:18:57:31

  Capabilities:
    Carrier Detect:  yes
    Speed:           10 Mb/s

  Wired Properties
    Carrier:         off


- Device: wlan0  [Auto RutaNet] ------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rt2800usb
  State:             connected
  Default:           yes
  HW Address:        00:1C:DF:6A:48:ED

  Capabilities:
    Speed:           54 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    Tardis:          Infra, F0:7D:68:4E:1D:70, Freq 2437 MHz, Rate 54 Mb/s, Strength 37 WEP
    neil linksys:    Infra, 00:1A:70:9B:EE:24, Freq 2437 MHz, Rate 54 Mb/s, Strength 31 WPA
    dlink:           Infra, 1C:BD:B9:B7:9D:A0, Freq 2437 MHz, Rate 54 Mb/s, Strength 48
    poppy:           Infra, 00:24:B2:B4:8A:C2, Freq 2437 MHz, Rate 54 Mb/s, Strength 42 WPA
    ZyXEL:           Infra, 00:19:CB:3C:09:1A, Freq 2437 MHz, Rate 54 Mb/s, Strength 37 WPA2
    virginmedia4242716: Infra, A0:21:B7:CD:8A:96, Freq 2417 MHz, Rate 54 Mb/s, Strength 60 WPA WPA2
    *RutaNet:        Infra, 00:22:75:6F:10:44, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WPA

  IPv4 Settings:
    Address:         192.168.2.3
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.2.1

    DNS:             192.168.2.1

```

> ```
lsusb
```
```
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 04f2:0935 Chicony Electronics Co., Ltd 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 050d:8053 Belkin Components F5D8053 N Wireless USB Adapter v1000/v4000 [Ralink RT2870]
Bus 001 Device 002: ID 058f:6362 Alcor Micro Corp. Flash Card Reader/Writer
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

> ```
iwconfig
```
```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"RutaNet"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:22:75:6F:10:44   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=70/70  Signal level=-40 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:173  Invalid misc:33   Missed beacon:0

```

> ```
rfkill list all
```
```
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

```

> ```
dmesg | grep wlan0
```
```
[   12.886396] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   22.037027] wlan0: authenticate with 00:22:75:6f:10:44 (try 1)
[   22.038528] wlan0: authenticated
[   23.643577] wlan0: associate with 00:22:75:6f:10:44 (try 1)
[   23.645970] wlan0: RX AssocResp from 00:22:75:6f:10:44 (capab=0x411 status=0 aid=4)
[   23.645975] wlan0: associated
[   23.658795] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   34.392015] wlan0: no IPv6 routers present
[   52.279756] wlan0: deauthenticating from 00:22:75:6f:10:44 by local choice (reason=3)
[   54.158410] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   56.362480] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   58.484531] wlan0: deauthenticating from 1c:bd:b9:b7:9d:a0 by local choice (reason=3)
[   60.108144] wlan0: authenticate with 00:22:75:6f:10:44 (try 1)
[   60.109858] wlan0: authenticated
[   61.717067] wlan0: associate with 00:22:75:6f:10:44 (try 1)
[   61.719580] wlan0: RX AssocResp from 00:22:75:6f:10:44 (capab=0x411 status=0 aid=4)
[   61.719587] wlan0: associated
[   61.728005] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   72.128009] wlan0: no IPv6 routers present

```

I will try these codes again if it fails to connect to the network in future, I don't know if they tell you any reasons why it didn't work here?

Thanks,
--Mike

---

### Post by wildmanne39 on 2011-09-02
Hi, the driver you are using I believe is not the best one for your adapter so that is the issue and I am pretty sure you are still going to have trouble.
Please post this results of this command.
```
lsmod | grep rt2
```
```
sudo iwlist scan
```
Thank you

---

### Post by mcfc4eva on 2011-09-02
> ```
lsmod | grep rt2
```
```
rt2870sta             410104  0 
rt2800usb              17907  0 
rt2800lib              43824  1 rt2800usb
crc_ccitt              12595  2 rt2870sta,rt2800lib
rt2x00usb              19693  1 rt2800usb
rt2x00lib              39075  3 rt2800usb,rt2800lib,rt2x00usb
mac80211              257001  3 rt2800lib,rt2x00usb,rt2x00lib
cfg80211              156212  2 rt2x00lib,mac80211

```


> ```
sudo iwlist scan
```
```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:22:75:6F:10:44
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=-40 dBm  
                    Encryption key:on
                    ESSID:"RutaNet"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000001653b59884
                    Extra: Last beacon: 12ms ago
                    IE: Unknown: 0007527574614E6574
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0104
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1AEE1113FF000000010000000000000000000000000C0000000000
                    IE: Unknown: 3D1606070700000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4307000000
                    IE: Unknown: DD1E00904C33EE1113FF000000010000000000000000000000000C0000000000
                    IE: Unknown: DD1A00904C3406070700000000000000000000000000000000000000
                    IE: Unknown: DDB70050F204104A0001101044000102103B00010310470010775B6680BFDE11D38D2F0022756F10441021001442656C6B696E20496E7465726E6174696F6E616C10230018456E68616E63656420576972656C65737320526F757465721024000C463644343233302D342076311042000E32303932303432333030353433331054000800060050F20400011011001F42656C6B696E20456E68616E63656420576972656C65737320526F75746572100800020084103C000101
          Cell 02 - Address: 1C:BD:B9:B7:9D:A0
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:off
                    ESSID:"dlink"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000959902614e
                    Extra: Last beacon: 296ms ago
                    IE: Unknown: 0005646C696E6B
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1AEE1117FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: 3D1606070500000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4307000000
                    IE: Unknown: 0706474220010D10
                    IE: Unknown: DD1E00904C33EE1117FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: DD1A00904C3406070500000000000000000000000000000000000000
                    IE: Unknown: DD050050F20500
                    IE: Unknown: DD750050F204104A00011010440001011041000100103B00010310470010B449250C54B9867370EE1CBDB9B79DA010210006442D4C696E6B102300074449522D363135102400074449522D3631351042000830303030303030301054000800060050F2040001101100074449522D363135100800020086
          Cell 03 - Address: F0:7D:68:4E:1D:70
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"Tardis"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001988fc8e178
                    Extra: Last beacon: 296ms ago
                    IE: Unknown: 0006546172646973
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030106
                    IE: Unknown: 32040C183060
                    IE: Unknown: 0706474220010D10
                    IE: Unknown: 33082001020304050607
                    IE: Unknown: 33082105060708090A0B
                    IE: Unknown: DD050050F20500
                    IE: Unknown: DD0E0050F204104A0001101044000101
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2D1AEE1117FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: 3D1606050700000000000000000000000000000000000000
                    IE: Unknown: 7F0101
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B0502002B127A
                    IE: Unknown: DD1E00904C33EE1117FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: DD1A00904C3406050700000000000000000000000000000000000000
                    IE: Unknown: DD07000C4307000000
          Cell 04 - Address: 00:19:CB:3C:09:1A
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"ZyXEL"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000005a92a542db
                    Extra: Last beacon: 296ms ago
                    IE: Unknown: 00055A7958454C
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 030106
                    IE: Unknown: 0706474220010D14
                    IE: Unknown: 200100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD0900037F01010020FF7F
          Cell 05 - Address: 00:1A:70:9B:EE:24
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"neil linksys"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000183d24987177
                    Extra: Last beacon: 296ms ago
                    IE: Unknown: 000C6E65696C206C696E6B737973
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030106
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 0406010200000000
                    IE: Unknown: 050400010100
                    IE: Unknown: 2A0100
                    IE: Unknown: 32080C1218243048606C
          Cell 06 - Address: A0:21:B7:CD:8A:96
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=42/70  Signal level=-68 dBm  
                    Encryption key:on
                    ESSID:"virginmedia4242716"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000009290490906
                    Extra: Last beacon: 4712ms ago
                    IE: Unknown: 001276697267696E6D6564696134323432373136
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030102
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A7E181BFFFF000001000000000000000000000000000000000000
                    IE: Unknown: 3D1602051B00000000000000000000000000000000000000
                    IE: Unknown: DD6F0050F204104A0001101044000102103B000103104700104D73C5C27E6B5243D6440AAB1719670B102100074E657467656172102300074E6574676561721024000631323334353610420007303030303030311054000800060050F20400011011000743473331303144100800020088
                    IE: Unknown: DD090010180201F0050000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C337E181BFFFF000001000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3402051B00000000000000000000000000000000000000

```

Seemed to work fine when I rebooted by the way.

---

### Post by wildmanne39 on 2011-09-02
Hi, if you are not having connection trouble then we should leave it as it is.
Thank you

---

### Post by nm_geo on 2011-09-02
> rt2870sta             410104  0 
 rt2800usb              17907  0 You do have two wireless drivers trying to control your wireless card as wildmanne was explaining. If you run into trouble again we would recommend you blacklist one of them and normally rt2800usb is the one we blacklist first.

---

### Post by mcfc4eva on 2011-09-03
> **nm_geo said:**
> You do have two wireless drivers trying to control your wireless card as wildmanne was explaining. If you run into trouble again we would recommend you blacklist one of them and normally rt2800usb is the one we blacklist first.

I only have 1 wireless device, and is a USB one so shouldn't I blacklist the other one (rt2870sta)? Also ...how do I blacklist it?

Thanks,
--Mike

---

### Post by wildmanne39 on 2011-09-03
Hi, the 2870sta is the one that works better even though you have a usb device I know it is strange.

This is how you black list the other drivers:
```
echo "blacklist rt2800usb" >> /etc/modprobe.d/blacklist.conf
echo "blacklist rt2x00usb" >> /etc/modprobe.d/blacklist.conf
exit
```
Then do this
```
sudo modprobe rt2870sta
```
Thank you

---

### Post by mcfc4eva on 2011-09-03
> **wildmanne39 said:**
> Hi, the 2870sta is the one that works better even though you have a usb device I know it is strange.

This is how you black list the other drivers:
```
echo "blacklist rt2800usb" >> /etc/modprobe.d/blacklist.conf
echo "blacklist rt2x00usb" >> /etc/modprobe.d/blacklist.conf
exit
```
Then do this
```
sudo modprobe rt2870sta
```
Thank you

I tried the 2 echo commands and I was shown a "Permission denied" error for both, so I used the "su" command, which I believe logs in as Super-user (correct me if I'm wrong) and then tried them. I wasn't displayed with an error, but neither was I displayed with a confirmation that it worked - should I have been?

Thanks,
--Mike

---

### Post by nm_geo on 2011-09-03
Answered below..

---

### Post by wildmanne39 on 2011-09-03
Hi, your right I made a mistake it should have been
```
sudo su
echo "blacklist rt2800usb" >> /etc/modprobe.d/blacklist.conf
echo "blacklist rt2x00usb" >> /etc/modprobe.d/blacklist.conf
exit
```
No it does not show confirmation, but I hope you did it just like I posted here or it might cause some files to be owned by root.

Please post the results of this command again.
```
lsmod | grep rt2
```
I am sorry it was my mistake.

---

### Post by mcfc4eva on 2011-09-07
> **wildmanne39 said:**
> Hi, your right I made a mistake it should have been
```
sudo su
echo "blacklist rt2800usb" >> /etc/modprobe.d/blacklist.conf
echo "blacklist rt2x00usb" >> /etc/modprobe.d/blacklist.conf
exit
```
No it does not show confirmation, but I hope you did it just like I posted here or it might cause some files to be owned by root.

Please post the results of this command again.
```
lsmod | grep rt2
```
I am sorry it was my mistake.

Hi Wildmanne,

I've executed the code and got the following result;
```
michael@michael-PC:~$ lsmod | grep rt2
[COLOR="red"]rt2[/COLOR]870sta             410104  1 
crc_ccitt              12595  1 [COLOR="Red"]rt2[/COLOR]870sta

```

---

### Post by praseodym on 2011-09-07
Hi,

shut off the power management:

```
sudo iwconfig wlan0 power off
sudo service wicd restart
```
You may try these encryption templates for wicd, too:

```
wget http://www.elektronenblitz63.de/download/wicd-1.6.x_addon0144.tar.gz
tar xvf wicd-1.6.x_addon0144.tar.gz
cd wicd-1.6.x_addon0144
sudo ./install_wicd_addon
sudo service wicd restart
```
They come from one of the developers (see also the sourceforge.net site for wicd)

---

### Post by wildmanne39 on 2011-09-07
Hi, the drivers look good now, can you connect good now or are you having encryption problems if so do what was mentioned in the previous post and set your wpa to wpa2.
Thank you

---

