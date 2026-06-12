---
title: "Wireless network gets slow after a couple minutes after login"
date: 2013-05-19
forum: Networking &amp; Wireless
---

### Post by blubber42 on 2013-05-19
I just installed Ubuntu 13.04 on my MacBook air, and have this really weird problem. When I first login and open my browser it's incredibly fast. I use [http://www.tweakers.net](http://www.tweakers.net) as a benchmark, and that page loads instantly. The google frontpage also loads instantly.

However, after a couple of minutes it starts to slow down. Both pages take a longer time to load (couple of seconds). Especially images are loading slowly.

The problem occurs after a couple minutes after booting, it doesn't matter if I log in or not.

I have the following broadcom nic:

02:00.0 Network controller [0280]: Broadcom Corporation BCM43224 802.11a/b/g/n [14e4:4353] (rev 01)

My guess is it's a problem with the network card, but I'm not actually sure. I looked at various logs, but not aberrant messages are logged. I tried both the open source and the proprietary drivers, but they both exhibit the same behavior.

Edit: I also tried to disable ipv6, but that doesn't make any difference at all.

---

### Post by praseodym on 2013-05-19
Install the missing firmware for the native driver:
```

wget media.cdn.ubuntu-de.org/forum/attachments/56/18/5007272-Broadcom_Firmware_070513.tar.gz
sudo tar xvf 5007272-Broadcom_Firmware_070513.tar.gz -C /lib/firmware 
```

Shut down currentless for 10 minutes and reboot then. Check
```

lsmod
dmesg | grep brcm
iwconfig
sudo iwlist scan
```

---

### Post by blubber42 on 2013-05-19
Well, I did what you said. No messages appeared in dmesg containing brcm, however, I've been browsing around for over 10m now, and it does seem that the issue is fixed.

So thanks a lot!

---

### Post by blubber42 on 2013-05-19
Ok, on second though it didn't work. The same problem is still there. After a while the wlan gets really slow, I tried copying the firmware but it didn't help.

---

### Post by blubber42 on 2013-05-19
It seems like the firmware isn't getting loaded, no requests are made to udev to actually load the firmware.

---

### Post by praseodym on 2013-05-19
Check now:
```

lspci -nnk | grep -iA2 net
rfkill list
lsmod
dmesg | egrep 'b43|bcma|brcm|[F]irm'
iwconfig
```

---

### Post by blubber42 on 2013-05-19
```

$ lspci -nnk | grep -iA2 net
02:00.0 Network controller [0280]: Broadcom Corporation BCM43224 802.11a/b/g/n [14e4:4353] (rev 01)
    Subsystem: Apple Inc. Device [106b:00e9]
    Kernel driver in use: bcma-pci-bridge

```

```

$ rfkill list
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

```

```

$ lsmod
Module                  Size  Used by
dm_crypt               22820  1 
arc4                   12615  2 
brcmsmac              550698  0 
coretemp               13355  0 
kvm_intel             132891  0 
parport_pc             28152  0 
kvm                   443165  1 kvm_intel
ppdev                  17073  0 
cordic                 12574  1 brcmsmac
brcmutil               14755  1 brcmsmac
mac80211              606457  1 brcmsmac
cfg80211              510937  2 brcmsmac,mac80211
bnep                   18036  2 
rfcomm                 42641  12 
joydev                 17377  0 
applesmc               19353  0 
input_polldev          13896  1 applesmc
snd_hda_codec_hdmi     36913  1 
microcode              22881  0 
snd_hda_codec_cirrus    23829  1 
nls_iso8859_1          12713  1 
uvcvideo               80847  0 
btusb                  22474  0 
snd_hda_intel          39619  3 
videobuf2_vmalloc      13056  1 uvcvideo
snd_hda_codec         136453  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec_cirrus
bcm5974                17347  0 
bluetooth             228619  22 bnep,btusb,rfcomm
snd_hwdep              13602  1 snd_hda_codec
lpc_ich                17061  0 
videobuf2_memops       13202  1 videobuf2_vmalloc
videobuf2_core         40513  1 uvcvideo
videodev              129260  2 uvcvideo,videobuf2_core
bcma                   41051  1 brcmsmac
snd_pcm                97451  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30180  1 snd_seq_midi
snd_seq                61554  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29425  2 snd_pcm,snd_seq
snd                    68876  16 snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_hda_codec_cirrus
mei                    41158  0 
soundcore              12680  1 snd
apple_bl               13673  0 
mac_hid                13205  0 
lp                     17759  0 
parport                46345  3 lp,ppdev,parport_pc
usb_storage            57204  0 
hid_apple              13237  0 
hid_generic            12540  0 
ghash_clmulni_intel    13259  0 
aesni_intel            55399  399 
aes_x86_64             17255  1 aesni_intel
xts                    12885  1 aesni_intel
lrw                    13257  1 aesni_intel
gf128mul               14951  2 lrw,xts
ablk_helper            13597  1 aesni_intel
cryptd                 20373  4 ghash_clmulni_intel,aesni_intel,ablk_helper
i915                  600351  3 
ahci                   25731  3 
libahci                31364  1 ahci
video                  19390  1 i915
i2c_algo_bit           13413  1 i915
drm_kms_helper         49394  1 i915
usbhid                 47074  0 
drm                   286313  4 i915,drm_kms_helper
hid                   101002  3 hid_generic,usbhid,hid_apple

```

