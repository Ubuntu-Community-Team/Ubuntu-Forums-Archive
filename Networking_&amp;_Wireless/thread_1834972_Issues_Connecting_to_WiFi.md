---
title: "Issues Connecting to WiFi"
date: 2011-08-28
forum: Networking &amp; Wireless
---

### Post by Wgimson on 2011-08-28
I'm having some issues connecting to wifi networks, but only for the first hour or so after I boot up my laptop. After a while, my laptop will 'magically' connect to any available networks. The problem is that 'a while' can end up being like two hours. I'm running 10.4.

Also, this may be entirely trivial, but the icon in the upper left corner signifying that the system is attempting two connect (looks like multiple parallel lines going around in a circle until a connection is established) is always composed of *two* groups of opposing parallel sets of lines following each other around in circles during periods when my laptop *won't* connect, kind of like a ying yang. After a while, when it does finally connect, the icon changes to a single group of parallel lines. Again, probably trivial...

Here's the output of lshw -C network...
```

lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: WiMAX/WiFi Link 6050 Series
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 5f
       serial: 00:23:15:61:39:a0
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:30 memory:f4c00000-f4c01fff
  *-network
       description: Ethernet interface
       product: Marvell Technology Group Ltd.
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 11
       serial: 00:24:54:df:bc:66
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.25 firmware=N/A ip=192.168.1.141 latency=0 multicast=yes
       resources: irq:28 memory:f3820000-f3823fff ioport:b000(size=256) memory:f
```Here's the output of iwconfig....

```
 iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
```Here's the output of ifconfig...
```

ifconfig
eth0      Link encap:Ethernet  HWaddr 00:24:54:df:bc:66  
          inet addr:192.168.1.141  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::224:54ff:fedf:bc66/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:53939 errors:0 dropped:0 overruns:0 frame:0
          TX packets:33926 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:70386586 (70.3 MB)  TX bytes:2515353 (2.5 MB)
          Interrupt:19 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:286756 errors:0 dropped:0 overruns:0 frame:0
          TX packets:286756 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:39342645 (39.3 MB)  TX bytes:39342645 (39.3 MB)

wlan0     Link encap:Ethernet  HWaddr 00:23:15:61:39:a0  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```

---

### Post by wildmanne39 on 2011-08-28
Hi, please post the results of these commands:
```
lspci -nn | grep 0280
```
```
rfkill list all
```
```
lsmod
```
```
sudo iwlist scan
```
```
nm-tool
```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by Wgimson on 2011-08-28
```
lspci -nn | grep 0280
02:00.0 Network controller [0280]: Intel Corporation WiMAX/WiFi Link 6050 Series [8086:0087] (rev 5f)

```

```
rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
```

```
lsmod
Module                  Size  Used by
binfmt_misc             6587  1 
ppdev                   5259  0 
nls_iso8859_1           3249  1 
nls_cp437               4919  1 
snd_hda_codec_intelhdmi    11622  1 
snd_hda_codec_realtek   203376  1 
vfat                    8933  1 
fat                    47767  1 vfat
fbcon                  35102  71 
tileblit                1999  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
snd_hda_intel          22165  4 
snd_hda_codec          74201  3 snd_hda_codec_intelhdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70918  4 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
arc4                    1153  2 
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
iwlagn                107199  0 
iwlcore               106661  1 iwlagn
mac80211              205402  2 iwlagn,iwlcore
i915                  289443  3 
nouveau               467624  0 
led_class               2864  1 iwlcore
uvcvideo               57406  0 
ttm                    50231  1 nouveau
drm_kms_helper         29361  2 i915,nouveau
snd                    54244  20 snd_hda_codec_intelhdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                63677  0 
videodev               34361  1 uvcvideo
v4l1_compat            13251  2 uvcvideo,videodev
serio_raw               3978  0 
cfg80211              126144  3 iwlagn,iwlcore,mac80211
drm                   163066  6 i915,nouveau,ttm,drm_kms_helper
soundcore               6620  1 snd
snd_page_alloc          7172  2 snd_hda_intel,snd_pcm
intel_agp              24671  2 i915
agpgart                31788  3 ttm,drm,intel_agp
i2c_algo_bit            5028  2 i915,nouveau
video                  17375  1 i915
output                  1871  1 video
lp                      7028  0 
parport                32635  2 ppdev,lp
usbhid                 36206  0 
hid                    67288  1 usbhid
sky2                   41072  0 
ahci                   32392  3 
```

