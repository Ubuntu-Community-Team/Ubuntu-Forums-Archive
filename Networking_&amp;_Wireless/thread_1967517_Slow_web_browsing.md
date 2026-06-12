---
title: "Slow web browsing"
date: 2012-04-28
forum: Networking &amp; Wireless
---

### Post by dpwilson on 2012-04-28
I have an ongoing problem.  I was using 10.04 when my issue first started.  Some webpages will not load, or load extremely slow.  This is primarily using firefox and chrome.  I also had 11.10 loaded and experienced the same problems.  Its not only that some pages load slowly, but also that some websites, will load, but clicking links on them will not.  I can load yahoo just fine, but clicking links on it, fail to load pages.  If I were to copy the link URL and open it with another browser, it will load  Several other websites are the same, but I yahoo is really bad about it. I just installed 12.04 and was hoping it would fix this issue, but not.  

If somebody can point me in the right direction, please do so. I use a mobile broadband for internet.  If I boot into windows, I dont experience this problem.

Any help or advice is very much appreciated. 

Not sure what more information is needed, but say the word, and I will post the outputs and hardware used.

---

### Post by dpwilson on 2012-04-29
bump

---

### Post by uylug on 2012-04-29
Could you run these comands and post the output here?

```
ping [www.google.com]("http://www.google.com/") -c 20
```

```
ifconfig
```

---

### Post by TBABill on 2012-04-29
Sounds a little like a DNS problem. Have you tried changing your DNS servers in network manager to open servers, such as 8.8.8.8 or 8.8.4.4?

---

### Post by dpwilson on 2012-04-30
Thanks for replying and helping.  I will try these when I get home this afternoon.

---

### Post by mörgæs on 2012-04-30
Please use a more informative thread title. 
Changed.

---

### Post by dpwilson on 2012-04-30
Here are the results, hope they can help make sense of this.  I will try changing the dns servers as well.  Got to get the young one to soccer practice for now.  Thanks for the help.

```
~$ ping www.google.com -c 20
PING www.l.google.com (173.194.73.105) 56(84) bytes of data.
64 bytes from vb-in-f105.1e100.net (173.194.73.105): icmp_req=1 ttl=48 time=117 ms
64 bytes from vb-in-f105.1e100.net (173.194.73.105): icmp_req=2 ttl=48 time=136 ms
64 bytes from vb-in-f105.1e100.net (173.194.73.105): icmp_req=3 ttl=48 time=117 ms
64 bytes from vb-in-f105.1e100.net (173.194.73.105): icmp_req=4 ttl=48 time=126 ms
64 bytes from vb-in-f105.1e100.net (173.194.73.105): icmp_req=5 ttl=48 time=615 ms
64 bytes from vb-in-f105.1e100.net (173.194.73.105): icmp_req=6 ttl=48 time=105 ms
64 bytes from vb-in-f105.1e100.net (173.194.73.105): icmp_req=7 ttl=48 time=134 ms
64 bytes from vb-in-f105.1e100.net (173.194.73.105): icmp_req=8 ttl=48 time=164 ms
64 bytes from vb-in-f105.1e100.net (173.194.73.105): icmp_req=9 ttl=48 time=126 ms
64 bytes from vb-in-f105.1e100.net (173.194.73.105): icmp_req=10 ttl=48 time=237 ms
64 bytes from vb-in-f105.1e100.net (173.194.73.105): icmp_req=11 ttl=48 time=130 ms
64 bytes from vb-in-f105.1e100.net (173.194.73.105): icmp_req=12 ttl=48 time=131 ms
64 bytes from vb-in-f105.1e100.net (173.194.73.105): icmp_req=13 ttl=48 time=128 ms
64 bytes from vb-in-f105.1e100.net (173.194.73.105): icmp_req=14 ttl=48 time=134 ms
64 bytes from vb-in-f105.1e100.net (173.194.73.105): icmp_req=15 ttl=48 time=308 ms
64 bytes from vb-in-f105.1e100.net (173.194.73.105): icmp_req=16 ttl=48 time=129 ms
64 bytes from vb-in-f105.1e100.net (173.194.73.105): icmp_req=17 ttl=48 time=124 ms
64 bytes from vb-in-f105.1e100.net (173.194.73.105): icmp_req=18 ttl=48 time=1531 ms
64 bytes from vb-in-f105.1e100.net (173.194.73.105): icmp_req=19 ttl=48 time=532 ms
64 bytes from vb-in-f105.1e100.net (173.194.73.105): icmp_req=20 ttl=48 time=128 ms

--- www.l.google.com ping statistics ---
20 packets transmitted, 20 received, 0% packet loss, time 19001ms
rtt min/avg/max/mdev = 105.865/258.133/1531.337/322.418 ms, pipe 2

```

