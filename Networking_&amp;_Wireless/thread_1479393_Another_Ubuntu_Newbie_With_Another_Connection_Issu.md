---
title: "Another Ubuntu Newbie With Another Connection Issue – PLEASE HELP!"
date: 2010-05-10
forum: Networking &amp; Wireless
---

### Post by mike068 on 2010-05-10
Hello everyone I am new  here and somewhat new to Ubuntu so Thank You in advance for any help I may receive.   	 	 	 	 	Also I am sorry for this post because I know his is a ongoing issue and there is a ton of posts on this subject but I have not found a thread that is close to my system specs so pleas bear with me as I am relatively new to the Linux OS but I already like it much more than Windows OS's and I use it most of the time now even with the connection issue so here goes it. 

 I have an intermittent connection problem, it disconnect and reconnects about every 5-10 minutes and sometimes to be slow even when just browsing the web. I am running a dual-boot system and have no problems with the windows os connection. I have tried reconfiguring my router a couple of times from No security at all, it will disconnect and then I have to manually reconnect each time it disconnects. I set it up on WPA / TKIP + AES then it still disconnects but it reconnects automatically. And I have then set it to WAP 2 / AES and that makes no difference as the WAP setup. I have included below some of the information I have come across in other posts I have read so I hope this helps or let me know what other info I need to provide. As I said before I am new to Linux so please be descriptive I can fix most issues with windows with no problems but this it totally different, much better but different.


   	 	 	 	 	 	  System Info
 

 Acer Aspire 5570z
 Intel CPU T2082 1.73 duo-core
 1 gig mem
 Atheros AR5007EG wireless network adapter / Driver ath5k
 

 Dual Boot Setup 
 Win Xp Pro  
 Ubuntu 10.04  / 2.6.32-22-generic / Gnome 2.30.0
 

 Internet Connection Info
 

 Time Warner Cable + Cable Modem
 Router Linksys WRT54GS &#8211; V7
 Interface 802.11 WiFi (wlan0)
 Security WPA2/AES  
 MTU Auto
 Speed 1 mb/s &#8211; 48mb/s (keeps changing between these two speeds but the monitor states a 100% connection)
 Also Note: I am using the standard network connection manager that install with Ubuntu
 

 Additional Info


   	 	 	 	 	 	  :~$ ifconfig 
 eth0       Link encap:Ethernet  HWaddr 00:1b:24:43:f7:68   
           UP BROADCAST MULTICAST  MTU:1500  Metric:1 
           RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
           TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
           collisions:0 txqueuelen:1000  
           RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 

   	 	 	 	 	 	  Interrupt:16 



   	 	 	 	 	 	  lo  Link encap:Local Loopback   
           inet addr:127.0.0.1  Mask:255.0.0.0 
           inet6 addr: ::1/128 Scope:Host 
           UP LOOPBACK RUNNING  MTU:16436  Metric:1 
           RX packets:24 errors:0 dropped:0 overruns:0 frame:0 
           TX packets:24 errors:0 dropped:0 overruns:0 carrier:0 
           collisions:0 txqueuelen:0  
           RX bytes:1696 (1.6 KB)  TX bytes:1696 (1.6 KB) 
 

   	 	 	 	 	 	  wlan0      Link encap:Ethernet  HWaddr 00:19:7e:80:b2:66   
           inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0 
           inet6 addr: fe80::219:7eff:fe80:b266/64 Scope:Link 
           UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
           RX packets:506 errors:0 dropped:0 overruns:0 frame:0 
           TX packets:547 errors:0 dropped:0 overruns:0 carrier:0 
           collisions:0 txqueuelen:1000  
           RX bytes:383625 (383.6 KB)  TX bytes:84333 (84.3 KB)


   	 	 	 	 	 	  :~$ ping localhost 
 PING localhost (127.0.0.1) 56(84) bytes of data. 
 64 bytes from localhost (127.0.0.1): icmp_seq=1 ttl=64 time=0.049 ms 
 64 bytes from localhost (127.0.0.1): icmp_seq=2 ttl=64 time=0.042 ms 
 64 bytes from localhost (127.0.0.1): icmp_seq=3 ttl=64 time=0.043 ms 
 64 bytes from localhost (127.0.0.1): icmp_seq=4 ttl=64 time=0.042 ms 
 64 bytes from localhost (127.0.0.1): icmp_seq=5 ttl=64 time=0.044 ms 
 64 bytes from localhost (127.0.0.1): icmp_seq=6 ttl=64 time=0.045 ms 
 64 bytes from localhost (127.0.0.1): icmp_seq=7 ttl=64 time=0.045 ms 
 64 bytes from localhost (127.0.0.1): icmp_seq=8 ttl=64 time=0.043 ms 
 64 bytes from localhost (127.0.0.1): icmp_seq=9 ttl=64 time=0.044 ms 
 64 bytes from localhost (127.0.0.1): icmp_seq=10 ttl=64 time=0.047 ms 
 64 bytes from localhost (127.0.0.1): icmp_seq=11 ttl=64 time=0.045 ms 
 64 bytes from localhost (127.0.0.1): icmp_seq=12 ttl=64 time=0.044 ms 
 64 bytes from localhost (127.0.0.1): icmp_seq=13 ttl=64 time=0.045 ms 
 64 bytes from localhost (127.0.0.1): icmp_seq=14 ttl=64 time=0.042 ms 
 64 bytes from localhost (127.0.0.1): icmp_seq=15 ttl=64 time=0.045 ms 
 
 

   	 	 	 	 	 	  :~$ ping 192.168.1.1 -c 1 -s 1400 -M do 
 PING 192.168.1.1 (192.168.1.1) 1400(1428) bytes of data. 
 1408 bytes from 192.168.1.1: icmp_seq=1 ttl=64 time=2.30 ms 
  
 

--- 192.168.1.1 ping statistics --- 
 1 packets transmitted, 1 received, 0% packet loss, time 0ms 
 rtt min/avg/max/mdev = 2.307/2.307/2.307/0.000 ms 
 

   	 	 	 	 	 	  :~$ ping 192.168.1.1 -c 1 -s 1501 -M do 
 PING 192.168.1.1 (192.168.1.1) 1501(1529) bytes of data. 
 From 192.168.1.100 icmp_seq=1 Frag needed and DF set (mtu = 1500) 
  
 

--- 192.168.1.1 ping statistics --- 
 0 packets transmitted, 0 received, +1 errors

---

### Post by chili555 on 2010-05-10
We need the gruesome details, please:

[http://ubuntuforums.org/showthread.php?p=6183681](http://ubuntuforums.org/showthread.php?p=6183681)

---

### Post by mike068 on 2010-05-10
> **chili555 said:**
> We need the gruesome details, please:

[http://ubuntuforums.org/showthread.php?p=6183681](http://ubuntuforums.org/showthread.php?p=6183681)

Yes sorry something messed up when I posted but I have fixed it

---

### Post by chili555 on 2010-05-10
Please try a temporary fix:```
sudo rmmod -f ath5k
sudo modprobe ath5k nohwcrypt=1
```If it works, we can write one file to memorialize it forever.

---

### Post by mike068 on 2010-05-10
> **chili555 said:**
> Please try a temporary fix:```
sudo rmmod -f ath5k
sudo modprobe ath5k nohwcrypt=1
```If it works, we can write one file to memorialize it forever.
 
I will try it now and let you know the results in a little while after giving it an ample test

---

### Post by mike068 on 2010-05-10
**Chili555**

Well maybe its me me but it seems to be a tad bit better since I was able to download the complete Ubuntu 10.04 ISO file with out getting disconnected which is better than it was but the problem is still not cured. It stayed connected 25-30 minutes before I disconnected.

BTW Thank You for the help please keep it coming.

---

### Post by mike068 on 2010-05-12
Dose anyone else have any ideas that could help me?

---

### Post by acreech on 2010-06-07
> **chili555 said:**
> Please try a temporary fix:```
sudo rmmod -f ath5k
sudo modprobe ath5k nohwcrypt=1
```If it works, we can write one file to memorialize it forever.

I have been haivng problems with my wireless, ever since upgrading to Lucid. I have searched the forums, but like others, halve not found a solution yet for the problem. The problems did not exist with Karmic. The problem that I am having is that the wireless connection disconnects constantly. I have installed Wicd. This does not make the connection more stable, but it does automatically try to reconnect, where as Network Manager would not automatically attempt to reconnect. 

I have an Atheros AR5001 Wireless Network Adapter. I have also seen it reffered to as an "Atheros ar5007eg". I found a thread that suggested running these commands for a temporary fix. 

```

sudo rmmod -f ath5k
sudo modprobe ath5k nohwcrypt=1

```

So far this seems to be working. I don't understand what the commands did or how to make that a more permanent fix (I am assuming that upon a restart the problems will be back). I also don't understand what changed between the last version and the current version of Ubuntu to create this connection issue. I have listed information below about my system, which should help with any diagnoses or solutions. 

Thanks for your help. 

acreech



1) Machine Brand and Model (PC/Laptop):

```

Acer Aspire 7520-5185
AMD Athlon 64 Dual Core Processor
NVIDIA GeForce 7000M Turbo Cache
3 GB DDR2
802.11 b/g WLAN

```
 
2) Wireless Brand, Model and Wireless Chipset:

```

lspci

00:00.0 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
00:01.0 ISA bridge: nVidia Corporation MCP67 ISA Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP67 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
00:01.3 Co-processor: nVidia Corporation MCP67 Co-processor (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:04.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:04.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP67 IDE Controller (rev a1)
00:07.0 Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1)
00:08.0 PCI bridge: nVidia Corporation MCP67 PCI Bridge (rev a2)
00:09.0 IDE interface: nVidia Corporation MCP67 AHCI Controller (rev a2)
00:0a.0 Ethernet controller: nVidia Corporation MCP67 Ethernet (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:0d.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:12.0 VGA compatible controller: nVidia Corporation C67 [GeForce 7000M / nForce 610M] (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:04.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
01:04.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
01:04.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
01:04.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
01:04.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
05:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)

```

```

lspci

00:00.0 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
00:01.0 ISA bridge: nVidia Corporation MCP67 ISA Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP67 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
00:01.3 Co-processor: nVidia Corporation MCP67 Co-processor (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:04.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:04.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP67 IDE Controller (rev a1)
00:07.0 Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1)
00:08.0 PCI bridge: nVidia Corporation MCP67 PCI Bridge (rev a2)
00:09.0 IDE interface: nVidia Corporation MCP67 AHCI Controller (rev a2)
00:0a.0 Ethernet controller: nVidia Corporation MCP67 Ethernet (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:0d.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:12.0 VGA compatible controller: nVidia Corporation C67 [GeForce 7000M / nForce 610M] (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:04.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
01:04.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
01:04.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
01:04.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
01:04.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
05:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)
acreech@acreech-laptop:~$ lsusb
Bus 004 Device 002: ID 046d:c062 Logitech, Inc. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 064e:a101 Suyin Corp. Acer CrystalEye Webcam
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

```

lspci -nn | grep Atheros
05:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR5001 Wireless Network Adapter [168c:001c] (rev 01)

```

3) Check interface:

```

ifconfig

eth0      Link encap:Ethernet  HWaddr 00:1b:38:c8:1c:d2  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:6501 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4888 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5480815 (5.4 MB)  TX bytes:805655 (805.6 KB)
          Interrupt:27 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:33055 errors:0 dropped:0 overruns:0 frame:0
          TX packets:33055 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:12097145 (12.0 MB)  TX bytes:12097145 (12.0 MB)

wlan0     Link encap:Ethernet  HWaddr 00:1f:3a:04:bd:7a  
          inet addr:192.168.0.64  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:3aff:fe04:bd7a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5262 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4027 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3879411 (3.8 MB)  TX bytes:637556 (637.5 KB)

```

```

iwconfig wlan0

wlan0     IEEE 802.11bg  ESSID:"AKAA"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:1A:C4:F0:E5:71   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-32 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

4) Check for modules:

