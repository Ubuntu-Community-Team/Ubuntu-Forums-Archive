---
title: "wireless problems: Slow/No Connectivity"
date: 2009-05-17
forum: Networking &amp; Wireless
---

### Post by maskedhedgehog on 2009-05-17
Hi all,

I'm having wireless connectivity problems with my netbook. The connection alternates between being fine (short periods) and no connectivity (longer periods), resulting in upwards of 70% packet loss over a prolonged period of time.

These problems only occur with the Ubuntu Netbook Remix install. The seperate WinXP install has no wireless connectivity issues. The problem is also just with wireless, as a wired connection does not display any packetloss.

I'm using network-manager, but I've also tried wicd with no improvement. The channel being used by the router also does not seem to matter, (I've tried 1 through 11.)

The only thing that I can see that seems off in any of the settings (full output below):
                    IE: IEEE 802.11i/WPA2 Version 1 (from iwlist)
 

 The network I'm using is 802.11bgn, not 802.11i. I can't seem to find this setting anywhere else though. I'm trying to use 802.11n, or g in the worst case.
 

  
Router: Dlink DIR-655
Netbook: Asus EeePC 1000HE
Dual-Booting UNR Jaunty (2.6.28-11-generic) and WinXP
Driver: Ath9k

ifconfig wlan0
```

wlan0     Link encap:Ethernet  HWaddr 00:22:43:77:4a:34   
            inet addr:192.168.0.198  Bcast:192.168.0.255  Mask:255.255.255.0 
            inet6 addr: fe80::222:43ff:fe77:4a34/64 Scope:Link 
            UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
            RX packets:11492 errors:0 dropped:0 overruns:0 frame:0 
            TX packets:8897 errors:0 dropped:0 overruns:0 carrier:0 
            collisions:0 txqueuelen:1000  
            RX bytes:13632811 (13.6 MB)  TX bytes:1665099 (1.6 MB) 
 
```iwlist:
```
wlan0     Scan completed :
            Cell 01 - Address: 00:22:B0:B8:25:55
                      ESSID:"Minerva"
                      Mode:Master
                      Channel:2
                      Frequency:2.417 GHz (Channel 2)
                      Quality=109/100  Signal level:-48 dBm  Noise level=-118 dBm
                      Encryption key:on
                      IE: Unknown: 00074D696E65727661
                      IE: Unknown: 010482848B96
                      IE: Unknown: 030102
                      IE: Unknown: 2A0100
                      IE: Unknown: 32088C129824B048606C
                      IE: IEEE 802.11i/WPA2 Version 1
                          Group Cipher : TKIP
                          Pairwise Ciphers (2) : TKIP CCMP
                          Authentication Suites (1) : PSK
                      IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                      IE: Unknown: 2D1A4E101BFFFF000000000000000000000000000000000000000000
                      IE: Unknown: 3D160205190000000F000000000000000000000000000000
                      IE: Unknown: DD1E00904C336E101BFFFF000000000000000000000000000000000000000000
                      IE: Unknown: DD1A00904C340205010000000F000000000000000000000000000000
   IE: Unknown: DD7F0050F204104A0001101044000102103B0001031047001061FEC6A4CD43372F847957878F39E85A1021000E442D4C696E6B2053797374656D73102300074449522D363535102400024134104200046E6F6E651054000800060050F204000110110017587472656D65204E204749474142495420526F75746572100800020084
                       Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                                9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                                48 Mb/s; 54 Mb/s
                      Extra:tsf=000000009197e180
                      Extra: Last beacon: 68ms ago
 
```lshw:
  
 ```
    
             *-network
                  description: Wireless interface
                  product: AR928X Wireless Network Adapter (PCI-Express)
                  vendor: Atheros Communications Inc.
                  physical id: 0
                  bus info: pci@0000:01:00.0
                  logical name: wmaster0
                  version: 01
                  serial: 00:22:43:77:4a:34
                  width: 64 bits
                  clock: 33MHz
                  capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
                  configuration: broadcast=yes driver=ath9k ip=192.168.0.198 latency=0 module=ath9k multicast=yes wireless=IEEE 802.11bgn
 
```lsmod:
 ```
    ath9k                 263224  0  
  mac80211              217208  1 ath9k 
  led_class              12036  1 ath9k 
 
```  Dmesg:
 ```
[   12.617502] ath9k: 0.1
[   12.617906] ath9k 0000:01:00.0: enabling device (0000 -> 0002)
[   12.617924] ath9k 0000:01:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[   12.617949] ath9k 0000:01:00.0: setting latency timer to 64
[   12.961526] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   12.961627] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   13.063825] phy0: Selected rate control algorithm 'ath9k_rate_control'
[   13.076242] psmouse serio1: ID: 10 00 64<6>Registered led device: ath9k-phy0:radio
[   13.192374] Registered led device: ath9k-phy0:assoc
[   13.192463] Registered led device: ath9k-phy0:tx
[   13.192552] Registered led device: ath9k-phy0:rx
[   13.193414] phy0: Atheros 9280: mem=0xf7fe0000, irq=19
[   13.273221] elantech.c: assuming hardware version 2, firmware version 2.48
[   13.347038] elantech.c: Synaptics capabilities query result 0x00, 0x02, 0x64.
[   13.432436] lp: driver loaded but no devices found
[   13.564754] input: ETPS/2 Elantech Touchpad as /devices/platform/i8042/serio1/input/input10
[   13.614473] Adding 1461904k swap on /dev/sda2.  Priority:-1 extents:1 across:1461904k
[   14.190754] EXT3 FS on sda3, internal journal
[   15.674507] type=1505 audit(1242596262.239:2): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=2061
[   15.674776] type=1505 audit(1242596262.239:3): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=2061
[   15.674887] type=1505 audit(1242596262.239:4): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=2061
[   15.674981] type=1505 audit(1242596262.239:5): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=2061
[   15.979260] type=1505 audit(1242596262.543:6): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=2066
[   15.979667] type=1505 audit(1242596262.543:7): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=2066
[   16.043784] type=1505 audit(1242596262.607:8): operation="profile_load" name="/usr/sbin/mysqld" name2="default" pid=2070
[   16.103260] type=1505 audit(1242596262.667:9): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=2074
[   23.679427] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   23.679435] Bluetooth: BNEP filters: protocol multicast
[   23.699838] Bridge firewalling registered
[   25.398256] ppdev: user-space parallel port driver
[   26.387679] [drm] Initialized drm 1.1.0 20060810
[   26.417622] pci 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   26.417634] pci 0000:00:02.0: setting latency timer to 64
[   26.418021] [drm] Initialized i915 1.6.0 20080730 on minor 0
[   26.423085] [drm:i915_setparam] *ERROR* unknown parameter 4
[   26.423153] [drm:i915_getparam] *ERROR* Unknown parameter 6
[   27.642562] [drm:i915_getparam] *ERROR* Unknown parameter 6
[   29.435981] ATL1E 0000:03:00.0: irq 2300 for MSI/MSI-X
[   29.436749] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   29.454839] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  125.809459] [drm:i915_getparam] *ERROR* Unknown parameter 6
[  127.721903] [drm:i915_getparam] *ERROR* Unknown parameter 6
[  129.712920] wlan0: authenticate with AP 00:22:b0:b8:25:55
[  129.714364] wlan0: authenticated
[  129.714377] wlan0: associate with AP 00:22:b0:b8:25:55
[  129.717920] wlan0: RX AssocResp from 00:22:b0:b8:25:55 (capab=0x431 status=0 aid=1)
[  129.717930] wlan0: associated
[  129.733830] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  132.846406] padlock: VIA PadLock not detected.
[  140.588067] wlan0: no IPv6 routers present
[  950.182580] ATL1E 0000:03:00.0: ATL1E: eth0 NIC Link is Up<100 Mbps Full Duplex>
[  950.183121] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  960.752050] eth0: no IPv6 routers present
```

---

### Post by Neil_Bell on 2009-05-18
Your not going to like the answer to this but here goes. From what I have read Network Manager is losing connection when it does a scan of the network every 120 seconds or so.So i'm getting  "wlan0: beacon loss from AP" repeatedly in dmesg plus you can watch the network drop off to nothing. A lot of folks have suggested going to wicd plus using the linux-backports-module. I have not found a working solution to this problem yet as niether of these options worked for me. I have the same card.
Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)

