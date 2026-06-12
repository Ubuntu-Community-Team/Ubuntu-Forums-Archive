---
title: "Wireless frequently drops in Ubuntu 8.10 on my Dell XPS 1530 using wireless-N"
date: 2009-01-16
forum: Networking &amp; Wireless
---

### Post by eboracum on 2009-01-16
Hello.  I have a strange problem with my wireless connection dropping in Ubuntu with my home router (network name 'ebor' below) some of the time, but working just fine with my school's wireless (which is unencrypted) and my neighbor's unencrypted wireless (network name 'linksys' below).  Also, my home router works just fine when I am in Vista (I dual-boot), just not linux.  When I'm in Ubuntu and connect, I have perfectly good wireless for at least a few minutes.  Generally after using it some (maybe 10 minutes of usage), the connection stops working.  The signal strength is still strong (4 bars), but I can't access the internet.  When I try to reconnect to the home connection, I can sometimes get a few more minutes of use out of it, but then have to restart before being able to get internet at all.  As I said, I don't have this problem when using my neighbor's unencrypted wireless or my school connection (also unencrypted).  I use WPA2 encryption on my home connection, and my router is ENCORE ENHWI-N2 IEEE 802.3/3u.  I am a linux noob, but have spent some time searching for similar problems on the forums and online to no avail.  I have found a few other people with the same problem, but no solutions.  Below is the stuff the HOWTO forum says to include:

1) Laptop Dell XPS M 1530

2) $ lspci -nn | grep 'wireless'
0b:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection [8086:4229] (rev 61)

3) $ iwconfig wlan0
wlan0     IEEE 802.11abgn  ESSID:"ebor"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:18:E7:57:44:AC   
          Bit Rate=60 Mb/s   Tx-Power=14 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=100/100  Signal level:-27 dBm  Noise level=-93 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

4) $ lsmod (I've pasted what I think are the related things below):
iwlagn                 99588  0 
iwlcore                92740  1 iwlagn
mac80211              216820  2 iwlagn,iwlcore
cfg80211               32392  3 iwlagn,iwlcore,mac80211

5) $ dmesg | grep wlan
[   25.212476] wlan0: authenticate with AP 00:22:6b:5d:f1:47
[   25.215067] wlan0: authenticated
[   25.215082] wlan0: associate with AP 00:22:6b:5d:f1:47
[   25.218854] wlan0: RX AssocResp from 00:22:6b:5d:f1:47 (capab=0x401 status=0 aid=3)
[   25.218865] wlan0: associated
[   25.218965] wlan0 (WE) : Wireless Event too big (338)
[   25.237806] wlan0: disassociating by local choice (reason=3)
[   46.725891] wlan0: deauthenticated
[   46.726236] wlan0: authenticate with AP 00:22:6b:5d:f1:47
[   46.728455] wlan0: authenticated
[   46.728470] wlan0: associate with AP 00:22:6b:5d:f1:47
[   46.732126] wlan0: RX ReassocResp from 00:22:6b:5d:f1:47 (capab=0x401 status=0 aid=3)
[   46.732142] wlan0: associated
[   46.732228] wlan0 (WE) : Wireless Event too big (338)
[   46.761316] wlan0: disassociating by local choice (reason=3)
[   56.658575] wlan0: deauthenticated
[   56.658988] wlan0: authenticate with AP 00:22:6b:5d:f1:47
[   56.677116] wlan0: authenticate with AP 00:18:e7:57:44:ac
[   56.686720] wlan0: authenticate with AP 00:18:e7:57:44:ac
[   56.686765] wlan0: authenticated
[   56.686772] wlan0: associate with AP 00:18:e7:57:44:ac
[   56.704435] wlan0: RX AssocResp from 00:18:e7:57:44:ac (capab=0x431 status=0 aid=1)
[   56.704450] wlan0: associated
[   56.704559] wlan0 (WE) : Wireless Event too big (342)
[   72.888180] wlan0: no IPv6 routers present
[ 2268.834494] wlan0: disassociating by local choice (reason=3)
[ 2270.845688] wlan0: Failed to config new SSID to the low-level driver
[ 2272.831701] wlan0: authenticate with AP 00:22:6b:5d:f1:47
[ 2272.833569] wlan0: authenticated
[ 2272.833584] wlan0: associate with AP 00:22:6b:5d:f1:47
[ 2272.837230] wlan0: RX AssocResp from 00:22:6b:5d:f1:47 (capab=0x401 status=0 aid=4)
[ 2272.837250] wlan0: associated
[ 2272.837343] wlan0 (WE) : Wireless Event too big (338)
[ 3245.967318] wlan0: disassociating by local choice (reason=3)
[ 3245.989650] wlan0: authenticate with AP 00:22:6b:5d:f1:47
[ 3246.025255] wlan0: authenticated
[ 3246.025268] wlan0: associate with AP 00:22:6b:5d:f1:47
[ 3246.060447] wlan0: RX AssocResp from 00:22:6b:5d:f1:47 (capab=0x401 status=0 aid=4)
[ 3246.060457] wlan0: associated
[ 3246.060520] wlan0 (WE) : Wireless Event too big (338)
[ 3246.072777] wlan0: disassociating by local choice (reason=3)
[ 3284.718396] wlan0: deauthenticated
[ 3284.718869] wlan0: authenticate with AP 00:22:6b:5d:f1:47
[ 3284.736800] wlan0: authenticate with AP 00:18:e7:57:44:ac
[ 3284.756404] wlan0: authenticate with AP 00:18:e7:57:44:ac
[ 3284.761757] wlan0: authenticated
[ 3284.761776] wlan0: associate with AP 00:18:e7:57:44:ac
[ 3284.777147] wlan0: RX AssocResp from 00:18:e7:57:44:ac (capab=0x431 status=0 aid=1)
[ 3284.777161] wlan0: associated
[ 3284.777253] wlan0 (WE) : Wireless Event too big (342)