```

lsmod

Module                  Size  Used by
ath5k                 134140  0 
binfmt_misc             7960  1 
ppdev                   6375  0 
vboxdrv              1768311  0 
snd_hda_codec_realtek   278890  1 
joydev                 11072  0 
arc4                    1473  2 
snd_hda_intel          25645  2 
snd_hda_codec          85727  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               6924  1 snd_hda_codec
snd_pcm_oss            41394  0 
snd_mixer_oss          16299  1 snd_pcm_oss
snd_pcm                87850  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1782  0 
snd_seq_oss            31219  0 
snd_seq_midi            5829  0 
snd_rawmidi            23388  1 snd_seq_midi
snd_seq_midi_event      7267  2 snd_seq_oss,snd_seq_midi
snd_seq                57417  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23553  2 snd_pcm,snd_seq
snd_seq_device          6824  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    70978  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
mac80211              243373  1 ath5k
ath                    10345  1 ath5k
uvcvideo               62403  0 
fbcon                  39270  71 
tileblit                2487  1 fbcon
font                    8053  1 fbcon
bitblit                 5811  1 fbcon
softcursor              1565  1 bitblit
ricoh_mmc               3416  0 
sdhci_pci               6700  0 
sdhci                  17928  1 sdhci_pci
videodev               40486  1 uvcvideo
v4l1_compat            15495  2 uvcvideo,videodev
v4l2_compat_ioctl32    12020  1 videodev
acer_wmi               15829  0 
edac_core              45423  0 
edac_mce_amd            9214  0 
cfg80211              152987  3 ath5k,mac80211,ath
led_class               3732  3 ath5k,sdhci,acer_wmi
psmouse                64608  0 
serio_raw               4918  0 
nvidia              10799466  41 
vga16fb                12757  1 
vgastate                9857  1 vga16fb
i2c_nforce2             6099  0 
soundcore               8052  1 snd
snd_page_alloc          8500  2 snd_hda_intel,snd_pcm
k8temp                  3912  0 
lirc_ene0100            7532  0 
lirc_dev               11302  1 lirc_ene0100
video                  20623  0 
output                  2503  1 video
lp                      9336  0 
parport                37160  2 ppdev,lp
usbhid                 40988  0 
hid                    83376  1 usbhid
ohci1394               30260  0 
ahci                   37646  6 
pata_amd               11962  0 
ieee1394               94675  1 ohci1394
forcedeth              55592  0 


lsmod | grep ath5k

ath5k                 134140  0 
mac80211              243373  1 ath5k
ath                    10345  1 ath5k
cfg80211              152987  3 ath5k,mac80211,ath
led_class               3732  3 ath5k,sdhci,acer_wmi

```

5) Kernel boot messages