```
~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:30:18:a9:01:f1  
          inet6 addr: fe80::230:18ff:fea9:1f1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3876 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:812869 (812.8 KB)
          Interrupt:43 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16456 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16456 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1568169 (1.5 MB)  TX bytes:1568169 (1.5 MB)

wlan0     Link encap:Ethernet  HWaddr 00:1a:ef:11:d5:59  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21a:efff:fe11:d559/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:680965 errors:0 dropped:5 overruns:0 frame:0
          TX packets:539788 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:766726137 (766.7 MB)  TX bytes:123362153 (123.3 MB)
```

---

### Post by dpwilson on 2012-05-01
I tried using different dns servers but no luck with that.  Still the same results when clicking on links.  I have to emphasize that I do not have this problem with every website.  It happens about 99% of the time with Yahoo and some others, while others I have no problem with.

One other issue and I am not sure if its related or not is that a times I lose my connection and it will not reconnect unless i reboot the mifi device.

---

### Post by dpwilson on 2012-05-01
Maybe this will help as well.

```
$ lspci
00:00.0 RAM memory: NVIDIA Corporation MCP61 Memory Controller (rev a1)
00:01.0 ISA bridge: NVIDIA Corporation MCP61 LPC Bridge (rev a2)
00:01.1 SMBus: NVIDIA Corporation MCP61 SMBus (rev a2)
00:01.2 RAM memory: NVIDIA Corporation MCP61 Memory Controller (rev a2)
00:02.0 USB controller: NVIDIA Corporation MCP61 USB 1.1 Controller (rev a3)
00:02.1 USB controller: NVIDIA Corporation MCP61 USB 2.0 Controller (rev a3)
00:04.0 PCI bridge: NVIDIA Corporation MCP61 PCI bridge (rev a1)
00:05.0 Audio device: NVIDIA Corporation MCP61 High Definition Audio (rev a2)
00:06.0 IDE interface: NVIDIA Corporation MCP61 IDE (rev a2)
00:08.0 IDE interface: NVIDIA Corporation MCP61 SATA Controller (rev a2)
00:08.1 IDE interface: NVIDIA Corporation MCP61 SATA Controller (rev a2)
00:09.0 PCI bridge: NVIDIA Corporation MCP61 PCI Express bridge (rev a2)
00:0b.0 PCI bridge: NVIDIA Corporation MCP61 PCI Express bridge (rev a2)
00:0c.0 PCI bridge: NVIDIA Corporation MCP61 PCI Express bridge (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:07.0 Network controller: Ralink corp. RT2561/RT61 802.11g PCI
02:00.0 VGA compatible controller: NVIDIA Corporation G98 [GeForce 8400 GS] (rev a1)
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)

```

```
$ iwconfig wlan0
wlan0     IEEE 802.11bg  ESSID:"MiFi2200 C124 Secure"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:26:E8:0E:C1:24   
          Bit Rate=48 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=50/70  Signal level=-60 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:4  Invalid misc:55   Missed beacon:0
```

---

