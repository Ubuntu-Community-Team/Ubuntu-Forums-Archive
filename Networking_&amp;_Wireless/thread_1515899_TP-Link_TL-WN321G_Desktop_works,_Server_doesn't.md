---
title: "TP-Link TL-WN321G Desktop works, Server doesn't"
date: 2010-06-23
forum: Networking &amp; Wireless
---

### Post by MartinHansell on 2010-06-23
Hi,

I have read most of the posts (I think) regarding this matter, but none of them are conclusive enough.

I have two machines side by side, both with the same wireless dongle.  Both have worked successfully with Lucid 10.04 out of the box.  But when I installed Ubuntu Server 10.04 onto one machine, the wireless never even got started.

There are several threads in existence which between them have taught me how to query the system to see what's happening.  The results are below.  I have also [plugged in an Ethernet cable]("http://ubuntuforums.org/showthread.php?t=1510046") to perform an update, but still no joy.

I don't understand what the difference is between the two set-ups.  It might be something to do with the server itself (rather than a problem with the hardware).  For example, I struggled to set up the DHCP server, so eventually uninstalled it to get back to what my desktop looks like.  [DHCP is being managed by my wireless router.]

Can anyone assist?

Many thanks,
Martin

ADDITIONAL INFO - Here's what I really don't understand.  I did a scan after following the [instructions on this page]("http://serverfault.com/questions/142225/connect-to-wep-wireless-network-by-command-line-on-ubuntu"), and it shows my wireless dongle as being able to find my wireless router - if I am reading the output correctly?  But I just can't use it (still).

```
wlan0     Scan completed :
          Cell 01 - Address: 00:18:4D:4C:37:52
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=48/70  Signal level=-62 dBm  
                    Encryption key:on
                    ESSID:"Hansell"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000006f0707aac5
                    Extra: Last beacon: 1112ms ago
                    IE: Unknown: 000748616E73656C6C
                    IE: Unknown: 010882848B960C183048
                    IE: Unknown: 030102
                    IE: Unknown: 2A0100
                    IE: Unknown: 32041224606C
```

On unplugging and replugging device in SERVER

> [593-155212]  phy2 -> rt2500usb_init_eeprom : error - Invalid RT chipset detected.....     rt2xx00lib_probe_dev : error - failed to allocate device  This is a bit misleading tho' coz when I did the same unplug/replug routine on my desktop, it gave the same error message in tty1, but my wireless dongle works just fine.

On restarting networking (with Ethernet and wireless plugged in) - this message only relates to wireless.
> No DHCPOFFERS received.
No working leases in persisten database - sleeping.

DESKTOP SETUP - which works
```
$iwconfig wlan0
wlan0     IEEE 802.11bg  ESSID:"Hansell"  
          Mode:Managed  Frequency:2.417 GHz  Access Point: 00:18:4D:4C:37:52   
          Bit Rate=54 Mb/s   Tx-Power=7 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=34/70  Signal level=-76 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

$lsmod | grep rt
exportfs                3437  1 nfsd
rt73usb                22434  0 
crc_itu_t               1371  2 udf,rt73usb
rt2500usb              18141  0 
rt2x00usb               9703  2 rt73usb,rt2500usb
rt2x00lib              27541  3 rt73usb,rt2500usb,rt2x00usb
led_class               2864  1 rt2x00lib
mac80211              204922  2 rt2x00usb,rt2x00lib
cfg80211              126517  2 rt2x00lib,mac80211
parport_pc             26250  1 
agpgart                31788  2 nvidia,intel_agp
parport                32635  3 ppdev,parport_pc,lp

$lshw -C network
  *-network
       description: Ethernet interface
       product: 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:06:08.0
       logical name: eth0
       version: 01
       serial: 00:13:20:a2:f4:2f
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI firmware=N/A latency=32 maxlatency=56 mingnt=8 multicast=yes
       resources: irq:20 memory:f9002000-f9002fff ioport:bc00(size=64)
  *-network
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 94:0c:6d:e1:82:3c
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=10.0.0.6 multicast=yes wireless=IEEE 802.11bg

$iwlist wlan0 scan
wlan0     Scan completed :
          Cell 01 - Address: 00:18:4D:4C:37:52
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=46/70  Signal level=-64 dBm  
                    Encryption key:on
                    ESSID:"Hansell"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000064893104ee
                    Extra: Last beacon: 56ms ago
                    IE: Unknown: 000748616E73656C6C
                    IE: Unknown: 010882848B960C183048
                    IE: Unknown: 030102
                    IE: Unknown: 2A0100
                    IE: Unknown: 32041224606C
          Cell 02 - Address: 00:1F:FB:06:DD:EA
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"HAMED"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000001a811542f
                    Extra: Last beacon: 2188ms ago
                    IE: Unknown: 000548414D4544
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030109
                    IE: Unknown: 2A0104
                    IE: Unknown: 32040C183060
                    IE: Unknown: DD07000C4300000000
                    IE: Unknown: 0706545720010D10
          Cell 03 - Address: 00:1E:40:78:32:E1
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key:on
                    ESSID:"Kiatkat"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000074e9f1071
                    Extra: Last beacon: 1428ms ago
                    IE: Unknown: 00074B6961746B6174
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD060010180200F4

Upon unplugging and replugging in the TP-Link TL-WN321G Wireless Dongle

$dmesg | grep wlan0
[437406.576185] wlan0: deauthenticating from 00:18:4d:4c:37:52 by local choice (reason=3)
[437438.639927] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[437446.207600] wlan0: deauthenticating from 00:18:4d:4c:37:52 by local choice (reason=3)
[437446.210067] wlan0: direct probe to AP 00:18:4d:4c:37:52 (try 1)
[437446.212107] wlan0: direct probe responded
[437446.212116] wlan0: authenticate with AP 00:18:4d:4c:37:52 (try 1)
[437446.214100] wlan0: authenticated
[437446.214145] wlan0: associate with AP 00:18:4d:4c:37:52 (try 1)
[437446.216230] wlan0: RX AssocResp from 00:18:4d:4c:37:52 (capab=0x431 status=0 aid=1)
[437446.216238] wlan0: associated
[437446.230165] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[437456.896014] wlan0: no IPv6 routers present

$dmesg | grep rt73
[437438.399646] Registered led device: rt73usb-phy7::radio
[437438.399690] Registered led device: rt73usb-phy7::assoc
[437438.399733] Registered led device: rt73usb-phy7::quality
[437438.453062] rt73usb 2-2:1.0: firmware: requesting rt73.bin

```