```

dmesg

[   60.368766] wlan0: associate with AP 00:1a:c4:f0:e5:71 (try 1)
[   60.370665] wlan0: RX AssocResp from 00:1a:c4:f0:e5:71 (capab=0x431 status=0 aid=1)
[   60.370671] wlan0: associated
[   60.382583] wlan0: deauthenticating from 00:1a:c4:f0:e5:71 by local choice (reason=3)
[   60.765482] wlan0: direct probe to AP 00:1a:c4:f0:e5:71 (try 1)
[   60.767118] wlan0: direct probe responded
[   60.767123] wlan0: authenticate with AP 00:1a:c4:f0:e5:71 (try 1)
[   60.768772] wlan0: authenticated
[   60.773792] wlan0: associate with AP 00:1a:c4:f0:e5:71 (try 1)
[   60.775418] wlan0: RX AssocResp from 00:1a:c4:f0:e5:71 (capab=0x431 status=0 aid=1)
[   60.775424] wlan0: associated
[   60.802590] wlan0: deauthenticating from 00:1a:c4:f0:e5:71 by local choice (reason=3)
[   61.185498] wlan0: direct probe to AP 00:1a:c4:f0:e5:71 (try 1)
[   61.188352] wlan0: direct probe responded
[   61.188362] wlan0: authenticate with AP 00:1a:c4:f0:e5:71 (try 1)
[   61.190269] wlan0: authenticated
[   61.190303] wlan0: associate with AP 00:1a:c4:f0:e5:71 (try 1)
[   61.192331] wlan0: RX AssocResp from 00:1a:c4:f0:e5:71 (capab=0x431 status=0 aid=1)
[   61.192336] wlan0: associated
[   61.222577] wlan0: deauthenticating from 00:1a:c4:f0:e5:71 by local choice (reason=3)
[   61.605447] wlan0: direct probe to AP 00:1a:c4:f0:e5:71 (try 1)
[   61.607094] wlan0: direct probe responded
[   61.607103] wlan0: authenticate with AP 00:1a:c4:f0:e5:71 (try 1)
[   61.608605] wlan0: authenticated
[   61.608641] wlan0: associate with AP 00:1a:c4:f0:e5:71 (try 1)
[   61.610518] wlan0: RX AssocResp from 00:1a:c4:f0:e5:71 (capab=0x431 status=0 aid=1)
[   61.610524] wlan0: associated
[   64.630389] wlan0: deauthenticated from 00:1a:c4:f0:e5:71 (Reason: 2)
[   65.790804] wlan0: direct probe to AP 00:1a:c4:f0:e5:71 (try 1)
[   65.793010] wlan0: direct probe responded
[   65.793015] wlan0: authenticate with AP 00:1a:c4:f0:e5:71 (try 1)
[   65.795001] wlan0: authenticated
[   65.795054] wlan0: associate with AP 00:1a:c4:f0:e5:71 (try 1)
[   65.796766] wlan0: RX AssocResp from 00:1a:c4:f0:e5:71 (capab=0x431 status=0 aid=1)
[   65.796770] wlan0: associated
[   68.820672] wlan0: deauthenticated from 00:1a:c4:f0:e5:71 (Reason: 2)
[   69.976252] wlan0: direct probe to AP 00:1a:c4:f0:e5:71 (try 1)
[   69.977909] wlan0: direct probe responded
[   69.977917] wlan0: authenticate with AP 00:1a:c4:f0:e5:71 (try 1)
[   69.979425] wlan0: authenticated
[   69.979454] wlan0: associate with AP 00:1a:c4:f0:e5:71 (try 1)
[   69.982188] wlan0: RX AssocResp from 00:1a:c4:f0:e5:71 (capab=0x431 status=0 aid=1)
[   69.982191] wlan0: associated
[   73.006836] wlan0: deauthenticated from 00:1a:c4:f0:e5:71 (Reason: 2)
[   73.836387] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   74.009268] forcedeth 0000:00:0a.0: irq 27 for MSI/MSI-X
[   74.009480] eth0: no link during initialization.
[   74.010753] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   78.646408] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   79.686272] wlan0: direct probe to AP 00:1a:c4:f0:e5:71 (try 1)
[   79.688602] wlan0: direct probe responded
[   79.688611] wlan0: authenticate with AP 00:1a:c4:f0:e5:71 (try 1)
[   79.690797] wlan0: authenticated
[   79.690849] wlan0: associate with AP 00:1a:c4:f0:e5:71 (try 1)
[   79.692858] wlan0: RX AssocResp from 00:1a:c4:f0:e5:71 (capab=0x431 status=0 aid=1)
[   79.692864] wlan0: associated
[   79.694134] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   79.912558] wlan0: deauthenticating from 00:1a:c4:f0:e5:71 by local choice (reason=3)
[   80.056370] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   80.168575] forcedeth 0000:00:0a.0: irq 27 for MSI/MSI-X
[   80.168782] eth0: no link during initialization.
[   80.169861] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   80.336357] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   82.612956] wlan0: direct probe to AP 00:1a:c4:f0:e5:71 (try 1)
[   82.614598] wlan0: direct probe responded
[   82.614602] wlan0: authenticate with AP 00:1a:c4:f0:e5:71 (try 1)
[   82.616100] wlan0: authenticated
[   82.616123] wlan0: associate with AP 00:1a:c4:f0:e5:71 (try 1)
[   82.617973] wlan0: RX AssocResp from 00:1a:c4:f0:e5:71 (capab=0x431 status=0 aid=1)
[   82.617976] wlan0: associated
[   82.619184] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   86.510042] Clocksource tsc unstable (delta = -272483014 ns)
[   92.670196] wlan0: deauthenticating from 00:1a:c4:f0:e5:71 by local choice (reason=3)
[   93.053128] wlan0: direct probe to AP 00:1a:c4:f0:e5:71 (try 1)
[   93.054837] wlan0: direct probe responded
[   93.054846] wlan0: authenticate with AP 00:1a:c4:f0:e5:71 (try 1)
[   93.056344] wlan0: authenticated
[   93.056395] wlan0: associate with AP 00:1a:c4:f0:e5:71 (try 1)
[   93.058273] wlan0: RX AssocResp from 00:1a:c4:f0:e5:71 (capab=0x431 status=0 aid=1)
[   93.058280] wlan0: associated
[   93.360067] wlan0: no IPv6 routers present
[   96.072729] wlan0: deauthenticated from 00:1a:c4:f0:e5:71 (Reason: 2)
[   97.319845] wlan0: direct probe to AP 00:1a:c4:f0:e5:71 (try 1)
[   97.321621] wlan0: direct probe responded
[   97.321641] wlan0: authenticate with AP 00:1a:c4:f0:e5:71 (try 1)
[   97.323256] wlan0: authenticated
[   97.323335] wlan0: associate with AP 00:1a:c4:f0:e5:71 (try 1)
[   97.326760] wlan0: RX AssocResp from 00:1a:c4:f0:e5:71 (capab=0x431 status=0 aid=1)
[   97.326774] wlan0: associated
[  107.970243] wlan0: deauthenticating from 00:1a:c4:f0:e5:71 by local choice (reason=3)
[  108.383403] wlan0: direct probe to AP 00:1a:c4:f0:e5:71 (try 1)
[  108.385063] wlan0: direct probe responded
[  108.385067] wlan0: authenticate with AP 00:1a:c4:f0:e5:71 (try 1)
[  108.387199] wlan0: authenticated
[  108.387244] wlan0: associate with AP 00:1a:c4:f0:e5:71 (try 1)
[  108.392161] wlan0: RX AssocResp from 00:1a:c4:f0:e5:71 (capab=0x431 status=0 aid=1)
[  108.392168] wlan0: associated
[  111.411796] wlan0: deauthenticated from 00:1a:c4:f0:e5:71 (Reason: 2)
[  112.624367] wlan0: direct probe to AP 00:1a:c4:f0:e5:71 (try 1)
[  112.628152] wlan0: direct probe responded
[  112.628171] wlan0: authenticate with AP 00:1a:c4:f0:e5:71 (try 1)
[  112.630134] wlan0: authenticated
[  112.630212] wlan0: associate with AP 00:1a:c4:f0:e5:71 (try 1)
[  112.632086] wlan0: RX AssocResp from 00:1a:c4:f0:e5:71 (capab=0x431 status=0 aid=1)
[  112.632094] wlan0: associated
[  115.652453] wlan0: deauthenticated from 00:1a:c4:f0:e5:71 (Reason: 2)
[  116.827489] wlan0: direct probe to AP 00:1a:c4:f0:e5:71 (try 1)
[  116.829221] wlan0: direct probe responded
[  116.829238] wlan0: authenticate with AP 00:1a:c4:f0:e5:71 (try 1)
[  116.830621] wlan0: authenticated
[  116.830674] wlan0: associate with AP 00:1a:c4:f0:e5:71 (try 1)
[  116.832466] wlan0: RX AssocResp from 00:1a:c4:f0:e5:71 (capab=0x431 status=0 aid=1)
[  116.832474] wlan0: associated
[  126.890158] wlan0: deauthenticating from 00:1a:c4:f0:e5:71 by local choice (reason=3)
[  127.425130] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  127.638001] forcedeth 0000:00:0a.0: irq 27 for MSI/MSI-X
[  127.638233] eth0: no link during initialization.
[  127.640612] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  132.255140] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  132.443096] wlan0: direct probe to AP 00:1a:c4:f0:e5:71 (try 1)
[  132.445147] wlan0: direct probe responded
[  132.445162] wlan0: authenticate with AP 00:1a:c4:f0:e5:71 (try 1)
[  132.447619] wlan0: authenticated
[  132.447694] wlan0: associate with AP 00:1a:c4:f0:e5:71 (try 1)
[  132.451097] wlan0: RX AssocResp from 00:1a:c4:f0:e5:71 (capab=0x431 status=0 aid=1)
[  132.451109] wlan0: associated
[  132.453836] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  142.180225] wlan0: deauthenticating from 00:1a:c4:f0:e5:71 by local choice (reason=3)
[  142.354902] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  142.527503] forcedeth 0000:00:0a.0: irq 27 for MSI/MSI-X
[  142.527736] eth0: no link during initialization.
[  142.529892] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  142.727707] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  145.064741] wlan0: direct probe to AP 00:1a:c4:f0:e5:71 (try 1)
[  145.066431] wlan0: direct probe responded
[  145.066441] wlan0: authenticate with AP 00:1a:c4:f0:e5:71 (try 1)
[  145.067905] wlan0: authenticated
[  145.170588] wlan0: associate with AP 00:1a:c4:f0:e5:71 (try 1)
[  145.172265] wlan0: RX AssocResp from 00:1a:c4:f0:e5:71 (capab=0x431 status=0 aid=1)
[  145.172274] wlan0: associated
[  145.174865] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  155.210199] wlan0: deauthenticating from 00:1a:c4:f0:e5:71 by local choice (reason=3)
[  155.510035] wlan0: no IPv6 routers present
[  156.376635] wlan0: direct probe to AP 00:1a:c4:f0:e5:71 (try 1)
[  156.379037] wlan0: direct probe responded
[  156.379048] wlan0: authenticate with AP 00:1a:c4:f0:e5:71 (try 1)
[  156.380905] wlan0: authenticated
[  156.380967] wlan0: associate with AP 00:1a:c4:f0:e5:71 (try 1)
[  156.382937] wlan0: RX AssocResp from 00:1a:c4:f0:e5:71 (capab=0x431 status=0 aid=1)
[  156.382958] wlan0: associated
[  166.420189] wlan0: deauthenticating from 00:1a:c4:f0:e5:71 by local choice (reason=3)
[  166.803123] wlan0: direct probe to AP 00:1a:c4:f0:e5:71 (try 1)
[  166.804942] wlan0: direct probe responded
[  166.804961] wlan0: authenticate with AP 00:1a:c4:f0:e5:71 (try 1)
[  166.808113] wlan0: authenticated
[  166.808201] wlan0: associate with AP 00:1a:c4:f0:e5:71 (try 1)
[  166.809907] wlan0: RX AssocResp from 00:1a:c4:f0:e5:71 (capab=0x431 status=0 aid=1)
[  166.809918] wlan0: associated
[  176.870177] wlan0: deauthenticating from 00:1a:c4:f0:e5:71 by local choice (reason=3)
[  177.363494] wlan0: direct probe to AP 00:1a:c4:f0:e5:71 (try 1)
[  177.365292] wlan0: direct probe responded
[  177.365307] wlan0: authenticate with AP 00:1a:c4:f0:e5:71 (try 1)
[  177.366688] wlan0: authenticated
[  177.366766] wlan0: associate with AP 00:1a:c4:f0:e5:71 (try 1)
[  177.368792] wlan0: RX AssocResp from 00:1a:c4:f0:e5:71 (capab=0x431 status=0 aid=1)
[  177.368804] wlan0: associated
[  187.480223] wlan0: deauthenticating from 00:1a:c4:f0:e5:71 by local choice (reason=3)
[  188.363804] wlan0: direct probe to AP 00:1a:c4:f0:e5:71 (try 1)
[  188.365547] wlan0: direct probe responded
[  188.365566] wlan0: authenticate with AP 00:1a:c4:f0:e5:71 (try 1)
[  188.368055] wlan0: authenticated
[  188.368145] wlan0: associate with AP 00:1a:c4:f0:e5:71 (try 1)
[  188.371509] wlan0: RX AssocResp from 00:1a:c4:f0:e5:71 (capab=0x431 status=0 aid=1)
[  188.371520] wlan0: associated
[  188.652629] wlan0: deauthenticating from 00:1a:c4:f0:e5:71 by local choice (reason=3)
[  188.797423] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  189.067176] forcedeth 0000:00:0a.0: irq 27 for MSI/MSI-X
[  189.067406] eth0: no link during initialization.
[  189.069506] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  189.197659] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  190.304848] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  190.487092] forcedeth 0000:00:0a.0: irq 27 for MSI/MSI-X
[  190.487324] eth0: no link during initialization.
[  190.489816] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  191.724229] wlan0: direct probe to AP 00:1a:c4:f0:e5:71 (try 1)
[  191.725910] wlan0: direct probe responded
[  191.725920] wlan0: authenticate with AP 00:1a:c4:f0:e5:71 (try 1)
[  191.727417] wlan0: authenticated
[  191.727470] wlan0: associate with AP 00:1a:c4:f0:e5:71 (try 1)
[  191.729350] wlan0: RX AssocResp from 00:1a:c4:f0:e5:71 (capab=0x431 status=0 aid=1)
[  191.729356] wlan0: associated
[  191.732231] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  201.800145] wlan0: deauthenticating from 00:1a:c4:f0:e5:71 by local choice (reason=3)
[  202.193518] wlan0: direct probe to AP 00:1a:c4:f0:e5:71 (try 1)
[  202.196278] wlan0: direct probe responded
[  202.196296] wlan0: authenticate with AP 00:1a:c4:f0:e5:71 (try 1)
[  202.197565] wlan0: authenticated
[  202.197637] wlan0: associate with AP 00:1a:c4:f0:e5:71 (try 1)
[  202.199515] wlan0: RX AssocResp from 00:1a:c4:f0:e5:71 (capab=0x431 status=0 aid=1)
[  202.199527] wlan0: associated
[  202.380050] wlan0: no IPv6 routers present
[  212.232701] wlan0: deauthenticating from 00:1a:c4:f0:e5:71 by local choice (reason=3)
[  212.662985] wlan0: direct probe to AP 00:1a:c4:f0:e5:71 (try 1)
[  212.666020] wlan0: direct probe responded
[  212.666030] wlan0: authenticate with AP 00:1a:c4:f0:e5:71 (try 1)
[  212.667286] wlan0: authenticated
[  212.667314] wlan0: associate with AP 00:1a:c4:f0:e5:71 (try 1)
[  212.669243] wlan0: RX AssocResp from 00:1a:c4:f0:e5:71 (capab=0x431 status=0 aid=1)
[  212.669246] wlan0: associated
[  214.100179] wlan0: deauthenticating from 00:1a:c4:f0:e5:71 by local choice (reason=3)
[  214.504622] wlan0: direct probe to AP 00:1a:c4:f0:e5:71 (try 1)
[  214.506816] wlan0: direct probe responded
[  214.506832] wlan0: authenticate with AP 00:1a:c4:f0:e5:71 (try 1)
[  214.508346] wlan0: authenticated
[  214.508401] wlan0: associate with AP 00:1a:c4:f0:e5:71 (try 1)
[  214.511005] wlan0: RX AssocResp from 00:1a:c4:f0:e5:71 (capab=0x431 status=0 aid=1)
[  214.511013] wlan0: associated
[  217.536448] wlan0: deauthenticated from 00:1a:c4:f0:e5:71 (Reason: 2)
[  218.724813] wlan0: direct probe to AP 00:1a:c4:f0:e5:71 (try 1)
[  218.726543] wlan0: direct probe responded
[  218.726551] wlan0: authenticate with AP 00:1a:c4:f0:e5:71 (try 1)
[  218.728437] wlan0: authenticated
[  218.728500] wlan0: associate with AP 00:1a:c4:f0:e5:71 (try 1)
[  218.730194] wlan0: RX AssocResp from 00:1a:c4:f0:e5:71 (capab=0x431 status=0 aid=1)
[  218.730201] wlan0: associated
[  228.780231] wlan0: deauthenticating from 00:1a:c4:f0:e5:71 by local choice (reason=3)
[  229.163050] wlan0: direct probe to AP 00:1a:c4:f0:e5:71 (try 1)
[  229.165010] wlan0: direct probe responded
[  229.165019] wlan0: authenticate with AP 00:1a:c4:f0:e5:71 (try 1)
[  229.166729] wlan0: authenticated
[  229.166779] wlan0: associate with AP 00:1a:c4:f0:e5:71 (try 1)
[  229.168663] wlan0: RX AssocResp from 00:1a:c4:f0:e5:71 (capab=0x431 status=0 aid=1)
[  229.168670] wlan0: associated
[  239.230165] wlan0: deauthenticating from 00:1a:c4:f0:e5:71 by local choice (reason=3)
[  239.615202] wlan0: direct probe to AP 00:1a:c4:f0:e5:71 (try 1)
[  239.617449] wlan0: direct probe responded
[  239.617466] wlan0: authenticate with AP 00:1a:c4:f0:e5:71 (try 1)
[  239.619575] wlan0: authenticated
[  239.620999] wlan0: associate with AP 00:1a:c4:f0:e5:71 (try 1)
[  239.622939] wlan0: RX AssocResp from 00:1a:c4:f0:e5:71 (capab=0x431 status=0 aid=1)
[  239.622951] wlan0: associated
[  242.646845] wlan0: deauthenticated from 00:1a:c4:f0:e5:71 (Reason: 2)
[  243.836110] wlan0: direct probe to AP 00:1a:c4:f0:e5:71 (try 1)
[  243.837882] wlan0: direct probe responded
[  243.837901] wlan0: authenticate with AP 00:1a:c4:f0:e5:71 (try 1)
[  243.840124] wlan0: authenticated
[  243.840903] wlan0: associate with AP 00:1a:c4:f0:e5:71 (try 1)
[  243.842829] wlan0: RX AssocResp from 00:1a:c4:f0:e5:71 (capab=0x431 status=0 aid=1)
[  243.842838] wlan0: associated
[  253.930200] wlan0: deauthenticating from 00:1a:c4:f0:e5:71 by local choice (reason=3)
[  255.173799] wlan0: direct probe to AP 00:1a:c4:f0:e5:71 (try 1)
[  255.177383] wlan0: direct probe responded
[  255.177401] wlan0: authenticate with AP 00:1a:c4:f0:e5:71 (try 1)
[  255.178621] wlan0: authenticated
[  255.178683] wlan0: associate with AP 00:1a:c4:f0:e5:71 (try 1)
[  255.181083] wlan0: RX AssocResp from 00:1a:c4:f0:e5:71 (capab=0x431 status=0 aid=1)
[  255.181093] wlan0: associated
[  258.200062] wlan0: deauthenticated from 00:1a:c4:f0:e5:71 (Reason: 2)
[  259.376124] wlan0: direct probe to AP 00:1a:c4:f0:e5:71 (try 1)
[  259.378721] wlan0: direct probe responded
[  259.378740] wlan0: authenticate with AP 00:1a:c4:f0:e5:71 (try 1)
[  259.382107] wlan0: authenticated
[  259.382191] wlan0: associate with AP 00:1a:c4:f0:e5:71 (try 1)
[  259.384378] wlan0: RX AssocResp from 00:1a:c4:f0:e5:71 (capab=0x431 status=0 aid=1)
[  259.384388] wlan0: associated
[  269.460214] wlan0: deauthenticating from 00:1a:c4:f0:e5:71 by local choice (reason=3)
[  269.845609] wlan0: direct probe to AP 00:1a:c4:f0:e5:71 (try 1)
[  269.847301] wlan0: direct probe responded
[  269.847317] wlan0: authenticate with AP 00:1a:c4:f0:e5:71 (try 1)
[  269.848844] wlan0: authenticated
[  269.848917] wlan0: associate with AP 00:1a:c4:f0:e5:71 (try 1)
[  269.854027] wlan0: RX AssocResp from 00:1a:c4:f0:e5:71 (capab=0x431 status=0 aid=1)
[  269.854039] wlan0: associated
[  272.872214] wlan0: deauthenticated from 00:1a:c4:f0:e5:71 (Reason: 2)
[  274.174103] wlan0: direct probe to AP 00:1a:c4:f0:e5:71 (try 1)
[  274.176262] wlan0: direct probe responded
[  274.176281] wlan0: authenticate with AP 00:1a:c4:f0:e5:71 (try 1)
[  274.177553] wlan0: authenticated
[  274.177624] wlan0: associate with AP 00:1a:c4:f0:e5:71 (try 1)
[  274.181811] wlan0: RX AssocResp from 00:1a:c4:f0:e5:71 (capab=0x431 status=0 aid=1)
[  274.181824] wlan0: associated
[  284.240202] wlan0: deauthenticating from 00:1a:c4:f0:e5:71 by local choice (reason=3)
[  284.624893] wlan0: direct probe to AP 00:1a:c4:f0:e5:71 (try 1)
[  284.627330] wlan0: direct probe responded
[  284.627348] wlan0: authenticate with AP 00:1a:c4:f0:e5:71 (try 1)
[  284.629132] wlan0: authenticated
[  284.629229] wlan0: associate with AP 00:1a:c4:f0:e5:71 (try 1)
[  284.631180] wlan0: RX AssocResp from 00:1a:c4:f0:e5:71 (capab=0x431 status=0 aid=1)
[  284.631192] wlan0: associated
[  294.700166] wlan0: deauthenticating from 00:1a:c4:f0:e5:71 by local choice (reason=3)
[  295.823527] wlan0: direct probe to AP 00:1a:c4:f0:e5:71 (try 1)
[  295.827590] wlan0: direct probe responded
[  295.827625] wlan0: authenticate with AP 00:1a:c4:f0:e5:71 (try 1)
[  295.828903] wlan0: authenticated
[  295.829014] wlan0: associate with AP 00:1a:c4:f0:e5:71 (try 1)
[  295.832340] wlan0: RX AssocResp from 00:1a:c4:f0:e5:71 (capab=0x431 status=0 aid=1)
[  295.832352] wlan0: associated
[  305.920202] wlan0: deauthenticating from 00:1a:c4:f0:e5:71 by local choice (reason=3)
[  306.487832] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  306.699017] forcedeth 0000:00:0a.0: irq 27 for MSI/MSI-X
[  306.699249] eth0: no link during initialization.
[  306.701440] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  311.255272] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  311.635607] wlan0: direct probe to AP 00:1a:c4:f0:e5:71 (try 1)
[  311.637274] wlan0: direct probe responded
[  311.637283] wlan0: authenticate with AP 00:1a:c4:f0:e5:71 (try 1)
[  311.638752] wlan0: authenticated
[  311.638808] wlan0: associate with AP 00:1a:c4:f0:e5:71 (try 1)
[  311.640631] wlan0: RX AssocResp from 00:1a:c4:f0:e5:71 (capab=0x431 status=0 aid=1)
[  311.640638] wlan0: associated
[  311.643221] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  315.352625] wlan0: deauthenticating from 00:1a:c4:f0:e5:71 by local choice (reason=3)
[  315.750301] wlan0: direct probe to AP 00:1a:c4:f0:e5:71 (try 1)
[  315.751993] wlan0: direct probe responded
[  315.752001] wlan0: authenticate with AP 00:1a:c4:f0:e5:71 (try 1)
[  315.753797] wlan0: authenticated
[  315.753832] wlan0: associate with AP 00:1a:c4:f0:e5:71 (try 1)
[  315.755754] wlan0: RX AssocResp from 00:1a:c4:f0:e5:71 (capab=0x431 status=0 aid=1)
[  315.755759] wlan0: associated
[  321.240220] wlan0: deauthenticating from 00:1a:c4:f0:e5:71 by local choice (reason=3)
[  321.408985] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  321.588454] forcedeth 0000:00:0a.0: irq 27 for MSI/MSI-X
[  321.588702] eth0: no link during initialization.
[  321.590735] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  321.787347] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  324.173162] wlan0: direct probe to AP 00:1a:c4:f0:e5:71 (try 1)
[  324.174967] wlan0: direct probe responded
[  324.174975] wlan0: authenticate with AP 00:1a:c4:f0:e5:71 (try 1)
[  324.177350] wlan0: authenticated
[  324.177394] wlan0: associate with AP 00:1a:c4:f0:e5:71 (try 1)
[  324.179692] wlan0: RX AssocResp from 00:1a:c4:f0:e5:71 (capab=0x431 status=0 aid=1)
[  324.179698] wlan0: associated
[  324.181060] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  334.220168] wlan0: deauthenticating from 00:1a:c4:f0:e5:71 by local choice (reason=3)
[  334.603086] wlan0: direct probe to AP 00:1a:c4:f0:e5:71 (try 1)
[  334.604944] wlan0: direct probe responded
[  334.604952] wlan0: authenticate with AP 00:1a:c4:f0:e5:71 (try 1)
[  334.606734] wlan0: authenticated
[  334.606786] wlan0: associate with AP 00:1a:c4:f0:e5:71 (try 1)
[  334.608645] wlan0: RX AssocResp from 00:1a:c4:f0:e5:71 (capab=0x431 status=0 aid=1)
[  334.608651] wlan0: associated
[  334.700052] wlan0: no IPv6 routers present
[  344.710199] wlan0: deauthenticating from 00:1a:c4:f0:e5:71 by local choice (reason=3)
[  345.093122] wlan0: direct probe to AP 00:1a:c4:f0:e5:71 (try 1)
[  345.095047] wlan0: direct probe responded
[  345.095056] wlan0: authenticate with AP 00:1a:c4:f0:e5:71 (try 1)
[  345.096781] wlan0: authenticated
[  345.173822] wlan0: associate with AP 00:1a:c4:f0:e5:71 (try 1)
[  345.175557] wlan0: RX AssocResp from 00:1a:c4:f0:e5:71 (capab=0x431 status=0 aid=1)
[  345.175568] wlan0: associated
[  346.082611] wlan0: deauthenticating from 00:1a:c4:f0:e5:71 by local choice (reason=3)
[  346.483098] wlan0: direct probe to AP 00:1a:c4:f0:e5:71 (try 1)
[  346.484814] wlan0: direct probe responded
[  346.484828] wlan0: authenticate with AP 00:1a:c4:f0:e5:71 (try 1)
[  346.486277] wlan0: authenticated
[  346.486334] wlan0: associate with AP 00:1a:c4:f0:e5:71 (try 1)
[  346.488189] wlan0: RX AssocResp from 00:1a:c4:f0:e5:71 (capab=0x431 status=0 aid=1)
[  346.488195] wlan0: associated
[  349.512047] wlan0: deauthenticated from 00:1a:c4:f0:e5:71 (Reason: 2)
[  350.725707] wlan0: direct probe to AP 00:1a:c4:f0:e5:71 (try 1)
[  350.728164] wlan0: direct probe responded
[  350.728179] wlan0: authenticate with AP 00:1a:c4:f0:e5:71 (try 1)
[  350.729697] wlan0: authenticated
[  350.729762] wlan0: associate with AP 00:1a:c4:f0:e5:71 (try 1)
[  350.731747] wlan0: RX AssocResp from 00:1a:c4:f0:e5:71 (capab=0x431 status=0 aid=1)
[  350.731759] wlan0: associated
[  353.755643] wlan0: deauthenticated from 00:1a:c4:f0:e5:71 (Reason: 2)
[  354.926127] wlan0: direct probe to AP 00:1a:c4:f0:e5:71 (try 1)
[  354.929338] wlan0: direct probe responded
[  354.929355] wlan0: authenticate with AP 00:1a:c4:f0:e5:71 (try 1)
[  354.930636] wlan0: authenticated
[  354.930710] wlan0: associate with AP 00:1a:c4:f0:e5:71 (try 1)
[  354.932481] wlan0: RX AssocResp from 00:1a:c4:f0:e5:71 (capab=0x431 status=0 aid=1)
[  354.932489] wlan0: associated
[  357.950307] wlan0: deauthenticated from 00:1a:c4:f0:e5:71 (Reason: 2)
[  359.177776] wlan0: direct probe to AP 00:1a:c4:f0:e5:71 (try 1)
[  359.179694] wlan0: direct probe responded
[  359.179709] wlan0: authenticate with AP 00:1a:c4:f0:e5:71 (try 1)
[  359.181604] wlan0: authenticated
[  359.181676] wlan0: associate with AP 00:1a:c4:f0:e5:71 (try 1)
[  359.184391] wlan0: RX AssocResp from 00:1a:c4:f0:e5:71 (capab=0x431 status=0 aid=1)
[  359.184405] wlan0: associated
[  369.240108] wlan0: deauthenticating from 00:1a:c4:f0:e5:71 by local choice (reason=3)
[  369.614536] wlan0: direct probe to AP 00:1a:c4:f0:e5:71 (try 1)
[  369.616378] wlan0: direct probe responded
[  369.616385] wlan0: authenticate with AP 00:1a:c4:f0:e5:71 (try 1)
[  369.618114] wlan0: authenticated
[  369.618169] wlan0: associate with AP 00:1a:c4:f0:e5:71 (try 1)
[  369.619972] wlan0: RX AssocResp from 00:1a:c4:f0:e5:71 (capab=0x431 status=0 aid=1)
[  369.619978] wlan0: associated
[  370.353162] eth0: link up.
[  370.355572] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  372.642558] wlan0: deauthenticated from 00:1a:c4:f0:e5:71 (Reason: 2)
[  373.535142] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  373.739823] forcedeth 0000:00:0a.0: irq 27 for MSI/MSI-X
[  384.415115] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  384.610043] eth0: no IPv6 routers present
[  393.826173] wlan0: direct probe to AP 00:1a:c4:f0:e5:71 (try 1)
[  393.826909] wlan0: direct probe to AP 00:1a:c4:f0:e5:71 (try 1)
[  393.828878] wlan0: direct probe responded
[  393.828896] wlan0: authenticate with AP 00:1a:c4:f0:e5:71 (try 1)
[  393.830874] wlan0: authenticated
[  393.830953] wlan0: associate with AP 00:1a:c4:f0:e5:71 (try 1)
[  393.832707] wlan0: RX AssocResp from 00:1a:c4:f0:e5:71 (capab=0x431 status=0 aid=1)
[  393.832719] wlan0: associated
[  393.835394] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  404.222558] wlan0: no IPv6 routers present
[ 2052.380231] wlan0: deauthenticating from 00:1a:c4:f0:e5:71 by local choice (reason=3)
[ 2052.981192] ath5k 0000:05:00.0: PCI INT A disabled
[ 2062.633872] ath5k 0000:05:00.0: PCI INT A -> Link[LK4E] -> GSI 19 (level, low) -> IRQ 19
[ 2062.633895] ath5k 0000:05:00.0: setting latency timer to 64
[ 2062.634068] ath5k 0000:05:00.0: registered as 'phy1'
[ 2063.132118] ath: EEPROM regdomain: 0x65
[ 2063.132121] ath: EEPROM indicates we should expect a direct regpair map
[ 2063.132126] ath: Country alpha2 being used: 00
[ 2063.132128] ath: Regpair used: 0x65
[ 2063.134640] phy1: Selected rate control algorithm 'minstrel'
[ 2063.137303] Registered led device: ath5k-phy1::rx
[ 2063.137713] Registered led device: ath5k-phy1::tx
[ 2063.137723] ath5k phy1: Atheros AR2425 chip found (MAC: 0xe2, PHY: 0x70)
[ 2063.183781] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2070.327608] wlan0: direct probe to AP 00:1a:c4:f0:e5:71 (try 1)
[ 2070.328184] wlan0: direct probe to AP 00:1a:c4:f0:e5:71 (try 1)
[ 2070.330032] wlan0: direct probe responded
[ 2070.330048] wlan0: authenticate with AP 00:1a:c4:f0:e5:71 (try 1)
[ 2070.332347] wlan0: authenticated
[ 2070.332419] wlan0: associate with AP 00:1a:c4:f0:e5:71 (try 1)
[ 2070.334902] wlan0: RX AssocResp from 00:1a:c4:f0:e5:71 (capab=0x431 status=0 aid=1)
[ 2070.334916] wlan0: associated
[ 2070.337681] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 2077.499244] eth0: link down.
[ 2078.350419] forcedeth 0000:00:0a.0: irq 27 for MSI/MSI-X
[ 2078.350657] eth0: no link during initialization.
[ 2078.354226] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 2081.050053] wlan0: no IPv6 routers present

```