### Post by dpwilson on 2012-05-01
```
lsmod
Module                  Size  Used by
nls_iso8859_1          12713  0 
nls_cp437              16991  0 
vfat                   17585  0 
fat                    61512  1 vfat
uas                    18027  0 
usb_storage            49198  1 
rfcomm                 47604  0 
bnep                   18281  2 
bluetooth             180104  10 rfcomm,bnep
usblp                  18307  0 
snd_hda_codec_realtek   223867  1 
nvidia              12319264  40 
snd_hda_intel          33773  3 
snd_hda_codec         127706  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                97188  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30748  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
arc4                   12529  2 
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
rt61pci                32257  0 
crc_itu_t              12707  1 rt61pci
rt2x00pci              14577  1 rt61pci
rt2x00lib              55301  2 rt61pci,rt2x00pci
mac80211              506816  2 rt2x00pci,rt2x00lib
cfg80211              205544  2 rt2x00lib,mac80211
snd                    78855  15 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
eeprom_93cx6           12725  1 rt61pci
soundcore              15091  1 snd
i2c_nforce2            13058  0 
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
edac_core              53746  0 
k8temp                 13057  0 
edac_mce_amd           23709  0 
psmouse                87603  0 
ppdev                  17113  0 
mac_hid                13253  0 
serio_raw              13211  0 
parport_pc             32866  1 
lp                     17799  0 
parport                46562  3 ppdev,parport_pc,lp
usbhid                 47199  0 
hid                    99559  1 usbhid
floppy                 70365  0 
sata_nv                32286  4 
r8169                  62099  0 
pata_amd               14118  1
```

---

### Post by hakermania on 2012-05-01
Can you post an example link which loads very slowly at your PC (so as to test it myself)?

Also, as I can see from the command ping [www.google.com]("http://www.google.com") -c 20, it's like something's wrong, did you notice that the time intervals between each packet differ very much? In my occassion the interval is ~65ms and never goes more than 80ms.
So, please check:
a) Are you sure another member isn't downloading stuff (or maybe even watching youtube videos, this makes slow connections go mad)
b) Double-check if someone other has access to your modem and downloads without your permission.

---

