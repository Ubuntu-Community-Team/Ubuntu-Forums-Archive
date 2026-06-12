---
title: "Can't connect with ZTE TU-25 modem(XOHM/Clear)"
date: 2009-09-05
forum: Networking &amp; Wireless
---

### Post by Uolirod on 2009-09-05
I have XOHM wimax service and I wanted to get 'connected' with the modem they supplied, ZTE TU-25, but there are no available drivers.  I have no experience with what to do to try to get it working and I'll probably need to have my hand held in the attempt. Any help would be greatly appreciated.

---

### Post by Uolirod on 2009-09-05
If I boot with the USB modem plugged in dmesg contains this:

[   12.000774] USB Serial support registered for GSM modem (1-port)
[   12.000811] option 1-1:1.0: GSM modem (1-port) converter detected
[   12.000933] usb 1-1: GSM modem (1-port) converter now attached to ttyUSB0
[   12.000954] usbcore: registered new interface driver option
[   12.000955] option: v0.7.2:USB Driver for GSM modems

but the device doesn't show up in Network Manager. lsusb gives this:

Bus 001 Device 004: ID 050d:0233 Belkin Components 
Bus 001 Device 002: ID 19d2:0007  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 003: ID 051d:0002 American Power Conversion Uninterruptible Power Supply
Bus 002 Device 002: ID 045e:00f9 Microsoft Corp. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

with the device ID being 19d2:0007.  I'm just curious if it's showing up in dmesg as a GSM modem is getting it up and running just a matter of configuring it properly?

---

### Post by Uolirod on 2009-09-05
And now after finally reading the guide to posting for networking issues here are the results of running all the suggested commands.

XXX@desktop:~$ lspci
00:00.0 RAM memory: nVidia Corporation MCP55 Memory Controller (rev a1)
00:01.0 ISA bridge: nVidia Corporation MCP55 LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP55 SMBus (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP55 USB Controller (rev a1)
00:02.1 USB Controller: nVidia Corporation MCP55 USB Controller (rev a2)
00:04.0 IDE interface: nVidia Corporation MCP55 IDE (rev a1)
00:05.0 RAID bus controller: nVidia Corporation MCP55 SATA Controller (rev a2)
00:05.1 RAID bus controller: nVidia Corporation MCP55 SATA Controller (rev a2)
00:06.0 PCI bridge: nVidia Corporation MCP55 PCI bridge (rev a2)
00:06.1 Audio device: nVidia Corporation MCP55 High Definition Audio (rev a2)
00:08.0 Bridge: nVidia Corporation MCP55 Ethernet (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2)
00:0d.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2)
00:0e.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2)
00:0f.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:08.0 Network controller: RaLink RT2561/RT61 802.11g PCI
06:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce 7600 GS] (rev a1)

XXX@desktop:~$ lsusb
Bus 001 Device 007: ID 154b:0005 PNY 
Bus 001 Device 004: ID 050d:0233 Belkin Components 
Bus 001 Device 002: ID 19d2:0007  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 003: ID 051d:0002 American Power Conversion Uninterruptible Power Supply
Bus 002 Device 002: ID 045e:00f9 Microsoft Corp. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

XXX@desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:e0:4d:0f:3a:e8  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:250 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:14:bf:79:26:28  
          inet addr:192.168.0.106  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::214:bfff:fe79:2628/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:52267 errors:0 dropped:0 overruns:0 frame:0
          TX packets:28191 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:30701439 (30.7 MB)  TX bytes:6146440 (6.1 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-14-BF-79-26-28-36-32-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

XXX@desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"Ravens-'08"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:1E:E5:B3:46:35   
          Bit Rate=54 Mb/s   Tx-Power=13 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=69/100  Signal level:-62 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

XXX@desktop:~$ lsmod
Module                  Size  Used by
nls_iso8859_1          12032  1 
nls_cp437              13696  1 
vfat                   18816  1 
fat                    58272  1 vfat
usb_storage            99648  1 
binfmt_misc            16776  1 
bridge                 56212  0 
stp                    10500  1 bridge
bnep                   20224  2 
input_polldev          11912  0 
video                  25360  0 
output                 11008  1 video
lp                     17156  0 
arc4                    9856  2 
ecb                    10752  2 
rt61pci                29572  0 
crc_itu_t              10112  1 rt61pci
rt2x00pci              15616  1 rt61pci
rt2x00lib              37888  2 rt61pci,rt2x00pci
led_class              12036  1 rt2x00lib
mac80211              217592  2 rt2x00pci,rt2x00lib
snd_hda_intel         434100  3 
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss
snd_pcm                83076  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          10756  0 
snd_seq_oss            37760  0 
snd_seq_midi           14336  0 
snd_rawmidi            29696  1 snd_seq_midi
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29704  2 snd_pcm,snd_seq
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
option                 28036  0 
cfg80211               38288  2 rt2x00lib,mac80211
jedec_probe            20352  0 
cfi_probe              11520  0 
gen_probe              11264  2 jedec_probe,cfi_probe
cfi_util               13696  1 cfi_probe
mtd                    23048  0 
chipreg                11012  2 jedec_probe,cfi_probe
nvidia               7233756  36 
joydev                 18496  0 
snd                    62756  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15200  1 snd
psmouse                61972  0 
ppdev                  15620  0 
i2c_nforce2            14980  0 
eeprom_93cx6           10240  1 rt61pci
map_funcs               9984  0 
agpgart                42696  1 nvidia
hid_microsoft          11780  0 
usbserial              39656  1 option
k8temp                 12416  0 
pcspkr                 10496  0 
snd_page_alloc         16904  2 snd_hda_intel,snd_pcm
serio_raw              13444  0 
parport_pc             40100  1 
parport                42220  3 lp,ppdev,parport_pc
usbhid                 42336  1 
forcedeth              61712  0 
floppy                 64324  0 
fbcon                  46112  0 
tileblit               10752  1 fbcon
font                   16384  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit

---

### Post by ugm6hr on 2009-09-06
Assuming that is a 3G modem, I think you may be out of luck.

This is the most comprehensive list of 3G experience with Ubuntu: [https://wiki.ubuntu.com/NetworkManager/Hardware/3G](https://wiki.ubuntu.com/NetworkManager/Hardware/3G)

It doesn't even mention your device.

---

### Post by Uolirod on 2009-09-06
Well, it's sold as Wimax, (I've gotten better than 3g speeds using Windows XP, but I'm trying to completely migrate from MS). I know it uses Sprint's, now Clearwire's, wimax network. Should I file a bug report for Network Manager or is there some other route for requesting driver support?

---