SERVER SETUP - which doesn't
```
$iwconfig wlan0
wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=10 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on

$lsmod | grep rt          
rt73usb                22434  0 
crc_itu_t               1371  1 rt73usb
rt2500usb              18141  0 
rt2x00usb               9703  2 rt73usb,rt2500usb
rt2x00lib              27541  3 rt73usb,rt2500usb,rt2x00usb
led_class               2864  1 rt2x00lib
mac80211              204922  2 rt2x00usb,rt2x00lib
cfg80211              126517  2 rt2x00lib,mac80211
parport_pc             26250  1 
parport                32635  3 ppdev,lp,parport_pc
agpgart                31788  3 ttm,drm,intel_agp

lshw -C network
  *-network DISABLED
       description: Ethernet interface
       product: N10/ICH 7 Family LAN Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:05:08.0
       logical name: eth0
       version: 01
       serial: 00:13:20:da:3a:20
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=half firmware=N/A latency=32 link=no maxlatency=56 mingnt=8 multicast=yes port=MII speed=10MB/s
       resources: irq:20 memory:52000000-52000fff ioport:1000(size=64)
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 94:0c:6d:e1:b5:72
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg

$iwlist wlan0 scan
wlan0     Scan completed :
          Cell 01 - Address: 00:18:4D:4C:37:52
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=42/70  Signal level=-68 dBm  
                    Encryption key:on
                    ESSID:"Hansell"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000006512c66bf7
                    Extra: Last beacon: 1024ms ago
                    IE: Unknown: 000748616E73656C6C
                    IE: Unknown: 010882848B960C183048
                    IE: Unknown: 030102
                    IE: Unknown: 2A0100
                    IE: Unknown: 32041224606C
          Cell 02 - Address: 00:1F:FB:06:DD:EA
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"HAMED"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000231cd6ed1
                    Extra: Last beacon: 576ms ago
                    IE: Unknown: 000548414D4544
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030109
                    IE: Unknown: 2A0104
                    IE: Unknown: 32040C183060
                    IE: Unknown: DD07000C4300000000
                    IE: Unknown: 0706545720010D10

$dmesg | grep -i rt73

[   22.800930] Registered led device: rt73usb-phy1::radio
[   22.800968] Registered led device: rt73usb-phy1::assoc
[   22.801009] Registered led device: rt73usb-phy1::quality
[   22.801497] usbcore: registered new interface driver rt73usb
[   23.790315] rt73usb 1-4:1.0: firmware: requesting rt73.bin
```

---

### Post by lisati on 2010-06-24
Please do not start multiple threads on the same question.

It's OK to bump your threads if you haven't had a response 24 hours after the last post.

---

### Post by MartinHansell on 2010-06-24
Hi,

Yeah, sorry about that... I was trying to check if in fact my thread was a server question rather than wireless, but posted it into Security category by mistake.. hence the trail of posts...  I appreciate the protocol and am not trying to circumvent it.  Oh - got any clues as to my question ](*,)

---

### Post by MartinHansell on 2010-06-25
Bump - anyone?

---

### Post by r0b0t0 on 2010-08-07
hi martin!  i just bought a TL-WN321G for an imac using ubuntu server ppc 10.04, with the same results: no wifi.

after reading your post, i downloaded the live cd and wifi works out of the box!

so, while in live cd, i search for rt* files and replace all of them from the live cd file system to my hd filesystem

/lib/firmware/rt*
/lib/modules/2.6.32-21-powerpc/kernel/drivers/netwireless/rt2x00/rt*
/lib/modules/2.6.32-21-powerpc-smp/kernel/drivers/netwireless/rt2x00/rt*

the last one folder 2.6.32-21-powerpc-smp/kernel/drivers/netwireless/rt2x00 was not even created in my hd server installation. then reboot and now wifi works!

there must be something wrong with the ubuntu server drivers :P

---

