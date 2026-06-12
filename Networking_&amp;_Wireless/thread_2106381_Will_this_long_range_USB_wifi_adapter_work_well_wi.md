---
title: "Will this long range USB wifi adapter work well with Ubuntu?"
date: 2013-01-18
forum: Networking &amp; Wireless
---

### Post by Ender Shadow on 2013-01-18
I was looking for a USB Wi-fi adapter a couple days ago, and I think I found one that I like. Although...

[http://www.amazon.com/Protronix%C2%AE-802-11N-Wireless-Adapter-150Mbps/dp/B004BAN3D6/ref=sr_1_18?s=electronics&ie=UTF8&qid=1358473437&sr=1-18&](http://www.amazon.com/Protronix%C2%AE-802-11N-Wireless-Adapter-150Mbps/dp/B004BAN3D6/ref=sr_1_18?s=electronics&ie=UTF8&qid=1358473437&sr=1-18&)

While it does say that it's compatible with Linux operating systems, will the Linux version of the driver actually support the long range mode?

---

### Post by helpee on 2013-01-18
There's 2 ways that thing could work

1) it has an amplifier
2) it's a directional antenna

Neither of those things require special drivers, the long range is just a function of the design of the device.

---

### Post by ahallubuntu on 2013-01-18
It uses the Ralink RT3070 chipset.  Do some googling on that and Ubuntu and you'll see how well it has been supported lately.

---

### Post by Ender Shadow on 2013-01-19
I guess I'll get it, then. 
By the way, does Ubuntu come with the driver, or do I have get it elsewhere?

---

### Post by ahallubuntu on 2013-01-19
I have no idea whether Ubuntu comes with a driver for this chipset or not.  If I were going to buy this card, first I would do some googling for "Ubuntu Ralink RT3070" and see what comes up.

---

### Post by chadk5utc on 2013-01-19
> **ahallubuntu said:**
> I have no idea whether Ubuntu comes with a driver for this chipset or not.  If I were going to buy this card, first I would do some googling for "Ubuntu Ralink RT3070" and see what comes up.

I have to agree Google is your friend for stuff like this research is always a good idea when choosing hardware for any OS, find compatibility, driver, troubleshooting Etc before buying so you know or at least have some idea what the challenges are prior to buying.

---

### Post by praseodym on 2013-01-20
The Ralink rt3070 chipset should work ootb with the module 'rt2800usb', which is part of the kernel. If it does not, come back with the outputs of
```

lsusb
lsmod
```
Ralink has several new drivers available on their homepage:

