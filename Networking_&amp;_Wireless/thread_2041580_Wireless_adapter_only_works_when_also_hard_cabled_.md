---
title: "Wireless adapter only works when also hard cabled at boot"
date: 2012-08-12
forum: Networking &amp; Wireless
---

### Post by AC_Soaring on 2012-08-12
Ok, so here is my odessy...  I have a Cisco AM10 that works fine if the machine is also connected at boot time by a hard wired connection, and not at all if the wireless is the only network connection.

By working fine, I mean it shows up on the desktop and connects to my wireless network (can tell it was successful from the router and have downloaded MB's of data after shutting down eth0).

I took no special steps to get the adapter working.  The attached are the commonly requested commands from the PC when it is booted without the hard link (so non-working see next post for the working version).  My guess is that some change in the start-up process will solve this problem.

```

cat /etc/lsb-release; uname -a 
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04 LTS"
Linux ubuntu-64-FX6800 3.2.0-27-generic #43-Ubuntu SMP Fri Jul 6 14:25:57 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

lspci -nnk | grep -iA2 net
00:19.0 Ethernet controller [0200]: Intel Corporation 82567LF-2 Gigabit Network Connection [8086:10cd]
    Subsystem: Acer Incorporated [ALI] Device [1025:0198]
    Kernel driver in use: e1000e

lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 1307:0169 Transcend Information, Inc. 
Bus 004 Device 002: ID 045e:00b9 Microsoft Corp. Wireless Optical Mouse 3.0
Bus 001 Device 004: ID 1307:1169 Transcend Information, Inc. TS2GJF210 JetFlash 210 2GB
Bus 001 Device 005: ID 13b1:0031 Linksys AM10 v1 802.11n [Ralink RT3072]
Bus 002 Device 002: ID 090c:1000 Silicon Motion, Inc. - Taiwan (formerly Feiya Technology Corp.) 64MB QDI U2 DISK

iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          
eth0      no wireless extensions.

rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

lsmod
Module                  Size  Used by
nls_iso8859_1          12713  1 
nls_cp437              16991  1 
vfat                   17585  1 
fat                    61512  1 vfat
bnep                   18281  2 
parport_pc             32866  0 
ppdev                  17113  0 
rfcomm                 47604  0 
bluetooth             180104  10 bnep,rfcomm
vesafb                 13844  1 
nvidia              12319264  58 
arc4                   12529  2 
rt2800usb              22684  0 
rt2800lib              58925  1 rt2800usb
crc_ccitt              12667  1 rt2800lib
rt2x00usb              20762  1 rt2800usb
rt2x00lib              51144  3 rt2800usb,rt2800lib,rt2x00usb
mac80211              506816  3 rt2800lib,rt2x00usb,rt2x00lib
cfg80211              205544  2 rt2x00lib,mac80211
snd_hda_codec_realtek   223962  1 
snd_hda_intel          33773  3 
snd_hda_codec         127706  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                97188  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30748  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
mxm_wmi                12979  0 
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
psmouse                87692  0 
snd                    78855  15 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
serio_raw              13211  0 
wmi                    19256  1 mxm_wmi
i7core_edac            28102  0 
edac_core              53746  3 i7core_edac
mac_hid                13253  0 
lp                     17799  0 
soundcore              15091  1 snd
parport                46562  3 parport_pc,ppdev,lp
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
firewire_ohci          41000  0 
firewire_core          63558  1 firewire_ohci
crc_itu_t              12707  1 firewire_core
usbhid                 47199  0 
e1000e                156693  0 
hid                    99559  1 usbhid
pata_jmicron           12747  0 
usb_storage            49198  1 

```

---

### Post by AC_Soaring on 2012-08-12
And here is what the same commands give me when I boot with a hard wire plugged in:  (Note I have to do a "sudo ifdown eth0" to avoid confusing the network)

```

cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04 LTS"
Linux ubuntu-64-FX6800 3.2.0-27-generic #43-Ubuntu SMP Fri Jul 6 14:25:57 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

 lspci -nnk | grep -iA2 net
00:19.0 Ethernet controller [0200]: Intel Corporation 82567LF-2 Gigabit Network Connection [8086:10cd]
	Subsystem: Acer Incorporated [ALI] Device [1025:0198]
	Kernel driver in use: e1000e


lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 1307:0169 Transcend Information, Inc. 
Bus 001 Device 004: ID 1307:1169 Transcend Information, Inc. TS2GJF210 JetFlash 210 2GB
Bus 001 Device 005: ID 13b1:0031 Linksys AM10 v1 802.11n [Ralink RT3072]
Bus 004 Device 002: ID 045e:00b9 Microsoft Corp. Wireless Optical Mouse 3.0

iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"Linksys"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:xx:xx:xx:xx:81   
          Bit Rate=65 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=70/70  Signal level=-27 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:5  Invalid misc:51   Missed beacon:0

eth0      no wireless extensions.

rfkill list all
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

lsmod
Module                  Size  Used by
rfcomm                 47604  0 
parport_pc             32866  0 
ppdev                  17113  0 
bnep                   18281  2 
bluetooth             180104  10 rfcomm,bnep
vesafb                 13844  1 
nvidia              12319264  58 
arc4                   12529  2 
rt2800usb              22684  0 
rt2800lib              58925  1 rt2800usb
crc_ccitt              12667  1 rt2800lib
rt2x00usb              20762  1 rt2800usb
rt2x00lib              51144  3 rt2800usb,rt2800lib,rt2x00usb
mac80211              506816  3 rt2800lib,rt2x00usb,rt2x00lib
cfg80211              205544  2 rt2x00lib,mac80211
snd_hda_codec_realtek   223962  1 
snd_hda_intel          33773  3 
snd_hda_codec         127706  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                97188  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30748  1 snd_seq_midi
mxm_wmi                12979  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
wmi                    19256  1 mxm_wmi
psmouse                87692  0 
snd                    78855  15 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
serio_raw              13211  0 
mac_hid                13253  0 
lp                     17799  0 
i7core_edac            28102  0 
parport                46562  3 parport_pc,ppdev,lp
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
edac_core              53746  3 i7core_edac
firewire_ohci          41000  0 
firewire_core          63558  1 firewire_ohci
usbhid                 47199  0 
crc_itu_t              12707  1 firewire_core
hid                    99559  1 usbhid
e1000e                156693  0 
pata_jmicron           12747  0 
usb_storage            49198  0 


```

---

### Post by AC_Soaring on 2012-08-12
I know folks will think the hard wire is carrying the traffic somehow, but here is the current ifconfig (I'm typing this post from the PC):

```

ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:934 errors:0 dropped:0 overruns:0 frame:0
          TX packets:934 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:96286 (96.2 KB)  TX bytes:96286 (96.2 KB)

wlan0     Link encap:Ethernet  HWaddr 68:xx:xx:xx:xx:b3  
          inet addr:192.168.11.65  Bcast:192.168.11.255  Mask:255.255.255.0
          inet6 addr: fe80::xxxx:xxxx:xxxx:xxb3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10457 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7470 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:11494899 (11.4 MB)  TX bytes:1045455 (1.0 MB)

```

---

### Post by AC_Soaring on 2012-08-25
Solved here: [http://ubuntuforums.org/showthread.php?t=1966633&page=5](http://ubuntuforums.org/showthread.php?t=1966633&page=5) 

- Alan

---