### Post by dpwilson on 2012-05-01
output from dmesg
```
[283596.539718] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[283596.539721] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[283596.539723] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[283596.539726] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[283596.539728] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[283596.539730] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[283596.539732] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[283596.539735] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[283596.539737] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[283596.539740] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[283596.539742] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[283596.539745] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[283596.539747] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[283596.539749] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[283596.539751] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[283596.539754] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[283596.539756] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[283596.539759] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[283596.539761] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[283596.539764] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[283596.539766] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[283596.539768] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[283596.539771] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[283596.539773] cfg80211: 2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[283596.539776] cfg80211: World regulatory domain updated:
[283596.539778] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[283596.539780] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[283596.539783] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[283596.539785] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[283596.539787] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[283596.539790] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[283597.760165] wlan0: authenticate with 00:26:e8:0e:c1:24 (try 1)
[283597.761615] wlan0: authenticated
[283597.761748] wlan0: associate with 00:26:e8:0e:c1:24 (try 1)
[283597.764517] wlan0: RX AssocResp from 00:26:e8:0e:c1:24 (capab=0x431 status=0 aid=3)
[283597.764524] wlan0: associated
[283598.055359] wlan0: deauthenticated from 00:26:e8:0e:c1:24 (Reason: 15)
[283598.057754] cfg80211: All devices are disconnected, going to restore regulatory settings
[283598.057769] cfg80211: Restoring regulatory settings
[283598.057778] cfg80211: Calling CRDA to update world regulatory domain
[283598.067977] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[283598.067988] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[283598.067995] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[283598.068053] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[283598.068059] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[283598.068066] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[283598.068071] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[283598.068078] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[283598.068083] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[283598.068090] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[283598.068095] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[283598.068102] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[283598.068107] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[283598.068114] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[283598.068119] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[283598.068126] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[283598.068131] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[283598.068138] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[283598.068143] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[283598.068150] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[283598.068155] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[283598.068162] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[283598.068167] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[283598.068174] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[283598.068179] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[283598.068186] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[283598.068192] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[283598.068198] cfg80211: 2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[283598.068205] cfg80211: World regulatory domain updated:
[283598.068209] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[283598.068216] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[283598.068223] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[283598.068234] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[283598.068245] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[283598.068256] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[283599.284215] wlan0: authenticate with 00:26:e8:0e:c1:24 (try 1)
[283599.285823] wlan0: authenticated
[283599.285965] wlan0: associate with 00:26:e8:0e:c1:24 (try 1)
[283599.289903] wlan0: RX AssocResp from 00:26:e8:0e:c1:24 (capab=0x431 status=0 aid=3)
[283599.289911] wlan0: associated
[283599.585480] wlan0: deauthenticated from 00:26:e8:0e:c1:24 (Reason: 15)
[283599.585854] cfg80211: All devices are disconnected, going to restore regulatory settings
[283599.585868] cfg80211: Restoring regulatory settings
[283599.585878] cfg80211: Calling CRDA to update world regulatory domain
[283599.596880] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[283599.596892] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[283599.596898] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[283599.596906] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[283599.596911] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[283599.596918] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[283599.596923] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[283599.596930] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[283599.596935] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[283599.596941] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[283599.596947] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[283599.596953] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[283599.596958] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[283599.596965] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[283599.596970] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[283599.596977] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[283599.596982] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[283599.596989] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[283599.596994] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[283599.597001] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[283599.597006] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[283599.597013] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[283599.597018] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[283599.597024] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[283599.597030] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[283599.597037] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[283599.597042] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[283599.597049] cfg80211: 2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[283599.597056] cfg80211: World regulatory domain updated:
[283599.597060] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[283599.597066] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[283599.597072] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[283599.597078] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[283599.597084] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[283599.597090] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[283600.812162] wlan0: authenticate with 00:26:e8:0e:c1:24 (try 1)
[283600.813594] wlan0: authenticated
[283600.813740] wlan0: associate with 00:26:e8:0e:c1:24 (try 1)
[283600.816558] wlan0: RX AssocResp from 00:26:e8:0e:c1:24 (capab=0x431 status=0 aid=3)
[283600.816568] wlan0: associated
[283601.115625] wlan0: deauthenticated from 00:26:e8:0e:c1:24 (Reason: 15)
[283601.116000] cfg80211: All devices are disconnected, going to restore regulatory settings
[283601.116050] cfg80211: Restoring regulatory settings
[283601.116059] cfg80211: Calling CRDA to update world regulatory domain
[283601.128441] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[283601.128452] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[283601.128458] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[283601.128465] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[283601.128471] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[283601.128477] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[283601.128483] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[283601.128489] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[283601.128495] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[283601.128501] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[283601.128506] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[283601.128513] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[283601.128518] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[283601.128525] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[283601.128530] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[283601.128536] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[283601.128542] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[283601.128548] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[283601.128554] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[283601.128560] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[283601.128565] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[283601.128572] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[283601.128577] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[283601.128584] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[283601.128589] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[283601.128596] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[283601.128601] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[283601.128608] cfg80211: 2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[283601.128615] cfg80211: World regulatory domain updated:
[283601.128619] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[283601.128625] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[283601.128631] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[283601.128636] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[283601.128642] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[283601.128648] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[283602.344554] wlan0: authenticate with 00:26:e8:0e:c1:24 (try 1)
[283602.345976] wlan0: authenticated
[283602.346115] wlan0: associate with 00:26:e8:0e:c1:24 (try 1)
[283602.348923] wlan0: RX AssocResp from 00:26:e8:0e:c1:24 (capab=0x431 status=0 aid=3)
[283602.348929] wlan0: associated
[283602.645711] wlan0: deauthenticated from 00:26:e8:0e:c1:24 (Reason: 15)
[283602.656316] cfg80211: All devices are disconnected, going to restore regulatory settings
[283602.656330] cfg80211: Restoring regulatory settings
[283602.656340] cfg80211: Calling CRDA to update world regulatory domain
[283602.666771] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[283602.666783] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[283602.666789] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[283602.666796] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[283602.666802] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[283602.666808] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[283602.666814] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[283602.666820] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[283602.666825] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[283602.666832] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[283602.666837] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[283602.666844] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[283602.666849] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[283602.666855] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[283602.666861] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[283602.666867] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[283602.666872] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[283602.666879] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[283602.666884] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[283602.666891] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[283602.666896] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[283602.666902] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[283602.666908] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[283602.666915] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[283602.666920] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[283602.666927] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[283602.666932] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[283602.666939] cfg80211: 2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[283602.666946] cfg80211: World regulatory domain updated:
[283602.666949] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[283602.666956] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[283602.666961] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[283602.666967] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[283602.666973] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[283602.666979] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[283603.884155] wlan0: authenticate with 00:26:e8:0e:c1:24 (try 1)
[283603.885713] wlan0: authenticated
[283603.885846] wlan0: associate with 00:26:e8:0e:c1:24 (try 1)
[283603.888632] wlan0: RX AssocResp from 00:26:e8:0e:c1:24 (capab=0x431 status=0 aid=3)
[283603.888639] wlan0: associated
[283604.185832] wlan0: deauthenticated from 00:26:e8:0e:c1:24 (Reason: 15)
[283604.186208] cfg80211: All devices are disconnected, going to restore regulatory settings
[283604.186222] cfg80211: Restoring regulatory settings
[283604.186232] cfg80211: Calling CRDA to update world regulatory domain
[283604.196391] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[283604.196402] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[283604.196408] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[283604.196415] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[283604.196421] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[283604.196427] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[283604.196433] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[283604.196439] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[283604.196444] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[283604.196451] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[283604.196456] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[283604.196463] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[283604.196468] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[283604.196475] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[283604.196480] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[283604.196486] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[283604.196492] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[283604.196498] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[283604.196503] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[283604.196510] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[283604.196515] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[283604.196522] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[283604.196527] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[283604.196534] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[283604.196539] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[283604.196546] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[283604.196551] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[283604.196557] cfg80211: 2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[283604.196565] cfg80211: World regulatory domain updated:
[283604.196569] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[283604.196575] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[283604.196581] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[283604.196587] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[283604.196592] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[283604.196598] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[283605.412228] wlan0: authenticate with 00:26:e8:0e:c1:24 (try 1)
[283605.413672] wlan0: authenticated
[283605.413798] wlan0: associate with 00:26:e8:0e:c1:24 (try 1)
[283605.416705] wlan0: RX AssocResp from 00:26:e8:0e:c1:24 (capab=0x431 status=0 aid=3)
[283605.416715] wlan0: associated
[283605.629275] wlan0: deauthenticating from 00:26:e8:0e:c1:24 by local choice (reason=3)
[283605.668099] cfg80211: All devices are disconnected, going to restore regulatory settings
[283605.668112] cfg80211: Restoring regulatory settings
[283605.668133] cfg80211: Calling CRDA to update world regulatory domain
[283605.678590] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[283605.678602] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[283605.678609] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[283605.678616] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[283605.678621] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[283605.678628] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[283605.678633] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[283605.678640] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[283605.678645] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[283605.678652] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[283605.678657] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[283605.678664] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[283605.678669] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[283605.678675] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[283605.678681] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[283605.678687] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[283605.678693] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[283605.678699] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[283605.678704] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[283605.678711] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[283605.678716] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[283605.678723] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[283605.678728] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[283605.678735] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[283605.678740] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[283605.678747] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[283605.678752] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[283605.678759] cfg80211: 2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[283605.678766] cfg80211: World regulatory domain updated:
[283605.678769] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[283605.678776] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[283605.678782] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[283605.678787] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[283605.678793] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[283605.678799] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[283737.937442] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[283738.009369] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[283738.233587] r8169 0000:04:00.0: eth0: link down
[283738.233601] r8169 0000:04:00.0: eth0: link down
[283738.235037] ADDRCONF(NETDEV_UP): eth0: link is not ready
[283738.605428] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[283739.817406] r8169 0000:04:00.0: eth0: link up
[283739.818641] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[283740.916389] wlan0: authenticate with 00:26:e8:0e:c1:24 (try 1)
[283740.917882] wlan0: authenticated
[283740.918009] wlan0: associate with 00:26:e8:0e:c1:24 (try 1)
[283740.920855] wlan0: RX AssocResp from 00:26:e8:0e:c1:24 (capab=0x431 status=0 aid=2)
[283740.920861] wlan0: associated
[283740.922633] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[283971.915500] wlan0: deauthenticating from 00:26:e8:0e:c1:24 by local choice (reason=3)
[283971.957406] cfg80211: All devices are disconnected, going to restore regulatory settings
[283971.957474] cfg80211: Restoring regulatory settings
[283971.957486] cfg80211: Calling CRDA to update world regulatory domain
[283971.967297] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[283971.967309] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[283971.967315] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[283971.967322] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[283971.967328] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[283971.967334] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[283971.967340] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[283971.967346] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[283971.967351] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[283971.967358] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[283971.967363] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[283971.967370] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[283971.967375] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[283971.967382] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[283971.967387] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[283971.967394] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[283971.967399] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[283971.967405] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[283971.967411] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[283971.967417] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[283971.967422] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[283971.967429] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[283971.967434] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[283971.967441] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[283971.967446] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[283971.967453] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[283971.967458] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[283971.967465] cfg80211: 2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[283971.967472] cfg80211: World regulatory domain updated:
[283971.967476] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[283971.967482] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[283971.967488] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[283971.967494] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[283971.967499] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[283971.967505] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[283972.021577] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[283974.393443] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[283974.477444] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[283974.701361] r8169 0000:04:00.0: eth0: link down
[283974.701383] r8169 0000:04:00.0: eth0: link down
[283974.702766] ADDRCONF(NETDEV_UP): eth0: link is not ready
[283975.021427] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[283976.313238] r8169 0000:04:00.0: eth0: link up
[283976.314466] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[283977.336199] wlan0: authenticate with 00:26:e8:0e:c1:24 (try 1)
[283977.337653] wlan0: authenticated
[283977.337788] wlan0: associate with 00:26:e8:0e:c1:24 (try 1)
[283977.340613] wlan0: RX AssocResp from 00:26:e8:0e:c1:24 (capab=0x431 status=0 aid=2)
[283977.340622] wlan0: associated
[283977.342403] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[284918.027940] wlan0: deauthenticated from 00:26:e8:0e:c1:24 (Reason: 2)
[284918.044183] cfg80211: All devices are disconnected, going to restore regulatory settings
[284918.044198] cfg80211: Restoring regulatory settings
[284918.044208] cfg80211: Calling CRDA to update world regulatory domain
[284918.100966] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[284918.100977] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[284918.100984] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[284918.100991] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[284918.100997] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[284918.101004] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[284918.101009] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[284918.101016] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[284918.101022] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[284918.101028] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[284918.101033] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[284918.101040] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[284918.101045] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[284918.101052] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[284918.101057] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[284918.101064] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[284918.101069] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[284918.101075] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[284918.101081] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[284918.101087] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[284918.101093] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[284918.101099] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[284918.101104] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[284918.101111] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[284918.101116] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[284918.101123] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[284918.101128] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[284918.101135] cfg80211: 2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[284918.101142] cfg80211: World regulatory domain updated:
[284918.101146] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[284918.101152] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[284918.101158] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[284918.101163] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[284918.101169] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[284918.101175] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[284919.272197] wlan0: authenticate with 00:26:e8:0e:c1:24 (try 1)
[284919.273641] wlan0: authenticated
[284919.273702] wlan0: associate with 00:26:e8:0e:c1:24 (try 1)
[284919.276586] wlan0: RX AssocResp from 00:26:e8:0e:c1:24 (capab=0x431 status=0 aid=2)
[284919.276592] wlan0: associated
[284920.779489] wlan0: deauthenticating from 00:26:e8:0e:c1:24 by local choice (reason=3)
[284920.824276] cfg80211: All devices are disconnected, going to restore regulatory settings
[284920.824303] cfg80211: Restoring regulatory settings
[284920.824314] cfg80211: Calling CRDA to update world regulatory domain
[284920.834097] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[284920.834109] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[284920.834115] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[284920.834122] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[284920.834128] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[284920.834134] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[284920.834140] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[284920.834147] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[284920.834152] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[284920.834159] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[284920.834164] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[284920.834171] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[284920.834176] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[284920.834183] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[284920.834188] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[284920.834194] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[284920.834200] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[284920.834206] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[284920.834212] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[284920.834218] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[284920.834223] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[284920.834230] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[284920.834235] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[284920.834242] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[284920.834247] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[284920.834254] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[284920.834259] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[284920.834266] cfg80211: 2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[284920.834273] cfg80211: World regulatory domain updated:
[284920.834277] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[284920.834283] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[284920.834289] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[284920.834295] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[284920.834301] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[284920.834307] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[284920.889546] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[284922.076202] wlan0: authenticate with 00:26:e8:0e:c1:24 (try 1)
[284922.077657] wlan0: authenticated
[284922.077717] wlan0: associate with 00:26:e8:0e:c1:24 (try 1)
[284922.080559] wlan0: RX AssocResp from 00:26:e8:0e:c1:24 (capab=0x431 status=0 aid=2)
[284922.080566] wlan0: associated
[284922.082273] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[284924.964374] wlan0: deauthenticating from 00:26:e8:0e:c1:24 by local choice (reason=3)
[284925.016303] cfg80211: All devices are disconnected, going to restore regulatory settings
[284925.016320] cfg80211: Restoring regulatory settings
[284925.016374] cfg80211: Calling CRDA to update world regulatory domain
[284925.026701] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[284925.026712] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[284925.026719] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[284925.026726] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[284925.026732] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[284925.026739] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[284925.026744] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[284925.026751] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[284925.026756] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[284925.026763] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[284925.026768] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[284925.026774] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[284925.026779] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[284925.026786] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[284925.026791] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[284925.026798] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[284925.026803] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[284925.026809] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[284925.026815] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[284925.026821] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[284925.026827] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[284925.026833] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[284925.026839] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[284925.026845] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[284925.026850] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[284925.026857] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[284925.026862] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[284925.026869] cfg80211: 2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[284925.026875] cfg80211: World regulatory domain updated:
[284925.026879] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[284925.026885] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[284925.026891] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[284925.026897] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[284925.026903] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[284925.026909] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[284925.111279] r8169 0000:04:00.0: eth0: link down
[284925.111302] r8169 0000:04:00.0: eth0: link down
[284925.112778] ADDRCONF(NETDEV_UP): eth0: link is not ready
[284926.702657] r8169 0000:04:00.0: eth0: link up
[284926.703888] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[325342.313441] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[325342.389434] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[325346.628465] r8169 0000:04:00.0: eth0: link down
[325346.628488] r8169 0000:04:00.0: eth0: link down
[325346.629875] ADDRCONF(NETDEV_UP): eth0: link is not ready
[325348.216932] r8169 0000:04:00.0: eth0: link up
[325348.218152] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[325350.985442] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[325353.292162] wlan0: authenticate with 00:26:e8:0e:c1:24 (try 1)
[325353.293602] wlan0: authenticated
[325353.293745] wlan0: associate with 00:26:e8:0e:c1:24 (try 1)
[325353.296556] wlan0: RX AssocResp from 00:26:e8:0e:c1:24 (capab=0x431 status=0 aid=3)
[325353.296563] wlan0: associated
[325353.298262] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready

```