```

 dmesg | grep ath5k
[   19.907369] ath5k 0000:05:00.0: PCI INT A -> Link[LK4E] -> GSI 19 (level, low) -> IRQ 19
[   19.907378] ath5k 0000:05:00.0: setting latency timer to 64
[   19.907436] ath5k 0000:05:00.0: registered as 'phy0'
[   20.470935] Registered led device: ath5k-phy0::rx
[   20.470958] Registered led device: ath5k-phy0::tx
[   20.470962] ath5k phy0: Atheros AR2425 chip found (MAC: 0xe2, PHY: 0x70)
[ 2052.981192] ath5k 0000:05:00.0: PCI INT A disabled
[ 2062.633872] ath5k 0000:05:00.0: PCI INT A -> Link[LK4E] -> GSI 19 (level, low) -> IRQ 19
[ 2062.633895] ath5k 0000:05:00.0: setting latency timer to 64
[ 2062.634068] ath5k 0000:05:00.0: registered as 'phy1'
[ 2063.137303] Registered led device: ath5k-phy1::rx
[ 2063.137713] Registered led device: ath5k-phy1::tx
[ 2063.137723] ath5k phy1: Atheros AR2425 chip found (MAC: 0xe2, PHY: 0x70)

```

6) Network configuration

```

sudo lshw -C network

  *-network               
       description: Ethernet interface
       product: MCP67 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:1b:38:c8:1c:d2
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 latency=0 link=no maxlatency=20 mingnt=1 multicast=yes port=MII
       resources: irq:27 memory:f2688000-f2688fff ioport:30f8(size=8) memory:f2689c00-f2689cff memory:f2689800-f268980f
  *-network
       description: Wireless interface
       product: AR5001 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: wlan0
       version: 01
       serial: 00:1f:3a:04:bd:7a
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath5k driverversion=2.6.32-22-generic firmware=N/A ip=192.168.0.64 latency=0 link=yes multicast=yes wireless=IEEE 802.11bg
       resources: irq:19 memory:f2200000-f220ffff

```