```
sudo iwlist scan
[sudo] password for william: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 98:FC:11:6B:8A:A5
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=-29 dBm  
                    Encryption key:on
                    ESSID:"ShyPenguin"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001686da13909
                    Extra: Last beacon: 3188ms ago
                    IE: Unknown: 000A53687950656E6775696E
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606080000000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD810050F204104A00011010440001021041000100103B00010310470010C091FF6CFCEF434299DAFCE2AB3B92321021000C4C696E6B73797320496E632E1023000D4C696E6B7379732045323030301024000776312E302E30331042000234321054000800060050F20400011011000D4C696E6B737973204532303030100800020084
                    IE: Unknown: DD090010180200F0040000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C33FC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3406080000000000000000000000000000000000000000
          Cell 02 - Address: 00:26:B8:C5:45:81
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:on
                    ESSID:"virus"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000009fb6734197
                    Extra: Last beacon: 2952ms ago
                    IE: Unknown: 00057669727573
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B000400000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD7B0050F204104A00011010440001021041000100103B00010310470010DB7AFFE529766427681162954EAE60F91021000842726F6164636F6D1023000842726F6164636F6D1024000631323334353610420004313233341054000800060050F20400011011000A42726F6164636F6D4150100800020084103C000101
                    IE: Unknown: DD090010180202F0040000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 03 - Address: 00:17:3F:BF:B3:6B
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:off
                    ESSID:"Adware Virus"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000027e3afcb35e
                    Extra: Last beacon: 3168ms ago
                    IE: Unknown: 000C416477617265205669727573
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0104
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1AEE1115FFFF0000010000000000000000000000000E0000000000
                    IE: Unknown: 3D1606070100000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4304000000
                    IE: Unknown: 0706555320010B10
                    IE: Unknown: DD1E00904C33EE1115FFFF0000010000000000000000000000000E0000000000
                    IE: Unknown: DD1A00904C3406070100000000000000000000000000000000000000
          Cell 04 - Address: 00:13:10:C8:A6:67
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=17/70  Signal level=-93 dBm  
                    Encryption key:on
                    ESSID:"Vash"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000169ca2a181
                    Extra: Last beacon: 3088ms ago
                    IE: Unknown: 000456617368
                    IE: Unknown: 010482848B96
                    IE: Unknown: 03010A
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 32088C129824B048606C
                    IE: Unknown: DD0C000AF50A0222C00003010305
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK

```
```

nm-tool

NetworkManager Tool

State: connected

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlagn
  State:             disconnected
  Default:           no
  HW Address:        00:23:15:61:39:A0

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    Vash:            Infra, 00:13:10:C8:A6:67, Freq 2457 MHz, Rate 54 Mb/s, Strength 24 WPA
    2WIRE403:        Infra, 98:2C:BE:AA:69:41, Freq 2412 MHz, Rate 54 Mb/s, Strength 27 WEP
    belkin.3b32:     Infra, 94:44:52:BD:1B:51, Freq 2412 MHz, Rate 54 Mb/s, Strength 28 WPA WPA2
    2WIRE747:        Infra, 00:1B:5B:7D:5C:39, Freq 2437 MHz, Rate 54 Mb/s, Strength 34 WEP
    Adware Virus:    Infra, 00:17:3F:BF:B3:6B, Freq 2437 MHz, Rate 54 Mb/s, Strength 45
    virus:           Infra, 00:26:B8:C5:45:81, Freq 2462 MHz, Rate 54 Mb/s, Strength 38 WPA WPA2
    ShyPenguin:      Infra, 98:FC:11:6B:8A:A5, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WPA WPA2
    interwebz:       Infra, A0:21:B7:AA:47:08, Freq 2412 MHz, Rate 54 Mb/s, Strength 40 WPA2


- Device: eth0  [Auto eth0] ----------------------------------------------------
  Type:              Wired
  Driver:            sky2
  State:             connected
  Default:           yes
  HW Address:        00:24:54:DF:BC:66

  Capabilities:
    Carrier Detect:  yes
    Speed:           1000 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.141
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.15.1
```


My wifi network is ShyPengiun......

---

### Post by fdrake on 2011-08-28
```
dmesg | grep -e wlan0 -e iwlagn

```

---

### Post by Wgimson on 2011-08-28
```
dmesg | grep -e wlan0 -e iwlagn
[    9.277614] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27k
[    9.277617] iwlagn: Copyright(c) 2003-2009 Intel Corporation
[    9.277693] iwlagn 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    9.277703] iwlagn 0000:02:00.0: setting latency timer to 64
[    9.277740] iwlagn 0000:02:00.0: Detected Intel Wireless WiFi Link 6050 Series 2x2 AGN REV=0x84
[    9.298850] iwlagn 0000:02:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[    9.298937] iwlagn 0000:02:00.0: irq 30 for MSI/MSI-X
[   10.271443] iwlagn 0000:02:00.0: firmware: requesting iwlwifi-6050-4.ucode
[   10.317777] iwlagn 0000:02:00.0: loaded firmware version 9.201.4.1
[   10.596529] ADDRCONF(NETDEV_UP): wlan0: link is not ready

```

---