I have swapped to wicd which I think is a better manager anyway and the problem improved but did now clear it up i was still having disconnection issues or limited or no connectivity. tried the backport with no change. Also have compiled the drivers from compat-wireless. The stable one makes no difference and the bleeding edge I haven't been able to test as it errors on a key.c file compiling MAC80211.

I had no issues under 8.10 with this driver but since switching it has been a nightmare. Stalls a lot on large file transfers. Will kill my torrent client stone dead which makes getting an interim distro a pain. Only thing i can say i like is that my scp speeds doubled when they manage to stay connected and copy.You can try these suggestion it has worked for some just not myself.
dmesg
[16394.785056] wlan0: beacon loss from AP f62726b8 - sending probe request
[16396.784205] wlan0: no probe response from AP f62726b8 - disassociating
[16398.116071] wlan0: authenticate with AP f62726b8
[16398.125581] wlan0: authenticate with AP f62726b8
[16398.128579] wlan0: authenticated
[16398.128584] wlan0: associate with AP f62726b8
[16398.133554] wlan0: RX ReassocResp from f2f3802a (capab=0x411 status=0 aid=1)
[16398.133561] wlan0: associated
[16514.786090] wlan0: beacon loss from AP f62726b8 - sending probe request
continueous issue ^^


iwconfig ** bitrate = 0 isn't right**
wlan0     IEEE 802.11bgn  ESSID:"POS"  
          Mode:Managed  Frequency:2.437 GHz  Access Point:
          00:21:29:9B:B1:6E   
          Bit Rate=0 kb/s   Tx-Power=20 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=58/70  Signal level=-52 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by superprash2003 on 2009-05-18