7) Scan for networks:

```

iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:1A:C4:F0:E5:71
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=-38 dBm  
                    Encryption key:on
                    ESSID:"AKAA"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000003722d29e7e
                    Extra: Last beacon: 79890ms ago
                    IE: Unknown: 0004414B4141
                    IE: Unknown: 010882848B8C12969824
                    IE: Unknown: 030106
                    IE: Unknown: 0706555320010B1B
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 3204B048606C

```

```

iwlist scan wlan0
iwlist: unknown command `wlan0' (check 'iwlist --help').

```

8 ) Ubuntu Version: 

```

lsb_release -d

Description:	Ubuntu 10.04 LTS

```

9) Kernel/architecture (including 32 vs. 64 bit): 

```

uname -mr

2.6.32-22-generic x86_64

```

10) Restarting the network:

```

sudo /etc/init.d/networking restart

* Reconfiguring network
interfaces...                      
Ignoring unknown interface wlan0=wlan0.

```

---

### Post by acreech on 2010-06-07
That temporary fix seemed to be working, but after logging out and then back in the wireless connection goes back to disconnecting. Also re-putting the commands does not seem to make a difference in the continual disconnecting. 

acreech

---

### Post by damontallen on 2010-06-07
I found that by installing the proprietary driver by using option 2 of the Manually installed drivers section at [[COLOR="Blue"]https://help.ubuntu.com/community/WifiDocs/Driver/Atheros[/COLOR]]("https://help.ubuntu.com/community/WifiDocs/Driver/Atheros") but when I reboot I have to type 

```
sudo modprobe ath5k nohwcrypt=1
```

But it keeps working after that; no problems with the 1/2 hour disconnect. 

I found this page [[COLOR="Blue"]http://linux.die.net/man/5/modprobe.conf[/COLOR]]("http://linux.die.net/man/5/modprobe.conf") and I am thinking about adding 

```
Install ath5k
```

to the /etc/modprobe.d/alsa-base.conf file but I don't know if that will fix it or I am missing some syntax.  

I don't have access to the machine at the moment so if anyone has a suggestion on what would be the correct way to fix it please let me know.

---

### Post by damontallen on 2010-06-07
Never mind I think I found what I was looking for here [[COLOR="Blue"]http://ubuntu-utah.ubuntuforums.org/showpost.php?p=8809305&postcount=11[/COLOR]]("http://ubuntu-utah.ubuntuforums.org/showpost.php?p=8809305&postcount=11").

Actually here [[COLOR="Blue"]http://ubuntu-utah.ubuntuforums.org/showpost.php?p=9026676&postcount=19[/COLOR]]("http://ubuntu-utah.ubuntuforums.org/showpost.php?p=9026676&postcount=19")

---

### Post by acreech on 2010-06-07
> **damontallen said:**
> I found that by installing the proprietary driver by using option 2 of the Manually installed drivers section at [[COLOR="Blue"]https://help.ubuntu.com/community/WifiDocs/Driver/Atheros[/COLOR]]("https://help.ubuntu.com/community/WifiDocs/Driver/Atheros") but when I reboot I have to type 

```
sudo modprobe ath5k nohwcrypt=1
```

But it keeps working after that; no problems with the 1/2 hour disconnect. 

I found this page [[COLOR="Blue"]http://linux.die.net/man/5/modprobe.conf[/COLOR]]("http://linux.die.net/man/5/modprobe.conf") and I am thinking about adding 

```
Install ath5k
```

to the /etc/modprobe.d/alsa-base.conf file but I don't know if that will fix it or I am missing some syntax.  

I don't have access to the machine at the moment so if anyone has a suggestion on what would be the correct way to fix it please let me know.


I get stuck on step 1) 

```