### Post by Wgimson on 2011-08-28
Any thoughts? Like I said, if my laptop has been on for a couple of hours, it connects to wifi no problem. It's those first couple of hours after boot up where it won't connect for some reason. So what's different between just after boot up vs. running for a couple hours? What changes?

---

### Post by wildmanne39 on 2011-08-28
Hi, for starters try this.

This problem is a known issue with the iwlagn driver, and the best workaround is to disable 802.11n on the card.

To disable 802.11n on this card create /edit your /etc/modprobe.d/options.conf file like this.
```
gksu gedit /etc/modprobe.d/options.conf
```
And add the following to it.
```
options iwlagn 11n_disable=1 11n_disable50=1 
```
then save and exit.

If this does not fix your issue post back if it does please mark solved.

I am sorry it took me so long to get back to you I have been doing a complete brake job on my car today.
Thank you

---

### Post by Wgimson on 2011-08-28
awesome man, thanks so much. I'll give it a shot now......

---

### Post by Wgimson on 2011-08-28
Well it didn't work unfortunately but I really appreciate the help thus far. I'll try to do some research on this driver issue.


- Another post seems to suggest that the file should be called 'iwlagn' rather than 'options.conf'. Anyone know whether this is true/makes a difference?

- or do I need to find my module name with $modinfo iwalgn?

---

### Post by wildmanne39 on 2011-08-28
Hi, before we go further make sure your router is setup for g/b/n speed and not just n speed.

Also set your wireless encryption to wpa2 only and see if that improves connection.

---

### Post by Wgimson on 2011-08-28
Ok, I just looked through the documentation for my router and couldn't find any instructions on modifying which 802.11 protocol it uses. That said, it's supposed to support n, g, a, etc. and should be enabled for all these. Is there a command I can use to verify this?

- also, I just noticed that the BSSID and MAC lines in the Network Connections gui for my wireless network are blank. Not sure if that's significant.

- as for the encryption, I configured the router on my windows partition because I have trouble getting Ubuntu to read the disk. I set it up with WPA2 only. That said, when Ubuntu prompts me for a password it's under 'WPA & WPA2', but that might just be the semantics of the prompt for all I know.

- I should also mention that my wireless worked perfectly for a long time until relatively recently, when this machine-connects-only-after-2-hours nonsense started happening out of the blue.

---

### Post by wildmanne39 on 2011-08-28
Hi, this is some of the information from the commands you ran.
>     ShyPenguin:      Infra, 98:FC:11:6B:8A:A5, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 [COLOR="Red"]WPA WPA2[/COLOR]
As for this
> Ok, I just looked through the documentation for my router and couldn't find any instructions on modifying which 802.11 protocol it uses. 
That is changed by the commands I gave you so it just did not fix your problem.

Did you have updates to network manager or your wireless driver recently?

Please post the results of these commands, and run all commands while you are not able to connect.
```
dmesg | grep iwl
```
```
lsmod | grep iwl
```
Also run this command 
```
gksu gedit /etc/modprobe.d/options.conf
```
does it have this in it?
```
options iwlagn 11n_disable=1 11n_disable50=1
```
Thank you

---

### Post by Wgimson on 2011-08-28
I almost always apply the updates the update manager offers. One of those is probably what did it, huh?

- ok, one second. I have to reboot because now my laptop has been on long enough that it is able to connect.

Thanks again, by the way, for taking this much time to help me out, I really appreciate it.

---

### Post by wildmanne39 on 2011-08-28
Hi, it is possible.
Please post the results of the commands in my previous post and we will see if we can narrow down the problem.
Thank you

---

### Post by Wgimson on 2011-08-29
Ok, here goes...
```

dmesg | grep iwl
[    9.383703] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27k
[    9.383707] iwlagn: Copyright(c) 2003-2009 Intel Corporation
[    9.383767] iwlagn 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    9.383776] iwlagn 0000:02:00.0: setting latency timer to 64
[    9.383809] iwlagn 0000:02:00.0: Detected Intel Wireless WiFi Link 6050 Series 2x2 AGN REV=0x84
[    9.404636] iwlagn 0000:02:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[    9.404723] iwlagn 0000:02:00.0: irq 29 for MSI/MSI-X
[    9.411878] phy0: Selected rate control algorithm 'iwl-agn-rs'
[   10.899906] iwlagn 0000:02:00.0: firmware: requesting iwlwifi-6050-4.ucode
[   10.923773] iwlagn 0000:02:00.0: loaded firmware version 9.201.4.1
[   11.180710] Registered led device: iwl-phy0::radio
[   11.180725] Registered led device: iwl-phy0::assoc
[   11.180739] Registered led device: iwl-phy0::RX
[   11.180751] Registered led device: iwl-phy0::TX
``````
lsmod | grep iwl
iwlagn                107199  0 
iwlcore               106661  1 iwlagn
mac80211              205402  2 iwlagn,iwlcore
led_class               2864  1 iwlcore
cfg80211              126144  3 iwlagn,iwlcore,mac80211
```

