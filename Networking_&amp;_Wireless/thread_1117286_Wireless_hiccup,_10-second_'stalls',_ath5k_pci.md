---
title: "Wireless hiccup, 10-second 'stalls', ath5k_pci"
date: 2009-04-05
forum: Networking &amp; Wireless
---

### Post by that1swede on 2009-04-05
**The setup:**
I'm on a *Fujutsu Lifebook A-3210* laptop using the wireless connection in conjunction with a *Linksys WRT54G2* router. The wireless chipset is a 
*Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)*.


**The problem:**
Every so often the wireless connection seems to stall for around 10 seconds, suspending any network traffic. It happens every two minutes, pretty much like clockwork. At the time of the stalling the ath5k_pci process' CPU usage jumps..

```
  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND 
 1363 root      15  -5     0    0    0 S   11  0.0   0:48.02 [ath5k_pci]
```

Continuosly pinging another computer on the local network shows the 'stall'..

```
64 bytes from 192.168.1.102: icmp_seq=2006 ttl=128 time=1.13 ms
64 bytes from 192.168.1.102: icmp_seq=2007 ttl=128 time=2.25 ms
64 bytes from 192.168.1.102: icmp_seq=2008 ttl=128 time=9629 ms
64 bytes from 192.168.1.102: icmp_seq=2009 ttl=128 time=8621 ms
64 bytes from 192.168.1.102: icmp_seq=2010 ttl=128 time=7614 ms
64 bytes from 192.168.1.102: icmp_seq=2011 ttl=128 time=6606 ms
64 bytes from 192.168.1.102: icmp_seq=2012 ttl=128 time=5600 ms
64 bytes from 192.168.1.102: icmp_seq=2013 ttl=128 time=4592 ms
64 bytes from 192.168.1.102: icmp_seq=2014 ttl=128 time=3584 ms
64 bytes from 192.168.1.102: icmp_seq=2015 ttl=128 time=2577 ms
64 bytes from 192.168.1.102: icmp_seq=2016 ttl=128 time=1578 ms
64 bytes from 192.168.1.102: icmp_seq=2017 ttl=128 time=579 ms
64 bytes from 192.168.1.102: icmp_seq=2018 ttl=128 time=0.837 ms
64 bytes from 192.168.1.102: icmp_seq=2019 ttl=128 time=0.809 ms
```



**Other information:**

```
$ ifconfig
wlan0     Link encap:Ethernet  HWaddr 00:1b:9e:d9:58:fc  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:9eff:fed9:58fc/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:35227 errors:0 dropped:0 overruns:0 frame:0
          TX packets:28179 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:40321915 (40.3 MB)  TX bytes:3794119 (3.7 MB)

```


```
$ iwconfig
wlan0     IEEE 802.11abg  ESSID:"smoothie"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:21:29:91:78:36   
          Bit Rate=11 Mb/s   Tx-Power=20 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=85/100  Signal level:-41 dBm  Noise level=-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```


```
$  lsmod | grep ath5k
ath5k                 107008  0 
mac80211              217208  1 ath5k
led_class              12036  1 ath5k
cfg80211               38032  2 ath5k,mac80211


```

```
$ dmesg | grep ath5k
[   11.137342] ath5k_pci 0000:07:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[   11.137353] ath5k_pci 0000:07:00.0: setting latency timer to 64
[   11.137500] ath5k_pci 0000:07:00.0: registered as 'phy0'
[   11.405914] ath5k phy0: Atheros AR5414 chip found (MAC: 0xa3, PHY: 0x61)

```

```
$ dmesg | grep wlan
[   29.120528] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   75.031668] wlan0: authenticate with AP 00:21:29:91:78:36
[   75.034783] wlan0: authenticated
[   75.034786] wlan0: associate with AP 00:21:29:91:78:36
[   75.037304] wlan0: RX AssocResp from 00:21:29:91:78:36 (capab=0x411 status=0 aid=1)
[   75.037306] wlan0: associated
[   75.037767] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready

```

```
$ sudo lshw -C network
  *-network
       description: Wireless interface
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: wmaster0
       version: 01
       serial: 00:1b:9e:d9:58:fc
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath5k_pci ip=192.168.1.100 latency=0 module=ath5k multicast=yes wireless=IEEE 802.11abg

```

```
$ iwlist wlan0 scan
wlan0     Scan completed :
          Cell 01 - Address: 00:21:29:91:78:36
                    ESSID:"smoothie"
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=81/100  Signal level:-43 dBm  Noise level=-95 dBm
                    Encryption key:on
                    IE: Unknown: 0008736D6F6F74686965
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD7E0050F204104A0001101044000102103B00010310470010138140001DD211B29FFFC67E816B4BFB102100074C696E6B73797310230006526F7574657210240007575254353447321042000C4353563031483537393334371054000800060050F204000110110011576972656C6573732D4720526F75746572100800020088
                    IE: Unknown: DD090010180200F4000000
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=000000248d323183
                    Extra: Last beacon: 16ms ago

```

```
$ lsb_release -d
Description:	Ubuntu jaunty (development branch)
```

```
$ uname -mr
2.6.28-11-generic i686

```


Any ideas on what's going on here?

---

### Post by battlebison on 2009-04-05
I did a google search and came across this article: [http://www.genmay.com/showthread.php?t=728574](http://www.genmay.com/showthread.php?t=728574)

It looks like it might be more of a physical location issue than soft/hardware. Also, in the comments they suggested changing the wireless channels to see if that helps.

I'm not sure what would cause your problem exactly, but if it comes in waves, it very well could be interference with other devices, which of course supports the idea of changing channel or location.

---

### Post by barometz on 2009-10-07
It's always good to see that I'm not the only one with a certain issue.  I've got the same hiccups every two minutes, indeed like a clockwork.  Over here it's the phy1 process (a driver for the physical network layer or something along those lines?) that creates fairly high load during and after the hiccup.  The specific timing of the hiccups appears to depend on the time of loading of the ath5k module.

It occurs in at least two locations several kilometers apart, so I'm inclined to rule physical interference out. 

This is a Thinkpad t60p, with an Atheros AR5212 card using the ath5k driver.  Ubuntu Karmic beta running 2.6.31-12-generic, but it's occured in Jaunty stable as well.

Has anyone (or possibly the OP?) found a solution to this?  It's not a huge problem most of the time, but pretty inconvenient when working with remote systems.

Details:
```

$ dmesg | grep ath5k
[ 5306.428375] ath5k 0000:03:00.0: PCI INT A disabled
[ 5311.613423] ath5k 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[ 5311.613440] ath5k 0000:03:00.0: setting latency timer to 64
[ 5311.613491] ath5k 0000:03:00.0: registered as 'phy2'
[ 5311.765809] Registered led device: ath5k-phy2::rx
[ 5311.765828] Registered led device: ath5k-phy2::tx
[ 5311.765832] ath5k phy2: Atheros AR5414 chip found (MAC: 0xa3, PHY: 0x61)

```That there is a little bit confusing to say the least, as lspci claims it's an AR5212.

Edit: Just did some wiresharking, I'm sending a bunch of ARP requests for my gateway right after most hiccups.  Not sure what's cause and what's effect here, but it's definitely related.

More updates: the hiccup does not occur in Windows, which confirms (well, near enough) my suspicion that it has nothing to do with external interference.

---