(Synopsis:
0. Connect to wired network and install build-essential (sudo apt-get install build-essential)
1. wget http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6-current.tar.gz
2. tar -zxvf madwifi-hal-0.10.5.6-current.tar.gz
3. cd madwifi-hal-0.10.5.6-r*
4. sudo make
5. sudo make install
6. System -> Administration -> Hardware Drivers -> Uncheck both hal and Atheros support
7. sudo vi /etc/modprobe.d/blacklist -> blacklist ndiswrapper (Do this if you had tried ndiswrapper)

This will download and install a non-free, binary-only driver for the atheros chipset. You need to rebuild and reinstall the driver every time you update your kernel.

```

here is the error that I got"
```

--2010-06-07 18:42:33--  http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6-current.tar.gz
Resolving snapshots.madwifi-project.org... 217.24.1.134
Connecting to snapshots.madwifi-project.org|217.24.1.134|:80... connected.
HTTP request sent, awaiting response... 403 Forbidden
2010-06-07 18:42:33 ERROR 403: Forbidden.

```

acreech

---

### Post by damontallen on 2010-06-10
Actually it may be easier just to download directly from [http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6/](http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6/) and then follow along.  I didn't find a need to do step 6 or 7 either.  I listed the complete process here [http://ubuntuforums.org/showpost.php?p=9426427&postcount=4](http://ubuntuforums.org/showpost.php?p=9426427&postcount=4) .

---

### Post by acreech on 2010-06-11
> **damontallen said:**
> Actually it may be easier just to download directly from [http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6/](http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6/) and then follow along.  I didn't find a need to do step 6 or 7 either.  I listed the complete process here [http://ubuntuforums.org/showpost.php?p=9426427&postcount=4](http://ubuntuforums.org/showpost.php?p=9426427&postcount=4) .

Thanks for the suggestion. So far that seems to have fixed my wireless issues. 

acreech

---

### Post by mike068 on 2010-06-15
Hi guys I am still having the same problem with getting disconnected all the time but I am very unsure how to install this new driver could some one please help me with step by step directions for the Linuxly Challenged  

This is driving me nuts

---

### Post by b k on 2010-06-15
> **acreech said:**
> I have been haivng problems with my wireless, ever since upgrading to Lucid. I have searched the forums, but like others, halve not found a solution yet for the problem. The problems did not exist with Karmic. The problem that I am having is that the wireless connection disconnects constantly. I have installed Wicd. This does not make the connection more stable, but it does automatically try to reconnect, where as Network Manager would not automatically attempt to reconnect. 
 
I have an Atheros AR5001 Wireless Network Adapter. I have also seen it reffered to as an "Atheros ar5007eg". I found a thread that suggested running these commands for a temporary fix. 
 
```

sudo rmmod -f ath5k
sudo modprobe ath5k nohwcrypt=1

```
 
So far this seems to be working. I don't understand what the commands did or how to make that a more permanent fix (I am assuming that upon a restart the problems will be back). I also don't understand what changed between the last version and the current version of Ubuntu to create this connection issue. I have listed information below about my system, which should help with any diagnoses or solutions. 
 
Thanks for your help. 
 
acreech
 
 
 
1) Machine Brand and Model (PC/Laptop):
 
```

Acer Aspire 7520-5185
AMD Athlon 64 Dual Core Processor
NVIDIA GeForce 7000M Turbo Cache
3 GB DDR2
802.11 b/g WLAN

```
 
2) Wireless Brand, Model and Wireless Chipset:
 
```

lspci
 
00:00.0 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
00:01.0 ISA bridge: nVidia Corporation MCP67 ISA Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP67 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
00:01.3 Co-processor: nVidia Corporation MCP67 Co-processor (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:04.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:04.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP67 IDE Controller (rev a1)
00:07.0 Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1)
00:08.0 PCI bridge: nVidia Corporation MCP67 PCI Bridge (rev a2)
00:09.0 IDE interface: nVidia Corporation MCP67 AHCI Controller (rev a2)
00:0a.0 Ethernet controller: nVidia Corporation MCP67 Ethernet (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:0d.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:12.0 VGA compatible controller: nVidia Corporation C67 [GeForce 7000M / nForce 610M] (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:04.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
01:04.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
01:04.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
01:04.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
01:04.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
05:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)

```
 
```

lspci
 
00:00.0 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
00:01.0 ISA bridge: nVidia Corporation MCP67 ISA Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP67 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
00:01.3 Co-processor: nVidia Corporation MCP67 Co-processor (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:04.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:04.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP67 IDE Controller (rev a1)
00:07.0 Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1)
00:08.0 PCI bridge: nVidia Corporation MCP67 PCI Bridge (rev a2)
00:09.0 IDE interface: nVidia Corporation MCP67 AHCI Controller (rev a2)
00:0a.0 Ethernet controller: nVidia Corporation MCP67 Ethernet (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:0d.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:12.0 VGA compatible controller: nVidia Corporation C67 [GeForce 7000M / nForce 610M] (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:04.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
01:04.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
01:04.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
01:04.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
01:04.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
05:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)
acreech@acreech-laptop:~$ lsusb
Bus 004 Device 002: ID 046d:c062 Logitech, Inc. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 064e:a101 Suyin Corp. Acer CrystalEye Webcam
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```
 
```

lspci -nn | grep Atheros
05:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR5001 Wireless Network Adapter [168c:001c] (rev 01)

```
 
3) Check interface:
 
```

ifconfig
 
eth0      Link encap:Ethernet  HWaddr 00:1b:38:c8:1c:d2  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:6501 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4888 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5480815 (5.4 MB)  TX bytes:805655 (805.6 KB)
          Interrupt:27 Base address:0x8000 
 
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:33055 errors:0 dropped:0 overruns:0 frame:0
          TX packets:33055 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:12097145 (12.0 MB)  TX bytes:12097145 (12.0 MB)
 
wlan0     Link encap:Ethernet  HWaddr 00:1f:3a:04:bd:7a  
          inet addr:192.168.0.64  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:3aff:fe04:bd7a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5262 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4027 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3879411 (3.8 MB)  TX bytes:637556 (637.5 KB)

```
 
```

iwconfig wlan0
 
wlan0     IEEE 802.11bg  ESSID:"AKAA"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:1A:C4:F0:E5:71   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-32 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```
 
4) Check for modules:
 
```

lsmod
 
Module                  Size  Used by
ath5k                 134140  0 
binfmt_misc             7960  1 
ppdev                   6375  0 
vboxdrv              1768311  0 
snd_hda_codec_realtek   278890  1 
joydev                 11072  0 
arc4                    1473  2 
snd_hda_intel          25645  2 
snd_hda_codec          85727  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               6924  1 snd_hda_codec
snd_pcm_oss            41394  0 
snd_mixer_oss          16299  1 snd_pcm_oss
snd_pcm                87850  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1782  0 
snd_seq_oss            31219  0 
snd_seq_midi            5829  0 
snd_rawmidi            23388  1 snd_seq_midi
snd_seq_midi_event      7267  2 snd_seq_oss,snd_seq_midi
snd_seq                57417  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23553  2 snd_pcm,snd_seq
snd_seq_device          6824  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    70978  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
mac80211              243373  1 ath5k
ath                    10345  1 ath5k
uvcvideo               62403  0 
fbcon                  39270  71 
tileblit                2487  1 fbcon
font                    8053  1 fbcon
bitblit                 5811  1 fbcon
softcursor              1565  1 bitblit
ricoh_mmc               3416  0 
sdhci_pci               6700  0 
sdhci                  17928  1 sdhci_pci
videodev               40486  1 uvcvideo
v4l1_compat            15495  2 uvcvideo,videodev
v4l2_compat_ioctl32    12020  1 videodev
acer_wmi               15829  0 
edac_core              45423  0 
edac_mce_amd            9214  0 
cfg80211              152987  3 ath5k,mac80211,ath
led_class               3732  3 ath5k,sdhci,acer_wmi
psmouse                64608  0 
serio_raw               4918  0 
nvidia              10799466  41 
vga16fb                12757  1 
vgastate                9857  1 vga16fb
i2c_nforce2             6099  0 
soundcore               8052  1 snd
snd_page_alloc          8500  2 snd_hda_intel,snd_pcm
k8temp                  3912  0 
lirc_ene0100            7532  0 
lirc_dev               11302  1 lirc_ene0100
video                  20623  0 
output                  2503  1 video
lp                      9336  0 
parport                37160  2 ppdev,lp
usbhid                 40988  0 
hid                    83376  1 usbhid
ohci1394               30260  0 
ahci                   37646  6 
pata_amd               11962  0 
ieee1394               94675  1 ohci1394
forcedeth              55592  0 
 
 
lsmod | grep ath5k
 
ath5k                 134140  0 
mac80211              243373  1 ath5k
ath                    10345  1 ath5k
cfg80211              152987  3 ath5k,mac80211,ath
led_class               3732  3 ath5k,sdhci,acer_wmi

```
 
5) Kernel boot messages
 
```

dmesg
 
[   60.368766] wlan0: associate with AP 00:1a:c4:f0:e5:71 (try 1)
[   60.370665] wlan0: RX AssocResp from 00:1a:c4:f0:e5:71 (capab=0x431 status=0 aid=1)
[   60.370671] wlan0: associated
[   60.382583] wlan0: deauthenticating from 00:1a:c4:f0:e5:71 by local choice (reason=3)
[   60.765482] wlan0: direct probe to AP 00:1a:c4:f0:e5:71 (try 1)
[   60.767118] wlan0: direct probe responded
[   60.767123] wlan0: authenticate with AP 00:1a:c4:f0:e5:71 (try 1)
[   60.768772] wlan0: authenticated
[   60.773792] wlan0: associate with AP 00:1a:c4:f0:e5:71 (try 1)
[   60.775418] wlan0: RX AssocResp from 00:1a:c4:f0:e5:71 (capab=0x431 status=0 aid=1)
[   60.775424] wlan0: associated
[   60.802590] wlan0: deauthenticating from 00:1a:c4:f0:e5:71 by local choice (reason=3)
[   61.185498] wlan0: direct probe to AP 00:1a:c4:f0:e5:71 (try 1)
[   61.188352] wlan0: direct probe responded
[   61.188362] wlan0: authenticate with AP 00:1a:c4:f0:e5:71 (try 1)
[   61.190269] wlan0: authenticated
[   61.190303] wlan0: associate with AP 00:1a:c4:f0:e5:71 (try 1)
[   61.192331] wlan0: RX AssocResp from 00:1a:c4:f0:e5:71 (capab=0x431 status=0 aid=1)
[   61.192336] wlan0: associated
[   61.222577] wlan0: deauthenticating from 00:1a:c4:f0:e5:71 by local choice (reason=3)
[   61.605447] wlan0: direct probe to AP 00:1a:c4:f0:e5:71 (try 1)
[   61.607094] wlan0: direct probe responded
[   61.607103] wlan0: authenticate with AP 00:1a:c4:f0:e5:71 (try 1)
[   61.608605] wlan0: authenticated
[   61.608641] wlan0: associate with AP 00:1a:c4:f0:e5:71 (try 1)
[   61.610518] wlan0: RX AssocResp from 00:1a:c4:f0:e5:71 (capab=0x431 status=0 aid=1)
[   61.610524] wlan0: associated
[   64.630389] wlan0: deauthenticated from 00:1a:c4:f0:e5:71 (Reason: 2)
[   65.790804] wlan0: direct probe to AP 00:1a:c4:f0:e5:71 (try 1)
[   65.793010] wlan0: direct probe responded
[   65.793015] wlan0: authenticate with AP 00:1a:c4:f0:e5:71 (try 1)
[   65.795001] wlan0: authenticated
[   65.795054] wlan0: associate with AP 00:1a:c4:f0:e5:71 (try 1)
[   65.796766] wlan0: RX AssocResp from 00:1a:c4:f0:e5:71 (capab=0x431 status=0 aid=1)
[   65.796770] wlan0: associated
[   68.820672] wlan0: deauthenticated from 00:1a:c4:f0:e5:71 (Reason: 2)
[   69.976252] wlan0: direct probe to AP 00:1a:c4:f0:e5:71 (try 1)
[   69.977909] wlan0: direct probe responded
[   69.977917] wlan0: authenticate with AP 00:1a:c4:f0:e5:71 (try 1)
[   69.979425] wlan0: authenticated
[   69.979454] wlan0: associate with AP 00:1a:c4:f0:e5:71 (try 1)
[   69.982188] wlan0: RX AssocResp from 00:1a:c4:f0:e5:71 (capab=0x431 status=0 aid=1)
[   69.982191] wlan0: associated
[   73.006836] wlan0: deauthenticated from 00:1a:c4:f0:e5:71 (Reason: 2)
[   73.836387] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   74.009268] forcedeth 0000:00:0a.0: irq 27 for MSI/MSI-X
[   74.009480] eth0: no link during initialization.
[   74.010753] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   78.646408] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   79.686272] wlan0: direct probe to AP 00:1a:c4:f0:e5:71 (try 1)
[   79.688602] wlan0: direct probe responded
[   79.688611] wlan0: authenticate with AP 00:1a:c4:f0:e5:71 (try 1)
[   79.690797] wlan0: authenticated
[   79.690849] wlan0: associate with AP 00:1a:c4:f0:e5:71 (try 1)
[   79.692858] wlan0: RX AssocResp from 00:1a:c4:f0:e5:71 (capab=0x431 status=0 aid=1)
[   79.692864] wlan0: associated
[   79.694134] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   79.912558] wlan0: deauthenticating from 00:1a:c4:f0:e5:71 by local choice (reason=3)
[   80.056370] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   80.168575] forcedeth 0000:00:0a.0: irq 27 for MSI/MSI-X
[   80.168782] eth0: no link during initialization.
[   80.169861] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   80.336357] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   82.612956] wlan0: direct probe to AP 00:1a:c4:f0:e5:71 (try 1)
[   82.614598] wlan0: direct probe responded
[   82.614602] wlan0: authenticate with AP 00:1a:c4:f0:e5:71 (try 1)
[   82.616100] wlan0: authenticated
[   82.616123] wlan0: associate with AP 00:1a:c4:f0:e5:71 (try 1)
[   82.617973] wlan0: RX AssocResp from 00:1a:c4:f0:e5:71 (capab=0x431 status=0 aid=1)
[   82.617976] wlan0: associated
[   82.619184] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   86.510042] Clocksource tsc unstable (delta = -272483014 ns)
[   92.670196] wlan0: deauthenticating from 00:1a:c4:f0:e5:71 by local choice (reason=3)
[   93.053128] wlan0: direct probe to AP 00:1a:c4:f0:e5:71 (try 1)
[   93.054837] wlan0: direct probe responded
[   93.054846] wlan0: authenticate with AP 00:1a:c4:f0:e5:71 (try 1)
[   93.056344] wlan0: authenticated
[   93.056395] wlan0: associate with AP 00:1a:c4:f0:e5:71 (try 1)
[   93.058273] wlan0: RX AssocResp from 00:1a:c4:f0:e5:71 (capab=0x431 status=0 aid=1)
[   93.058280] wlan0: associated
[   93.360067] wlan0: no IPv6 routers present
[   96.072729] wlan0: deauthenticated from 00:1a:c4:f0:e5:71 (Reason: 2)
[   97.319845] wlan0: direct probe to AP 00:1a:c4:f0:e5:71 (try 1)
[   97.321621] wlan0: direct probe responded
[   97.321641] wlan0: authenticate with AP 00:1a:c4:f0:e5:71 (try 1)
[   97.323256] wlan0: authenticated
[   97.323335] wlan0: associate with AP 00:1a:c4:f0:e5:71 (try 1)
[   97.326760] wlan0: RX AssocResp from 00:1a:c4:f0:e5:71 (capab=0x431 status=0 aid=1)
[   97.326774] wlan0: associated
[  107.970243] wlan0: deauthenticating from 00:1a:c4:f0:e5:71 by local choice (reason=3)
[  108.383403] wlan0: direct probe to AP 00:1a:c4:f0:e5:71 (try 1)
[  108.385063] wlan0: direct probe responded
[  108.385067] wlan0: authenticate with AP 00:1a:c4:f0:e5:71 (try 1)
[  108.387199] wlan0: authenticated
[  108.387244] wlan0: associate with AP 00:1a:c4:f0:e5:71 (try 1)
[  108.392161] wlan0: RX AssocResp from 00:1a:c4:f0:e5:71 (capab=0x431 status=0 aid=1)
[  108.392168] wlan0: associated
[  111.411796] wlan0: deauthenticated from 00:1a:c4:f0:e5:71 (Reason: 2)
[  112.624367] wlan0: direct probe to AP 00:1a:c4:f0:e5:71 (try 1)
[  112.628152] wlan0: direct probe responded
[  112.628171] wlan0: authenticate with AP 00:1a:c4:f0:e5:71 (try 1)
[  112.630134] wlan0: authenticated
[  112.630212] wlan0: associate with AP 00:1a:c4:f0:e5:71 (try 1)
[  112.632086] wlan0: RX AssocResp from 00:1a:c4:f0:e5:71 (capab=0x431 status=0 aid=1)
[  112.632094] wlan0: associated
[  115.652453] wlan0: deauthenticated from 00:1a:c4:f0:e5:71 (Reason: 2)
[  116.827489] wlan0: direct probe to AP 00:1a:c4:f0:e5:71 (try 1)
[  116.829221] wlan0: direct probe responded
[  116.829238] wlan0: authenticate with AP 00:1a:c4:f0:e5:71 (try 1)
[  116.830621] wlan0: authenticated
[  116.830674] wlan0: associate with AP 00:1a:c4:f0:e5:71 (try 1)
[  116.832466] wlan0: RX AssocResp from 00:1a:c4:f0:e5:71 (capab=0x431 status=0 aid=1)
[  116.832474] wlan0: associated
[  126.890158] wlan0: deauthenticating from 00:1a:c4:f0:e5:71 by local choice (reason=3)
[  127.425130] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  127.638001] forcedeth 0000:00:0a.0: irq 27 for MSI/MSI-X
[  127.638233] eth0: no link during initialization.
[  127.640612] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  132.255140] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  132.443096] wlan0: direct probe to AP 00:1a:c4:f0:e5:71 (try 1)
[  132.445147] wlan0: direct probe responded
[  132.445162] wlan0: authenticate with AP 00:1a:c4:f0:e5:71 (try 1)
[  132.447619] wlan0: authenticated
[  132.447694] wlan0: associate with AP 00:1a:c4:f0:e5:71 (try 1)
[  132.451097] wlan0: RX AssocResp from 00:1a:c4:f0:e5:71 (capab=0x431 status=0 aid=1)
[  132.451109] wlan0: associated
[  132.453836] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  142.180225] wlan0: deauthenticating from 00:1a:c4:f0:e5:71 by local choice (reason=3)
[  142.354902] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  142.527503] forcedeth 0000:00:0a.0: irq 27 for MSI/MSI-X
[  142.527736] eth0: no link during initialization.
[  142.529892] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  142.727707] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  145.064741] wlan0: direct probe to AP 00:1a:c4:f0:e5:71 (try 1)
[  145.066431] wlan0: direct probe responded
[  145.066441] wlan0: authenticate with AP 00:1a:c4:f0:e5:71 (try 1)
[  145.067905] wlan0: authenticated
[  145.170588] wlan0: associate with AP 00:1a:c4:f0:e5:71 (try 1)
[  145.172265] wlan0: RX AssocResp from 00:1a:c4:f0:e5:71 (capab=0x431 status=0 aid=1)
[  145.172274] wlan0: associated
[  145.174865] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  155.210199] wlan0: deauthenticating from 00:1a:c4:f0:e5:71 by local choice (reason=3)
[  155.510035] wlan0: no IPv6 routers present
[  156.376635] wlan0: direct probe to AP 00:1a:c4:f0:e5:71 (try 1)
[  156.379037] wlan0: direct probe responded
[  156.379048] wlan0: authenticate with AP 00:1a:c4:f0:e5:71 (try 1)
[  156.380905] wlan0: authenticated
[  156.380967] wlan0: associate with AP 00:1a:c4:f0:e5:71 (try 1)
[  156.382937] wlan0: RX AssocResp from 00:1a:c4:f0:e5:71 (capab=0x431 status=0 aid=1)
[  156.382958] wlan0: associated
[  166.420189] wlan0: deauthenticating from 00:1a:c4:f0:e5:71 by local choice (reason=3)
[  166.803123] wlan0: direct probe to AP 00:1a:c4:f0:e5:71 (try 1)
[  166.804942] wlan0: direct probe responded
[  166.804961] wlan0: authenticate with AP 00:1a:c4:f0:e5:71 (try 1)
[  166.808113] wlan0: authenticated
[  166.808201] wlan0: associate with AP 00:1a:c4:f0:e5:71 (try 1)
[  166.809907] wlan0: RX AssocResp from 00:1a:c4:f0:e5:71 (capab=0x431 status=0 aid=1)
[  166.809918] wlan0: associated
[  176.870177] wlan0: deauthenticating from 00:1a:c4:f0:e5:71 by local choice (reason=3)
[  177.363494] wlan0: direct probe to AP 00:1a:c4:f0:e5:71 (try 1)
[  177.365292] wlan0: direct probe responded
[  177.365307] wlan0: authenticate with AP 00:1a:c4:f0:e5:71 (try 1)
[  177.366688] wlan0: authenticated
[  177.366766] wlan0: associate with AP 00:1a:c4:f0:e5:71 (try 1)
[  177.368792] wlan0: RX AssocResp from 00:1a:c4:f0:e5:71 (capab=0x431 status=0 aid=1)
[  177.368804] wlan0: associated
[  187.480223] wlan0: deauthenticating from 00:1a:c4:f0:e5:71 by local choice (reason=3)
[  188.363804] wlan0: direct probe to AP 00:1a:c4:f0:e5:71 (try 1)
[  188.365547] wlan0: direct probe responded
[  188.365566] wlan0: authenticate with AP 00:1a:c4:f0:e5:71 (try 1)
[  188.368055] wlan0: authenticated
[  188.368145] wlan0: associate with AP 00:1a:c4:f0:e5:71 (try 1)
[  188.371509] wlan0: RX AssocResp from 00:1a:c4:f0:e5:71 (capab=0x431 status=0 aid=1)
[  188.371520] wlan0: associated
[  188.652629] wlan0: deauthenticating from 00:1a:c4:f0:e5:71 by local choice (reason=3)
[  188.797423] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  189.067176] forcedeth 0000:00:0a.0: irq 27 for MSI/MSI-X
[  189.067406] eth0: no link during initialization.
[  189.069506] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  189.197659] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  190.304848] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  190.487092] forcedeth 0000:00:0a.0: irq 27 for MSI/MSI-X
[  190.487324] eth0: no link during initialization.
[  190.489816] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  191.724229] wlan0: direct probe to AP 00:1a:c4:f0:e5:71 (try 1)
[  191.725910] wlan0: direct probe responded
[  191.725920] wlan0: authenticate with AP 00:1a:c4:f0:e5:71 (try 1)
[  191.727417] wlan0: authenticated
[  191.727470] wlan0: associate with AP 00:1a:c4:f0:e5:71 (try 1)
[  191.729350] wlan0: RX AssocResp from 00:1a:c4:f0:e5:71 (capab=0x431 status=0 aid=1)
[  191.729356] wlan0: associated
[  191.732231] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  201.800145] wlan0: deauthenticating from 00:1a:c4:f0:e5:71 by local choice (reason=3)
[  202.193518] wlan0: direct probe to AP 00:1a:c4:f0:e5:71 (try 1)
[  202.196278] wlan0: direct probe responded
[  202.196296] wlan0: authenticate with AP 00:1a:c4:f0:e5:71 (try 1)
[  202.197565] wlan0: authenticated
[  202.197637] wlan0: associate with AP 00:1a:c4:f0:e5:71 (try 1)
[  202.199515] wlan0: RX AssocResp from 00:1a:c4:f0:e5:71 (capab=0x431 status=0 aid=1)
[  202.199527] wlan0: associated
[  202.380050] wlan0: no IPv6 routers present
[  212.232701] wlan0: deauthenticating from 00:1a:c4:f0:e5:71 by local choice (reason=3)
[  212.662985] wlan0: direct probe to AP 00:1a:c4:f0:e5:71 (try 1)
[  212.666020] wlan0: direct probe responded
[  212.666030] wlan0: authenticate with AP 00:1a:c4:f0:e5:71 (try 1)
[  212.667286] wlan0: authenticated
[  212.667314] wlan0: associate with AP 00:1a:c4:f0:e5:71 (try 1)
[  212.669243] wlan0: RX AssocResp from 00:1a:c4:f0:e5:71 (capab=0x431 status=0 aid=1)
[  212.669246] wlan0: associated
[  214.100179] wlan0: deauthenticating from 00:1a:c4:f0:e5:71 by local choice (reason=3)
[  214.504622] wlan0: direct probe to AP 00:1a:c4:f0:e5:71 (try 1)
[  214.506816] wlan0: direct probe responded
[  214.506832] wlan0: authenticate with AP 00:1a:c4:f0:e5:71 (try 1)
[  214.508346] wlan0: authenticated
[  214.508401] wlan0: associate with AP 00:1a:c4:f0:e5:71 (try 1)
[  214.511005] wlan0: RX AssocResp from 00:1a:c4:f0:e5:71 (capab=0x431 status=0 aid=1)
[  214.511013] wlan0: associated
[  217.536448] wlan0: deauthenticated from 00:1a:c4:f0:e5:71 (Reason: 2)
[  218.724813] wlan0: direct probe to AP 00:1a:c4:f0:e5:71 (try 1)
[  218.726543] wlan0: direct probe responded
[  218.726551] wlan0: authenticate with AP 00:1a:c4:f0:e5:71 (try 1)
[  218.728437] wlan0: authenticated
[  218.728500] wlan0: associate with AP 00:1a:c4:f0:e5:71 (try 1)
[  218.730194] wlan0: RX AssocResp from 00:1a:c4:f0:e5:71 (capab=0x431 status=0 aid=1)
[  218.730201] wlan0: associated
[  228.780231] wlan0: deauthenticating from 00:1a:c4:f0:e5:71 by local choice (reason=3)
[  229.163050] wlan0: direct probe to AP 00:1a:c4:f0:e5:71 (try 1)
[  229.165010] wlan0: direct probe responded
[  229.165019] wlan0: authenticate with AP 00:1a:c4:f0:e5:71 (try 1)
[  229.166729] wlan0: authenticated
[  229.166779] wlan0: associate with AP 00:1a:c4:f0:e5:71 (try 1)
[  229.168663] wlan0: RX AssocResp from 00:1a:c4:f0:e5:71 (capab=0x431 status=0 aid=1)
[  229.168670] wlan0: associated
[  239.230165] wlan0: deauthenticating from 00:1a:c4:f0:e5:71 by local choice (reason=3)
[  239.615202] wlan0: direct probe to AP 00:1a:c4:f0:e5:71 (try 1)
[  239.617449] wlan0: direct probe responded
[  239.617466] wlan0: authenticate with AP 00:1a:c4:f0:e5:71 (try 1)
[  239.619575] wlan0: authenticated
[  239.620999] wlan0: associate with AP 00:1a:c4:f0:e5:71 (try 1)
[  239.622939] wlan0: RX AssocResp from 00:1a:c4:f0:e5:71 (capab=0x431 status=0 aid=1)
[  239.622951] wlan0: associated
[  242.646845] wlan0: deauthenticated from 00:1a:c4:f0:e5:71 (Reason: 2)
[  243.836110] wlan0: direct probe to AP 00:1a:c4:f0:e5:71 (try 1)
[  243.837882] wlan0: direct probe responded
[  243.837901] wlan0: authenticate with AP 00:1a:c4:f0:e5:71 (try 1)
[  243.840124] wlan0: authenticated
[  243.840903] wlan0: associate with AP 00:1a:c4:f0:e5:71 (try 1)
[  243.842829] wlan0: RX AssocResp from 00:1a:c4:f0:e5:71 (capab=0x431 status=0 aid=1)
[  243.842838] wlan0: associated
[  253.930200] wlan0: deauthenticating from 00:1a:c4:f0:e5:71 by local choice (reason=3)
[  255.173799] wlan0: direct probe to AP 00:1a:c4:f0:e5:71 (try 1)
[  255.177383] wlan0: direct probe responded
[  255.177401] wlan0: authenticate with AP 00:1a:c4:f0:e5:71 (try 1)
[  255.178621] wlan0: authenticated
[  255.178683] wlan0: associate with AP 00:1a:c4:f0:e5:71 (try 1)
[  255.181083] wlan0: RX AssocResp from 00:1a:c4:f0:e5:71 (capab=0x431 status=0 aid=1)
[  255.181093] wlan0: associated
[  258.200062] wlan0: deauthenticated from 00:1a:c4:f0:e5:71 (Reason: 2)
[  259.376124] wlan0: direct probe to AP 00:1a:c4:f0:e5:71 (try 1)
[  259.378721] wlan0: direct probe responded
[  259.378740] wlan0: authenticate with AP 00:1a:c4:f0:e5:71 (try 1)
[  259.382107] wlan0: authenticated
[  259.382191] wlan0: associate with AP 00:1a:c4:f0:e5:71 (try 1)
[  259.384378] wlan0: RX AssocResp from 00:1a:c4:f0:e5:71 (capab=0x431 status=0 aid=1)
[  259.384388] wlan0: associated
[  269.460214] wlan0: deauthenticating from 00:1a:c4:f0:e5:71 by local choice (reason=3)
[  269.845609] wlan0: direct probe to AP 00:1a:c4:f0:e5:71 (try 1)
[  269.847301] wlan0: direct probe responded
[  269.847317] wlan0: authenticate with AP 00:1a:c4:f0:e5:71 (try 1)
[  269.848844] wlan0: authenticated
[  269.848917] wlan0: associate with AP 00:1a:c4:f0:e5:71 (try 1)
[  269.854027] wlan0: RX AssocResp from 00:1a:c4:f0:e5:71 (capab=0x431 status=0 aid=1)
[  269.854039] wlan0: associated
[  272.872214] wlan0: deauthenticated from 00:1a:c4:f0:e5:71 (Reason: 2)
[  274.174103] wlan0: direct probe to AP 00:1a:c4:f0:e5:71 (try 1)
[  274.176262] wlan0: direct probe responded
[  274.176281] wlan0: authenticate with AP 00:1a:c4:f0:e5:71 (try 1)
[  274.177553] wlan0: authenticated
[  274.177624] wlan0: associate with AP 00:1a:c4:f0:e5:71 (try 1)
[  274.181811] wlan0: RX AssocResp from 00:1a:c4:f0:e5:71 (capab=0x431 status=0 aid=1)
[  274.181824] wlan0: associated
[  284.240202] wlan0: deauthenticating from 00:1a:c4:f0:e5:71 by local choice (reason=3)
[  284.624893] wlan0: direct probe to AP 00:1a:c4:f0:e5:71 (try 1)
[  284.627330] wlan0: direct probe responded
[  284.627348] wlan0: authenticate with AP 00:1a:c4:f0:e5:71 (try 1)
[  284.629132] wlan0: authenticated
[  284.629229] wlan0: associate with AP 00:1a:c4:f0:e5:71 (try 1)
[  284.631180] wlan0: RX AssocResp from 00:1a:c4:f0:e5:71 (capab=0x431 status=0 aid=1)
[  284.631192] wlan0: associated
[  294.700166] wlan0: deauthenticating from 00:1a:c4:f0:e5:71 by local choice (reason=3)
[  295.823527] wlan0: direct probe to AP 00:1a:c4:f0:e5:71 (try 1)
[  295.827590] wlan0: direct probe responded
[  295.827625] wlan0: authenticate with AP 00:1a:c4:f0:e5:71 (try 1)
[  295.828903] wlan0: authenticated
[  295.829014] wlan0: associate with AP 00:1a:c4:f0:e5:71 (try 1)
[  295.832340] wlan0: RX AssocResp from 00:1a:c4:f0:e5:71 (capab=0x431 status=0 aid=1)
[  295.832352] wlan0: associated
[  305.920202] wlan0: deauthenticating from 00:1a:c4:f0:e5:71 by local choice (reason=3)
[  306.487832] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  306.699017] forcedeth 0000:00:0a.0: irq 27 for MSI/MSI-X
[  306.699249] eth0: no link during initialization.
[  306.701440] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  311.255272] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  311.635607] wlan0: direct probe to AP 00:1a:c4:f0:e5:71 (try 1)
[  311.637274] wlan0: direct probe responded
[  311.637283] wlan0: authenticate with AP 00:1a:c4:f0:e5:71 (try 1)
[  311.638752] wlan0: authenticated
[  311.638808] wlan0: associate with AP 00:1a:c4:f0:e5:71 (try 1)
[  311.640631] wlan0: RX AssocResp from 00:1a:c4:f0:e5:71 (capab=0x431 status=0 aid=1)
[  311.640638] wlan0: associated
[  311.643221] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  315.352625] wlan0: deauthenticating from 00:1a:c4:f0:e5:71 by local choice (reason=3)
[  315.750301] wlan0: direct probe to AP 00:1a:c4:f0:e5:71 (try 1)
[  315.751993] wlan0: direct probe responded
[  315.752001] wlan0: authenticate with AP 00:1a:c4:f0:e5:71 (try 1)
[  315.753797] wlan0: authenticated
[  315.753832] wlan0: associate with AP 00:1a:c4:f0:e5:71 (try 1)
[  315.755754] wlan0: RX AssocResp from 00:1a:c4:f0:e5:71 (capab=0x431 status=0 aid=1)
[  315.755759] wlan0: associated
[  321.240220] wlan0: deauthenticating from 00:1a:c4:f0:e5:71 by local choice (reason=3)
[  321.408985] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  321.588454] forcedeth 0000:00:0a.0: irq 27 for MSI/MSI-X
[  321.588702] eth0: no link during initialization.
[  321.590735] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  321.787347] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  324.173162] wlan0: direct probe to AP 00:1a:c4:f0:e5:71 (try 1)
[  324.174967] wlan0: direct probe responded
[  324.174975] wlan0: authenticate with AP 00:1a:c4:f0:e5:71 (try 1)
[  324.177350] wlan0: authenticated
[  324.177394] wlan0: associate with AP 00:1a:c4:f0:e5:71 (try 1)
[  324.179692] wlan0: RX AssocResp from 00:1a:c4:f0:e5:71 (capab=0x431 status=0 aid=1)
[  324.179698] wlan0: associated
[  324.181060] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  334.220168] wlan0: deauthenticating from 00:1a:c4:f0:e5:71 by local choice (reason=3)
[  334.603086] wlan0: direct probe to AP 00:1a:c4:f0:e5:71 (try 1)
[  334.604944] wlan0: direct probe responded
[  334.604952] wlan0: authenticate with AP 00:1a:c4:f0:e5:71 (try 1)
[  334.606734] wlan0: authenticated
[  334.606786] wlan0: associate with AP 00:1a:c4:f0:e5:71 (try 1)
[  334.608645] wlan0: RX AssocResp from 00:1a:c4:f0:e5:71 (capab=0x431 status=0 aid=1)
[  334.608651] wlan0: associated
[  334.700052] wlan0: no IPv6 routers present
[  344.710199] wlan0: deauthenticating from 00:1a:c4:f0:e5:71 by local choice (reason=3)
[  345.093122] wlan0: direct probe to AP 00:1a:c4:f0:e5:71 (try 1)
[  345.095047] wlan0: direct probe responded
[  345.095056] wlan0: authenticate with AP 00:1a:c4:f0:e5:71 (try 1)
[  345.096781] wlan0: authenticated
[  345.173822] wlan0: associate with AP 00:1a:c4:f0:e5:71 (try 1)
[  345.175557] wlan0: RX AssocResp from 00:1a:c4:f0:e5:71 (capab=0x431 status=0 aid=1)
[  345.175568] wlan0: associated
[  346.082611] wlan0: deauthenticating from 00:1a:c4:f0:e5:71 by local choice (reason=3)
[  346.483098] wlan0: direct probe to AP 00:1a:c4:f0:e5:71 (try 1)
[  346.484814] wlan0: direct probe responded
[  346.484828] wlan0: authenticate with AP 00:1a:c4:f0:e5:71 (try 1)
[  346.486277] wlan0: authenticated
[  346.486334] wlan0: associate with AP 00:1a:c4:f0:e5:71 (try 1)
[  346.488189] wlan0: RX AssocResp from 00:1a:c4:f0:e5:71 (capab=0x431 status=0 aid=1)
[  346.488195] wlan0: associated
[  349.512047] wlan0: deauthenticated from 00:1a:c4:f0:e5:71 (Reason: 2)
[  350.725707] wlan0: direct probe to AP 00:1a:c4:f0:e5:71 (try 1)
[  350.728164] wlan0: direct probe responded
[  350.728179] wlan0: authenticate with AP 00:1a:c4:f0:e5:71 (try 1)
[  350.729697] wlan0: authenticated
[  350.729762] wlan0: associate with AP 00:1a:c4:f0:e5:71 (try 1)
[  350.731747] wlan0: RX AssocResp from 00:1a:c4:f0:e5:71 (capab=0x431 status=0 aid=1)
[  350.731759] wlan0: associated
[  353.755643] wlan0: deauthenticated from 00:1a:c4:f0:e5:71 (Reason: 2)
[  354.926127] wlan0: direct probe to AP 00:1a:c4:f0:e5:71 (try 1)
[  354.929338] wlan0: direct probe responded
[  354.929355] wlan0: authenticate with AP 00:1a:c4:f0:e5:71 (try 1)
[  354.930636] wlan0: authenticated
[  354.930710] wlan0: associate with AP 00:1a:c4:f0:e5:71 (try 1)
[  354.932481] wlan0: RX AssocResp from 00:1a:c4:f0:e5:71 (capab=0x431 status=0 aid=1)
[  354.932489] wlan0: associated
[  357.950307] wlan0: deauthenticated from 00:1a:c4:f0:e5:71 (Reason: 2)
[  359.177776] wlan0: direct probe to AP 00:1a:c4:f0:e5:71 (try 1)
[  359.179694] wlan0: direct probe responded
[  359.179709] wlan0: authenticate with AP 00:1a:c4:f0:e5:71 (try 1)
[  359.181604] wlan0: authenticated
[  359.181676] wlan0: associate with AP 00:1a:c4:f0:e5:71 (try 1)
[  359.184391] wlan0: RX AssocResp from 00:1a:c4:f0:e5:71 (capab=0x431 status=0 aid=1)
[  359.184405] wlan0: associated
[  369.240108] wlan0: deauthenticating from 00:1a:c4:f0:e5:71 by local choice (reason=3)
[  369.614536] wlan0: direct probe to AP 00:1a:c4:f0:e5:71 (try 1)
[  369.616378] wlan0: direct probe responded
[  369.616385] wlan0: authenticate with AP 00:1a:c4:f0:e5:71 (try 1)
[  369.618114] wlan0: authenticated
[  369.618169] wlan0: associate with AP 00:1a:c4:f0:e5:71 (try 1)
[  369.619972] wlan0: RX AssocResp from 00:1a:c4:f0:e5:71 (capab=0x431 status=0 aid=1)
[  369.619978] wlan0: associated
[  370.353162] eth0: link up.
[  370.355572] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  372.642558] wlan0: deauthenticated from 00:1a:c4:f0:e5:71 (Reason: 2)
[  373.535142] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  373.739823] forcedeth 0000:00:0a.0: irq 27 for MSI/MSI-X
[  384.415115] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  384.610043] eth0: no IPv6 routers present
[  393.826173] wlan0: direct probe to AP 00:1a:c4:f0:e5:71 (try 1)
[  393.826909] wlan0: direct probe to AP 00:1a:c4:f0:e5:71 (try 1)
[  393.828878] wlan0: direct probe responded
[  393.828896] wlan0: authenticate with AP 00:1a:c4:f0:e5:71 (try 1)
[  393.830874] wlan0: authenticated
[  393.830953] wlan0: associate with AP 00:1a:c4:f0:e5:71 (try 1)
[  393.832707] wlan0: RX AssocResp from 00:1a:c4:f0:e5:71 (capab=0x431 status=0 aid=1)
[  393.832719] wlan0: associated
[  393.835394] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  404.222558] wlan0: no IPv6 routers present
[ 2052.380231] wlan0: deauthenticating from 00:1a:c4:f0:e5:71 by local choice (reason=3)
[ 2052.981192] ath5k 0000:05:00.0: PCI INT A disabled
[ 2062.633872] ath5k 0000:05:00.0: PCI INT A -> Link[LK4E] -> GSI 19 (level, low) -> IRQ 19
[ 2062.633895] ath5k 0000:05:00.0: setting latency timer to 64
[ 2062.634068] ath5k 0000:05:00.0: registered as 'phy1'
[ 2063.132118] ath: EEPROM regdomain: 0x65
[ 2063.132121] ath: EEPROM indicates we should expect a direct regpair map
[ 2063.132126] ath: Country alpha2 being used: 00
[ 2063.132128] ath: Regpair used: 0x65
[ 2063.134640] phy1: Selected rate control algorithm 'minstrel'
[ 2063.137303] Registered led device: ath5k-phy1::rx
[ 2063.137713] Registered led device: ath5k-phy1::tx
[ 2063.137723] ath5k phy1: Atheros AR2425 chip found (MAC: 0xe2, PHY: 0x70)
[ 2063.183781] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2070.327608] wlan0: direct probe to AP 00:1a:c4:f0:e5:71 (try 1)
[ 2070.328184] wlan0: direct probe to AP 00:1a:c4:f0:e5:71 (try 1)
[ 2070.330032] wlan0: direct probe responded
[ 2070.330048] wlan0: authenticate with AP 00:1a:c4:f0:e5:71 (try 1)
[ 2070.332347] wlan0: authenticated
[ 2070.332419] wlan0: associate with AP 00:1a:c4:f0:e5:71 (try 1)
[ 2070.334902] wlan0: RX AssocResp from 00:1a:c4:f0:e5:71 (capab=0x431 status=0 aid=1)
[ 2070.334916] wlan0: associated
[ 2070.337681] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 2077.499244] eth0: link down.
[ 2078.350419] forcedeth 0000:00:0a.0: irq 27 for MSI/MSI-X
[ 2078.350657] eth0: no link during initialization.
[ 2078.354226] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 2081.050053] wlan0: no IPv6 routers present