```

$ dmesg | egrep 'b43|bcma|brcm|[F]irm'
[    0.054999] [Firmware Bug]: ioapic 2 has no mapping iommu, interrupt remapping will be disabled
[    0.152145] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    2.188626] pci_root PNP0A08:00: [Firmware Info]: MMCONFIG for domain 0000 [bus 00-99] only partially covers this bridge
[   12.481966] bcma-pci-bridge 0000:02:00.0: enabling device (0000 -> 0002)
[   12.482061] bcma: bus0: Found chip with id 0xA8D8, rev 0x01 and package 0x08
[   12.482089] bcma: bus0: Core 0 found: ChipCommon (manuf 0x4BF, id 0x800, rev 0x22, class 0x0)
[   12.482158] bcma: bus0: Core 1 found: IEEE 802.11 (manuf 0x4BF, id 0x812, rev 0x17, class 0x0)
[   12.482204] bcma: bus0: Core 2 found: PCIe (manuf 0x4BF, id 0x820, rev 0x0F, class 0x0)
[   12.531978] bcma: bus0: Bus registered
[   12.758110] brcmsmac bcma0:0: mfg 4bf core 812 rev 23 class 0 irq 17
[   12.938135] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[   12.938146] brcmsmac bcma0:0: brcms_ops_config: change power-save mode: false (implement)
[   20.848581] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[   20.848584] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: enabled true, count 0 (implement)
[   20.848585] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[   20.881542] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: enabled true, count 1 (implement)
[   98.783045] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: enabled true, count 0 (implement)
[   98.805136] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[   98.805159] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: enabled false, count 0 (implement)
[   98.805168] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[  106.830574] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[  106.830585] brcmsmac bcma0:0: brcms_ops_config: change power-save mode: false (implement)
[  114.771996] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[  114.772017] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: enabled true, count 0 (implement)
[  114.772029] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[  114.853436] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: enabled true, count 1 (implement)
[  123.946149] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[  123.946173] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: enabled false, count 1 (implement)
[  123.946179] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[  132.073918] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[  132.073937] brcmsmac bcma0:0: brcms_ops_config: change power-save mode: false (implement)
[  140.052529] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[  140.052542] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: enabled true, count 0 (implement)
[  140.052551] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[  140.154181] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: enabled true, count 1 (implement)
[  200.349080] brcmsmac bcma0:0: brcms_c_ampdu_dotxstatus_complete: Pkt tx suppressed, illegal channel possibly 44

```


```

$ iwconfig
lo        no wireless extensions.


wlan0     IEEE 802.11abgn  ESSID:"wlan"  
          Mode:Managed  Frequency:5.22 GHz  Access Point: E0:46:9A:4E:63:9A   
          Bit Rate=65 Mb/s   Tx-Power=17 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=63/70  Signal level=-47 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:13  Invalid misc:56   Missed beacon:0

```

---

### Post by praseodym on 2013-05-19
The last message shows you are using the 5GHz region. Normally, this driver works there, check:
```

iwlist chan
sudo iwlist scan
```
Which country do you live? Set to "a+b+g" mode in your router, pure WPA2-AES encryption and a fixed channel.

---

### Post by blubber42 on 2013-05-19
```

$ iwlist chan
lo        no frequency information.


wlan0     32 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 36 : 5.18 GHz
          Channel 40 : 5.2 GHz
          Channel 44 : 5.22 GHz
          Channel 48 : 5.24 GHz
          Channel 52 : 5.26 GHz
          Channel 56 : 5.28 GHz
          Channel 60 : 5.3 GHz
          Channel 64 : 5.32 GHz
          Channel 100 : 5.5 GHz
          Channel 104 : 5.52 GHz
          Channel 108 : 5.54 GHz
          Channel 112 : 5.56 GHz
          Channel 116 : 5.58 GHz
          Channel 132 : 5.66 GHz
          Channel 136 : 5.68 GHz
          Channel 140 : 5.7 GHz
          Channel 149 : 5.745 GHz
          Channel 153 : 5.765 GHz
          Channel 157 : 5.785 GHz
          Channel 161 : 5.805 GHz
          Channel 165 : 5.825 GHz
          Current Frequency:5.22 GHz (Channel 44)

```