---

### Post by dpwilson on 2012-05-01
Here are just a few links from yahoo news that I cannot get to load.  It just hangs there trying to load, never actually leaving the main page.

[http://www.yahoo.com/_ylt=AuChOPySxEYE9ZG4Q0GIWzebvZx4;_ylu=X3oDMTYyMXFnbTFkBGEDMTMgeWVhcnMgb2YgcGVyZmVjdCBhdHRlbmRhbmNlOiBzdHVkZW50IG5lYXJzIDIsMDAwIGRheXMgaW4gYSByb3cEY2NvZGUDcHpidWFsbGNhaDUEY3BvcwMyBGcDaWQtMjI2Mjk1MARpbnRsA3VzBG1jb2RlA3B6YnVhbGxjYWg1BG1wb3MDMgRwa2d0AzIEcG9zAzEEc2VjA3RkLW53cwRzbGsDdGl0bGUEdGVzdAM3MDEEd29lAzEyNzY3MTM3/SIG=13n9pge7s/EXP=1336005055/**http%3A//news.yahoo.com/blogs/sideshow/13-years-perfect-attendance-student-nears-2-000-221116269.html]("http://www.yahoo.com/_ylt=AuChOPySxEYE9ZG4Q0GIWzebvZx4;_ylu=X3oDMTYyMXFnbTFkBGEDMTMgeWVhcnMgb2YgcGVyZmVjdCBhdHRlbmRhbmNlOiBzdHVkZW50IG5lYXJzIDIsMDAwIGRheXMgaW4gYSByb3cEY2NvZGUDcHpidWFsbGNhaDUEY3BvcwMyBGcDaWQtMjI2Mjk1MARpbnRsA3VzBG1jb2RlA3B6YnVhbGxjYWg1BG1wb3MDMgRwa2d0AzIEcG9zAzEEc2VjA3RkLW53cwRzbGsDdGl0bGUEdGVzdAM3MDEEd29lAzEyNzY3MTM3/SIG=13n9pge7s/EXP=1336005055/**http%3A//news.yahoo.com/blogs/sideshow/13-years-perfect-attendance-student-nears-2-000-221116269.html")

This link actually left the main page, but never loaded the story, just a blank page.
[http://news.yahoo.com/blogs/technology-blog/pick-tablet-personality-193650669.html]("http://news.yahoo.com/blogs/technology-blog/pick-tablet-personality-193650669.html")

This [http://news.yahoo.com/video]("http://news.yahoo.com/video")took me to the page, and after about 5 minutes the video did load, but clicking links within the page did nothing.

---

### Post by dpwilson on 2012-05-02
These are ping results from windows laptop using the same mifi.  Laptop boots to Ubuntu 10.04 by default.  I used windows to run this and compare results, which are pretty similar to my desktop with ubuntu 12.04.  It is rare that both computers are on at the same time, so results are typical of normal use.  There is not much change when both are online at the same time.  

I tried to go to yahoo while using windows and get the same results as using my ubuntu, so maybe this is more of a problem with ntelos wireless than ubuntu which I first thought.  I will continue to look into this as possible issues for either.  I do not normally use windows so I will try it again later and see if results are the same.  Until then, any suggestions that I can try to narrow this down?

```

C:\Users\wilson>ping www.google.com -n 20

Pinging www.l.google.com [173.194.73.105] with 32 bytes of data:
Reply from 173.194.73.105: bytes=32 time=135ms TTL=48
Reply from 173.194.73.105: bytes=32 time=137ms TTL=48
Reply from 173.194.73.105: bytes=32 time=143ms TTL=48
Reply from 173.194.73.105: bytes=32 time=146ms TTL=48
Reply from 173.194.73.105: bytes=32 time=140ms TTL=48
Reply from 173.194.73.105: bytes=32 time=185ms TTL=48
Reply from 173.194.73.105: bytes=32 time=174ms TTL=48
Reply from 173.194.73.105: bytes=32 time=141ms TTL=48
Reply from 173.194.73.105: bytes=32 time=143ms TTL=48
Reply from 173.194.73.105: bytes=32 time=140ms TTL=48
Reply from 173.194.73.105: bytes=32 time=142ms TTL=48
Reply from 173.194.73.105: bytes=32 time=216ms TTL=48
Reply from 173.194.73.105: bytes=32 time=141ms TTL=48
Reply from 173.194.73.105: bytes=32 time=147ms TTL=48
Reply from 173.194.73.105: bytes=32 time=142ms TTL=48
Reply from 173.194.73.105: bytes=32 time=140ms TTL=48
Reply from 173.194.73.105: bytes=32 time=272ms TTL=48
Reply from 173.194.73.105: bytes=32 time=160ms TTL=48
Reply from 173.194.73.105: bytes=32 time=227ms TTL=48
Reply from 173.194.73.105: bytes=32 time=138ms TTL=48

Ping statistics for 173.194.73.105:
    Packets: Sent = 20, Received = 20, Lost = 0 (0% loss),
Approximate round trip times in milli-seconds:
    Minimum = 135ms, Maximum = 272ms, Average = 160ms

C:\Users\wilson>^A
```

---