```
 
```

 dmesg | grep ath5k
[   19.907369] ath5k 0000:05:00.0: PCI INT A -> Link[LK4E] -> GSI 19 (level, low) -> IRQ 19
[   19.907378] ath5k 0000:05:00.0: setting latency timer to 64
[   19.907436] ath5k 0000:05:00.0: registered as 'phy0'
[   20.470935] Registered led device: ath5k-phy0::rx
[   20.470958] Registered led device: ath5k-phy0::tx
[   20.470962] ath5k phy0: Atheros AR2425 chip found (MAC: 0xe2, PHY: 0x70)
[ 2052.981192] ath5k 0000:05:00.0: PCI INT A disabled
[ 2062.633872] ath5k 0000:05:00.0: PCI INT A -> Link[LK4E] -> GSI 19 (level, low) -> IRQ 19
[ 2062.633895] ath5k 0000:05:00.0: setting latency timer to 64
[ 2062.634068] ath5k 0000:05:00.0: registered as 'phy1'
[ 2063.137303] Registered led device: ath5k-phy1::rx
[ 2063.137713] Registered led device: ath5k-phy1::tx
[ 2063.137723] ath5k phy1: Atheros AR2425 chip found (MAC: 0xe2, PHY: 0x70)

```
 
6) Network configuration
 
```