[http://www.mediatek.com/_en/07_downloads/01_windows.php?sn=501](http://www.mediatek.com/_en/07_downloads/01_windows.php?sn=501)

---

### Post by Ender Shadow on 2013-01-22
I ordered the adapter a few days ago, and it should be here soon.
I had already found the driver for it, which I can use if the kernel's driver doesn't work, or if any problems with the kernel's driver are unsolvable.

---

### Post by Ender Shadow on 2013-01-24
I just got the adapter today, and it's working very well. Now, with the adapter plugged into back of my PC, it can connect to the wifi in the other room. The signal strength is pretty good, although it isn't strong enough to watch Youtube videos.

---

### Post by praseodym on 2013-01-24
Check:
```

iwconfig
lsusb
lsmod
sudo iwlist scan #which is your nw?
ifconfig -a
route -n
```
Change to pure WPA2-AES (CCMP) encryption, if possible, and use a fixed channel.

Edit: "Ignore" IPv6 in the network-manager.

---

### Post by Ender Shadow on 2013-01-24
My security is already set to WPA2-AES with the CCMP thing, and I set IPv6 to "Ignore."

Here are the outputs of iwconfig, lsusb, lsmod, sudo iwlist scan, ifconfig -a, 
and route -n.


```

[U]iwconfig
[/U]
lo        no wireless extensions.

wlan1     IEEE 802.11bgn  ESSID:"~WXPN~"  #
          Mode:Managed  Frequency:2.412 GHz  Access Point: 48:02:2A:B6:4B:36   
          Bit Rate=43.3 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=57/70  Signal level=-53 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:10  Invalid misc:46   Missed beacon:0

eth0      no wireless extensions.
[U]
lsusb[/U]

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 009 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 010 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 011 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 012 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 002: ID 0ecd:1403 Lite-On IT Corp. 
Bus 011 Device 004: ID 148f:3070 Ralink Technology, Corp. RT2870/RT3070 Wireless Adapter
Bus 009 Device 002: ID 045e:00db Microsoft Corp. Natural Ergonomic Keyboard 4000 V1.0
Bus 009 Device 003: ID 093a:2510 Pixart Imaging, Inc. Optical Mouse

_lsmod_

Module                  Size  Used by
arc4                   12529  2 
rt2800usb              22773  0 
rt2800lib              58967  1 rt2800usb
crc_ccitt              12707  1 rt2800lib
rt2x00usb              20808  1 rt2800usb
rt2x00lib              55326  3 rt2800usb,rt2800lib,rt2x00usb
mac80211              506862  3 rt2800lib,rt2x00usb,rt2x00lib
cfg80211              205774  2 rt2x00lib,mac80211
rfcomm                 47604  0 
bnep                   18281  2 
bluetooth             180153  10 rfcomm,bnep
parport_pc             32866  0 
ppdev                  17113  0 
binfmt_misc            17540  1 
nvidia              11257276  40 
fglrx                3264017  0 
snd_hda_codec_hdmi     32474  2 
snd_emu10k1_synth      17293  0 
snd_emux_synth         42825  1 snd_emu10k1_synth
snd_seq_virmidi        13525  1 snd_emux_synth
snd_seq_midi_emul      17854  1 snd_emux_synth
k10temp                13166  0 
psmouse                97485  0 
serio_raw              13211  0 
snd_emu10k1           157352  3 snd_emu10k1_synth
emu10k1_gp             12650  0 
gameport               19693  2 emu10k1_gp
snd_ac97_codec        134869  1 snd_emu10k1
ac97_bus               12730  1 snd_ac97_codec
snd_util_mem           14117  2 snd_emux_synth,snd_emu10k1
snd_hda_intel          33773  4 
snd_hda_codec         127706  2 snd_hda_codec_hdmi,snd_hda_intel
snd_seq_midi           13324  0 
snd_hwdep              17764  3 snd_emux_synth,snd_emu10k1,snd_hda_codec
snd_pcm                97275  5 snd_hda_codec_hdmi,snd_emu10k1,snd_ac97_codec,snd_hda_intel,snd_hda_codec
snd_rawmidi            30748  3 snd_seq_virmidi,snd_emu10k1,snd_seq_midi
joydev                 17693  0 
snd_seq_midi_event     14899  2 snd_seq_virmidi,snd_seq_midi
snd_seq                61929  5 snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_midi,snd_seq_midi_event
snd_timer              29990  3 snd_emu10k1,snd_pcm,snd_seq
snd_seq_device         14540  5 snd_emu10k1_synth,snd_emu10k1,snd_seq_midi,snd_rawmidi,snd_seq
mac_hid                13253  0 
snd                    79041  25 snd_hda_codec_hdmi,snd_emux_synth,snd_seq_virmidi,snd_emu10k1,snd_ac97_codec,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
radeon                804518  1 
i2c_piix4              13301  0 
ttm                    76949  1 radeon
drm_kms_helper         46978  1 radeon
drm                   241971  3 radeon,ttm,drm_kms_helper
i2c_algo_bit           13423  1 radeon
soundcore              15091  1 snd
snd_page_alloc         18529  3 snd_emu10k1,snd_hda_intel,snd_pcm
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
hid_microsoft          12888  0 
usbhid                 47238  0 
firewire_ohci          41000  0 
hid                    99636  2 hid_microsoft,usbhid
firewire_core          63600  1 firewire_ohci
crc_itu_t              12707  1 firewire_core
r8169                  62154  0 
pata_atiixp            13204  0 
usb_storage            49198  0 
[U]
sudo iwlist scan[/U]

lo        Interface doesn't support scanning.

wlan1     Scan completed :
          Cell 01 - Address: 48:02:2A:B6:4B:36
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=59/70  Signal level=-51 dBm  
                    Encryption key:on
                    ESSID:"~WXPN~"                                     # <--This is my network
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000002f00a557
                    Extra: Last beacon: 32ms ago
                    IE: Unknown: 00067E5758504E7E
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030101
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32088C129824B048606C
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 2D1A6E181EFF00000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601050000000000000000000000000000000000000000
                    IE: Unknown: DD0600E04C020110
          Cell 02 - Address: 20:76:00:19:D6:DC
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=35/70  Signal level=-75 dBm  
                    Encryption key:on
                    ESSID:"TDSV1000W0665"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000dfdc8b3ba5
                    Extra: Last beacon: 960ms ago
                    IE: Unknown: 000D54445356313030305730363635
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030109
                    IE: Unknown: 2A0102
                    IE: Unknown: 2F0102
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AEC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1609001700000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD7B0050F204104A00011010440001021041000100103B0001031047001020E686CDB41BBBBC538C5CF6E28899841021000842726F6164636F6D1023000842726F6164636F6D1024000631323334353610420004313233341054000800060050F20400011011000A42726F6164636F6D4150100800020084103C000101
                    IE: Unknown: DD090010180201F0040000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 03 - Address: 00:1D:CE:A1:F7:00
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:on
                    ESSID:"HOME-F702"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001150975c172
                    Extra: Last beacon: 892ms ago
                    IE: Unknown: 0009484F4D452D46373032
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 03010B
                    IE: Unknown: 32040C183060
                    IE: Unknown: 070C5553200101110209140B0111
                    IE: Unknown: 33082001020304050607
                    IE: Unknown: 33082105060708090A0B
                    IE: Unknown: DD270050F204104A0001101044000102104700102880288028801880A880001DCEA1F700103C000101
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 2D1A0E1017FFFFFF00010000000000000000000000000F0000000000
                    IE: Unknown: 3D160B000100000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101034003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05000023127A
                    IE: Unknown: DD07000C4307000000

eth0      Interface doesn't support scanning.
[U]
ifconfig -a[/U]

eth0      Link encap:Ethernet  HWaddr bc:5f:f4:44:79:36  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:54 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4930 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4930 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:489234 (489.2 KB)  TX bytes:489234 (489.2 KB)

wlan1     Link encap:Ethernet  HWaddr 7c:dd:90:1d:e3:a0  
          inet addr:192.168.159.2  Bcast:192.168.159.255  Mask:255.255.255.0
          inet6 addr: fe80::7edd:90ff:fe1d:e3a0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:46 errors:0 dropped:0 overruns:0 frame:0
          TX packets:114 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:8083 (8.0 KB)  TX bytes:17860 (17.8 KB)
[U]
route -n[/U]

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.159.1   0.0.0.0         UG    0      0        0 wlan1
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan1
192.168.159.0   0.0.0.0         255.255.255.0   U     2      0        0 wlan1



```

---

### Post by praseodym on 2013-01-25
Deactivate the power management:

```
sudo iwconfig wlan1 power off
```

---

### Post by Ender Shadow on 2013-01-25
> **praseodym said:**
> Deactivate the power management:

```
sudo iwconfig wlan1 power off
```

The power management is now set to off, and I will be testing the signal to see if it's any better.

---

### Post by Ender Shadow on 2013-01-26
I've been testing the signal, but it still isn't strong enough. Sometimes it can overcome all the interference, but usually it can't. The TV pretty much kills it. 
I'm using a wired connection right now, and I'll probably use the USB wifi adapter for something else.

---

### Post by praseodym on 2013-01-27
You can deactivate IPv6 in the NM-applet.

---