```

$ sudo iwlist scan
[sudo] password for blubber: 
lo        Interface doesn't support scanning.


wlan0     Scan completed :
          Cell 01 - Address: E0:46:9A:4E:63:9A
                    Channel:44
                    Frequency:5.22 GHz (Channel 44)
                    Quality=65/70  Signal level=-45 dBm  
                    Encryption key:on
                    ESSID:"wlan"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000050f1d3182
                    Extra: Last beacon: 76ms ago
                    IE: Unknown: 0004776C616E
                    IE: Unknown: 01088C129824B048606C
                    IE: Unknown: 03012C
                    IE: Unknown: 070A55532024041195051E00
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2D1ACC111BFFFF000000000000000000000100000000000000000000
                    IE: Unknown: 3D162C000400000000000000000000000000000000000000
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
          Cell 02 - Address: E0:46:9A:4E:63:98
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=37/70  Signal level=-73 dBm  
                    Encryption key:on
                    ESSID:"wlan"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000001d74b9180
                    Extra: Last beacon: 3656ms ago
                    IE: Unknown: 0004776C616E
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 050401020000
                    IE: Unknown: 0706555320010B1B
                    IE: Unknown: 2A0104
                    IE: Unknown: 32043048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2D1ACC111BFFFF000000000000000000000100000000000000000000
                    IE: Unknown: 3D1606000000000000000000000000000000000000000000
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
          Cell 03 - Address: 00:24:FE:A4:DC:28
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=21/70  Signal level=-89 dBm  
                    Encryption key:on
                    ESSID:"Leeuwekuil"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000099151233
                    Extra: Last beacon: 19012ms ago
                    IE: Unknown: 000A4C65657577656B75696C
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030101
                    IE: Unknown: 050C020300000000000000000000
                    IE: Unknown: 2A0107
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32080C1218243048606C
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00

```


I forced my router to use only AES earlier today as I read somewhere that it might make a difference. Just found out the regulatory region on the router was set to US (I live in the netherlands), so I set it to NL now.

> 
[COLOR=#000000]Set to "a+b+g" mode ...


You mean I should try turning of N? [/COLOR]

---

### Post by praseodym on 2013-05-19
Yes, just for the try. Also

```
sudo apt-get install iw
iw reg get
sudo iw reg set NL
iw reg get
iwlist chan
```

---

### Post by blubber42 on 2013-05-20
I tried setting it to a+g only, but no luck.

```

$ iw reg get
country NL:
	(2402 - 2482 @ 40), (N/A, 20)
	(5170 - 5250 @ 40), (N/A, 20), NO-OUTDOOR
	(5250 - 5330 @ 40), (N/A, 20), NO-OUTDOOR, DFS
	(5490 - 5710 @ 40), (N/A, 27), DFS

```

```

wlan0     32 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Channel 36 : 5.18 GHz
          Channel 40 : 5.2 GHz
          Channel 44 : 5.22 GHz
          Channel 48 : 5.24 GHz
          Channel 52 : 5.26 GHz
          Channel 56 : 5.28 GHz
          Channel 60 : 5.3 GHz
          Channel 64 : 5.32 GHz
          Channel 100 : 5.5 GHz
          Channel 104 : 5.52 GHz
          Channel 108 : 5.54 GHz
          Channel 112 : 5.56 GHz
          Channel 116 : 5.58 GHz
          Channel 120 : 5.6 GHz
          Channel 124 : 5.62 GHz
          Channel 128 : 5.64 GHz
          Channel 132 : 5.66 GHz
          Channel 136 : 5.68 GHz
          Channel 140 : 5.7 GHz
          Current Frequency:5.22 GHz (Channel 44)

```

I still think it's weird that the firmware doesn't get loaded. I looked at udev events and various logs, but the firmware isn't even requested by the kernel.

---

### Post by blubber42 on 2013-05-20
Tried various other settings on my router, also rebooted it, but it doesn't seem to help. I think it must be the wifi adapter.

---

### Post by praseodym on 2013-05-20
Try 2,4 GHz region instead

---

### Post by blubber42 on 2013-05-20
I already tried that. I tried both 5 and 2.4GHz, also tried them separately, doesn't seem to have any effect. And I still don't understand why the firmware isn't getting loaded at all.

---