sudo lshw -C network
 
  *-network               
       description: Ethernet interface
       product: MCP67 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:1b:38:c8:1c:d2
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 latency=0 link=no maxlatency=20 mingnt=1 multicast=yes port=MII
       resources: irq:27 memory:f2688000-f2688fff ioport:30f8(size=8) memory:f2689c00-f2689cff memory:f2689800-f268980f
  *-network
       description: Wireless interface
       product: AR5001 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: wlan0
       version: 01
       serial: 00:1f:3a:04:bd:7a
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath5k driverversion=2.6.32-22-generic firmware=N/A ip=192.168.0.64 latency=0 link=yes multicast=yes wireless=IEEE 802.11bg
       resources: irq:19 memory:f2200000-f220ffff

```
 
7) Scan for networks:
 
```

iwlist scan
lo        Interface doesn't support scanning.
 
eth0      Interface doesn't support scanning.
 
wlan0     Scan completed :
          Cell 01 - Address: 00:1A:C4:F0:E5:71
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=-38 dBm  
                    Encryption key:on
                    ESSID:"AKAA"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000003722d29e7e
                    Extra: Last beacon: 79890ms ago
                    IE: Unknown: 0004414B4141
                    IE: Unknown: 010882848B8C12969824
                    IE: Unknown: 030106
                    IE: Unknown: 0706555320010B1B
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 3204B048606C

```
 
```

iwlist scan wlan0
iwlist: unknown command `wlan0' (check 'iwlist --help').

```
 
8 ) Ubuntu Version: 
 
```

lsb_release -d
 
Description:    Ubuntu 10.04 LTS

```
 
9) Kernel/architecture (including 32 vs. 64 bit): 
 
```

uname -mr
 
2.6.32-22-generic x86_64

```
 
10) Restarting the network:
 
```

sudo /etc/init.d/networking restart
 
* Reconfiguring network
interfaces...                      
Ignoring unknown interface wlan0=wlan0.

```
 
Hi there, not sure if it will solve your problem but suggest you try this:
 
If you have administration rights to your router, try different combination of authmode and encryption [COLOR=red]without TKIP [/COLOR][COLOR=black]eg. wpa2-psk with AES encryption.[/COLOR]
 
You may also like to try this:
 
Go to Applications > Accessories > Terminal

Code:
[COLOR=blue]sudo gedit /etc/rc.local[/COLOR] (then type your password and press Enter)

add the following line at the* end* of the opened file (*just above* the exit 0 line):

[COLOR=blue]iwconfig wlan0 power off[/COLOR]

[COLOR=red]save[/COLOR] and close

reboot
 
No garantee though if it will work for you. 
(If it does not work the above procedure can be repeated and the added line removed to reverse the change -[COLOR=red] but leave the exit 0 line untouched[/COLOR]).

Good luck and post back.

---