> 
cat /etc/modprobe.d/options.conf
options iwlagn 11n_disable=1 11n_disable50=1

---

### Post by wildmanne39 on 2011-08-29
I do not see a problem from the last information you posted.

I believe you still should change your encryption to just wpa2 in your router or disable it completely for a few minutes and see if that fixes your problem it will help to eliminate that as a problem at the very least. 

It maybe that your isp updated your routers firmware.
Thank you

---

### Post by Wgimson on 2011-08-29
> **wildmanne39 said:**
> 
I believe you still should change your encryption to just wpa2


How do I do this? Or is it router-specific?

> **wildmanne39 said:**
> 
It maybe that your isp updated your routers firmware.


If this is the case is it basically just a matter of waiting for a fix to come out?

Thanks again.


- Now that I think about it, the first time I had the problem was on a different network, so I don't think it's the router's firmware. The issue persists across networks.

The part that's strange to me is that it *starts* working after a few hours. If I could just figure out what changes in those first couple hours we might be able to figure this out haha.....

---

### Post by wildmanne39 on 2011-08-29
Hi, type this 192.168.0.1 into your address bar of your web browser and it should get you to your routers setup, then under wireless you can change your security settings. 

You will need to have a wired connection to your router. 

I am going to bed for tonight, I will check on you tomorrow, and if I need to I will ask a friend for help.
Thank you

---

### Post by Wgimson on 2011-08-29
> **wildmanne39 said:**
> Hi, type this 192.168.0.1 into your address bar of your web browser and it should get you to your routers setup, then under wireless you can change your security settings. 

You will need to have a wired connection to your router. 

I am going to bed for tonight, I will check on you tomorrow, and if I need to I will ask a friend for help.
Thank you
 
Cool man, and a million thanks for your help so far.

---

### Post by Wgimson on 2011-08-29
any ideas guys? I'm at a loss.

---

### Post by wildmanne39 on 2011-08-29
Hi, I asked a friend to take a look.

Did you change your encryption settings?

---

### Post by Wgimson on 2011-08-29
Hey wildmanne, thanks for asking about my problem here. Ok, can I go about changing my encryption settings from the command line?

---

### Post by wildmanne39 on 2011-08-29
Hi, the only way that I know of is to use the method in post 18. For some routers it is not the ip address I mentioned but a little variation of it.

Did you try the way in post 18?

You have to be hard wired to do it.

---

### Post by Wgimson on 2011-08-29
Ah, ok. Yeah, when I do that I get an error, but I'm pretty sure I can log into the cisco website and perhaps I can change it from there. Give me one minute to check.

---

### Post by praseodym on 2011-08-30
Hello,

you can update the module iwlagn using the backported modules in 10.04. You can directly install the metapackage for them being updated automatically:

```
sudo apt-get install --reinstall linux-backports-modules-wireless-lucid-generic
```
Check if you need generic, generic-pae or whatever kernel architecture you are using with
```
uname -r
```
Reboot after that.

---

### Post by chili555 on 2011-08-30
I suggest you go into the administration pages of your router and set the encryption to WPA2 only; not mixed mode. Please see attached.

---

### Post by Wgimson on 2011-08-31
> **praseodym said:**
> Hello,

you can update the module iwlagn using the backported modules in 10.04. You can directly install the metapackage for them being updated automatically:

```
sudo apt-get install --reinstall linux-backports-modules-wireless-lucid-generic
```
Check if you need generic, generic-pae or whatever kernel architecture you are using with
```
uname -r
```
Reboot after that.

That seems to have done the trick. Thanks so much, praseodym. Now I can add backporting to the list of things I really need to learn about haha. Also, thanks a ton for your help, wildmanne, and for taking the time to walk me through everything.

So, given that this backporting apparently fixed the problem, what likely caused it in the first place? A bad update corrupted the iwlagn module? And what exactly is backporting, and what did it do? Restore my iwlagn module to the standard configuration?

Thanks again guys.

---

### Post by praseodym on 2011-08-31
These are the kernel modules from newer kernels, compiled for the older ones. Take a look at

[http://linuxwireless.org/en/users/Devices](http://linuxwireless.org/en/users/Devices)

which modules are in that package. Some devices dont work properly with the "standard" module versions, so updating them is always a good idea

---

### Post by wildmanne39 on 2011-08-31
Hi, I am glad you got it working and I learned something new in the process.

Thank you to my friends for helping us out.

---

### Post by howl at the moon on 2011-09-01
```
sudo apt-get install --reinstall linux-backports-modules-wireless-lucid-generic
```Worked perfectly for me too, thanks very much :KS

---