6) $ sudo lshw -C network
[sudo] password for andrewdc: 
  *-network               
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 12
       serial: 00:21:9b:ea:e8:c7
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.22 firmware=N/A latency=0 link=no module=sky2 multicast=yes port=twisted pair
  *-network
       description: Wireless interface
       product: PRO/Wireless 4965 AG or AGN [Kedron] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       logical name: wmaster0
       version: 61
       serial: 00:21:5c:8a:d3:ed
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn ip=192.168.1.101 latency=0 module=iwlagn multicast=yes wireless=IEEE 802.11abgn
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 6e:b0:c2:9a:b5:76
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

7) $ iwlist scan
wlan0     Scan completed :
          Cell 01 - Address: 00:22:6B:5D:F1:47
                    ESSID:"linksys"
                    Mode:Master
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=80/100  Signal level:-54 dBm  Noise level=-127 dBm
                    Encryption key:off
                    IE: Unknown: 2D1AEC0117FFFF0000000000000000000000000000000C0000000000
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 12 Mb/s
                              24 Mb/s; 48 Mb/s
                    Extra:tsf=000000dc068321eb
                    Extra: Last beacon: 3700ms ago
          Cell 02 - Address: 00:18:E7:57:44:AC
                    ESSID:"ebor"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=100/100  Signal level:-27 dBm  Noise level=-92 dBm
                    Encryption key:on
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2D1A4E101BFFFF000000000000000000000000000000000000000000
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=000000114bfc1180
                    Extra: Last beacon: 44ms ago

8) Ubuntu 8.10

9) $ uname -mr
2.6.27-9-generic i686

10) $ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          Ignoring unknown interface wlan0=wlan0.
                                                                         [ OK ]

---

### Post by cdahmedeh on 2009-01-17
I have the same laptop and I get the same problems. However, the disconnects happen every hour on a unencrypted network only protected by MAC Address Filtering.

---

### Post by maggiagg on 2009-01-27
I am having a similiar problem on totally different hardware. See [http://ubuntuforums.org/showthread.php?t=1030392](http://ubuntuforums.org/showthread.php?t=1030392). 

It seems like the network is just dropped. restarting gets it up again for a while.

---

### Post by capscrew on 2009-01-27
This bug resport may explain the problem.  See:[[COLOR="Black"]**https://bugs.launchpad.net/ubuntu/+source/linux/+bug/267063**[/COLOR]]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/267063")

---

### Post by eboracum on 2009-02-14
Okay, I found the solution by trying to fix one of my other problems, system freezes.  Apparently, there's a bug in the intel wireless card driver for the 4965AGN cards in Intrepid that causes both system freezes and problems getting wireless.  The solution for me was to install "linux-backports-modules-intrepid" using the package manager.  The solution was described here:
[http://ubuntuforums.org/archive/index.php/t-969657.html](http://ubuntuforums.org/archive/index.php/t-969657.html)

---

### Post by Pylon757 on 2009-02-15
Same issues, with a Sony Vaio and a TEW-424UB USB card. Wireless works fine in XP though.

---