could be related to this [http://ubuntuforums.org/showthread.php?t=1146367](http://ubuntuforums.org/showthread.php?t=1146367)

---

### Post by Neil_Bell on 2009-05-18
some of the symptoms seem the same however I haven't booted windows or had it on anything I've owned in years and the original poster hasn't indicated he is a dual boot setup. None of these issues were present in Hardy and the hardware hasn't changed as it is a laptop. I have moved to wicd this morning. I gave network manager the night but when it disconnects it may or may not reconnect. Wicd reconnects on it own but it is still the same issues. Connection sits at 80+% then it will drop to the 20+% and disconnect. Almost a yoyo effect. It is also very easy to crash it early by transfering anything large, torrent clients running full out or scp to the server will kill the connection.

Really I'm at a loss but I'm not the only one. One other trick I've seen is an issue with bluetooth and wifi coexisting so you can try. 
sudo modprobe ath9k btcoex_enable=1

Just figured I'd get all the info in one thread for him as I've been googling this to death since I moved to Jaunty. :)

---

### Post by maskedhedgehog on 2009-05-18
Hi Neil,

Thanks for the information!

I've posted a bug report on this. There are several other reports open involving the ath9k driver, but no existing bug report quite fit what I'm experiencing. Here is the url:
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/378156](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/378156)

The current setup does dual-boot with winXP, and there are no connectivity issues with XP.

Wicd didn't help me either. The backports module also didn't help too much. My best guess at this point is that there is some bug in the driver which doesn't play well with 802.11g/n and WPA1/2.

At this point, I'm contemplating a usb wifi adapter, as a netbook without the net is kind of silly.

---

### Post by Neil_Bell on 2009-05-18
yeah I'm at the same point I've seen several of the complaints where a few of the symptoms are similar but the solutions are all over the map and none has fixed the problem to date. It would seem to be the maturity level of the driver but there are obviously differences in the newer kernel causing part of the problem as sidux gave me the same headaches, Backtrack as well. I'll add what i can to the bug report see if any info i can grab will help as tripping over cat5e is driving me nuts.

---

### Post by eznet on 2009-05-28
Although the 'me-toos' don't really progress the matter, I wanted to toss my name in the hat - I am experiencing the same issues on my 1000HE.  

Things are lightning fast in XP, but not so much in Ubuntu.  I can connect to my wireless network just about every time I try, but the signal is always exceptionally low. The network responds in a tolerable manner, but still at about 1/2 the speed as in XP - this also varies, as although it is usually tolerable, it does drop to a snails pace at times. 

I cannot help but wonder if the issue relates to WPA (AES) - when I remove WPA from my AP, speeds seem to really pick up... 

-Matt

---

