---
title: "Intel Link 5100AGN/Ubuntu Jaunty/Dell Inspiron 14 wireless issue"
date: 2009-10-25
forum: Networking &amp; Wireless
---

### Post by Antares784 on 2009-10-25
Hi!

I'm having trouble enabling wireless on my machine (The "Enable Wireless" checkbox is greyed out). More information:

1. The machine is a Dell Inspiron 14 laptop (1440, specifically).

2: lspci gives:
```
0c:00.0 Network controller: Intel Corporation Wireless WiFi Link 5100
```

3. Output of ifconfig:
```

user@host:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:25:64:67:4e:4b  
--line removed--
          inet6 addr: fec0::a:225:64ff:fe67:4e4b/64 Scope:Site
          inet6 addr: 2002:800c:e096:a:225:64ff:fe67:4e4b/64 Scope:Global
          inet6 addr: fe80::225:64ff:fe67:4e4b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:30189 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5009 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:9256604 (9.2 MB)  TX bytes:812764 (812.7 KB)
          Interrupt:250 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:34 errors:0 dropped:0 overruns:0 frame:0
          TX packets:34 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:11152 (11.1 KB)  TX bytes:11152 (11.1 KB)

wlan0     Link encap:Ethernet  HWaddr 00:24:d6:2b:bc:c6  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-24-D6-2B-BC-C6-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

(the line with IP addresses in eth0 is removed by me)

iwconfig:

```

user@host:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=15 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

```

4. I'm not certain what part of this is relevant so here's the whole output of lsmod

```

user@host:~$ lsmod
Module                  Size  Used by
nls_iso8859_1          13440  1 
nls_cp437              15104  1 
vfat                   21120  1 
fat                    65592  1 vfat
i915                   77960  2 
drm                   123232  3 i915
binfmt_misc            18572  1 
ppdev                  16904  0 
bridge                 63776  0 
stp                    11140  1 bridge
bnep                   22912  2 
input_polldev          12688  0 
lp                     19588  0 
parport                49584  2 ppdev,lp
joydev                 20864  0 
snd_hda_codec_idt      78476  1 
snd_hda_intel          38536  2 
snd_hda_codec          93824  2 snd_hda_codec_idt,snd_hda_intel
arc4                   10240  2 
ecb                    11392  2 
snd_hwdep              17032  1 snd_hda_codec
snd_pcm_oss            51872  0 
snd_mixer_oss          25088  1 snd_pcm_oss
iwlagn                114820  0 
iwlcore               106496  1 iwlagn
snd_pcm                98696  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy          11652  0 
snd_seq_oss            40320  0 
snd_seq_midi           15680  0 
led_class              13064  1 iwlcore
snd_rawmidi            34080  1 snd_seq_midi
snd_seq_midi_event     16640  2 snd_seq_oss,snd_seq_midi
snd_seq                66848  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              33168  2 snd_pcm,snd_seq
snd_seq_device         16532  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
mac80211              251528  2 iwlagn,iwlcore
snd                    82760  17 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                64028  0 
dcdbas                 16944  0 
soundcore              16800  1 snd
usbhid                 47040  0 
uvcvideo               69640  0 
pcspkr                 11136  0 
usb_storage           115520  1 
serio_raw              14468  0 
iTCO_wdt               21712  0 
iTCO_vendor_support    12420  1 iTCO_wdt
cfg80211               43680  3 iwlagn,iwlcore,mac80211
video                  29844  0 
compat_ioctl32         18304  1 uvcvideo
snd_page_alloc         18960  2 snd_hda_intel,snd_pcm
videodev               45184  2 uvcvideo,compat_ioctl32
v4l1_compat            23940  2 uvcvideo,videodev
output                 11648  1 video
intel_agp              39408  1 
r8169                  46596  0 
mii                    14464  1 r8169
fbcon                  49792  0 
tileblit               11264  1 fbcon
font                   17024  1 fbcon
bitblit                14464  1 fbcon
softcursor             10368  1 bitblit

```

5. (Seemingly) relevant output from dmesg:

```

[    9.918318] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27ks
[    9.918321] iwlagn: Copyright(c) 2003-2008 Intel Corporation
[    9.918429] iwlagn 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    9.918464] iwlagn 0000:0c:00.0: setting latency timer to 64
[    9.918555] iwlagn: Detected Intel Wireless WiFi Link 5100AGN REV=0x54
[    9.938479] iwlagn: Tunable channels: 13 802.11bg, 24 802.11a channels
[    9.938546] iwlagn 0000:0c:00.0: irq 2297 for MSI/MSI-X

```

6
```

user@host:~$ sudo lshw -C network
SCSI                      
  *-network        
       description: Wireless interface
       product: Wireless WiFi Link 5100
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: wmaster0
       version: 00
       serial: 00:24:d6:2b:bc:c6
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn latency=0 module=iwlagn multicast=yes wireless=IEEE 802.11abgn
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 02
       serial: 00:25:64:67:4e:4b
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=128.12.228.37 latency=0 link=yes module=r8169 multicast=yes port=MII speed=100MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: aa:e5:d5:20:38:a5
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

```

7.

```

user@host:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     No scan results

pan0      Interface doesn't support scanning.

```

8. Ubuntu 9.04 Jaunty Jackalope

9
```

user@host:~$ uname -mr
2.6.28-16-generic x86_64

```

10: restarting networking
```

user@host:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                   [ OK ]

```

Sorry if this is too much information - I figured more information would make this easier to solve! Thanks very much in advance! :)

---

### Post by Antares784 on 2009-10-25
Sorry also if this is a repeat post... I haven't found anything yet that's worked though.

Thanks!

---

### Post by RainKing44 on 2009-10-25
I wish I could help...I'm in the same boat as you. 

I ended up reinstalling the driver using ndiswrapper, but no matter what I do the network keeps showing up as unclaimed.

---

### Post by darthvader87 on 2009-10-26
hmm my wireless work out of the box with jaunty on my lenovo g450..same card as you.wierd problem you had here

---

### Post by Antares784 on 2009-10-28
Bump.

Has anyone had this problem and fixed it?

---

### Post by abdusamed on 2009-10-31
same..here died tryin.. so i quit ubuntu..now i hope 9.10 will solve it

---

### Post by RainKing44 on 2009-10-31
I just installed Ubuntu 9.10 and am happy to report that Wireless works out of the box with an Intel Wi Fi Link 5100. 

However, it also worked out of the box with 9.04 until I made some updates. I have not made any updates yet to 9.10.

---

### Post by abdusamed on 2009-11-07
really.. it never worked on my qomsio f50-126 machine! SOO MANY ISSUES WITH UBUNTU.. FROM STATIC IP TO SCREENLETS! having a nightmare here!

---

### Post by Antares784 on 2009-11-07
> **abdusamed said:**
> really.. it never worked on my qomsio f50-126 machine! SOO MANY ISSUES WITH UBUNTU.. FROM STATIC IP TO SCREENLETS! having a nightmare here!

I'm sorry to hear that. The problem I was having was silly.. one of the function keys on the keyboard controls wireless as well as bluetooth, and it was disabled. So, the problem is solved!

Abdusamed: Have you tried the same? There might be some hotkeys/function keys on the keyboard or a physical switch for wireless.

---

