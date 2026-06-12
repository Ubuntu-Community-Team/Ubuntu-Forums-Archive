---
title: "broadcom, driver problems SLOWWWWW"
date: 2011-09-04
forum: Networking &amp; Wireless
---

### Post by lkljh on 2011-09-04
I am on Ubuntu 11.04

Broadcom Sta wireless N pci adapter.


It took me quite a lot of time but I finally got the drivers for the thing to work.

However to make it work I am forced into using an older version of the driver for it, and I guess for some reason it is being horribly slow.

I have been searching everywhere and can not find a solution to this slow thing.  I can't update stuff because it is TOO slow.  I have to fo into windows and down load stuff and then move it to ubuntu.  O_O

---

### Post by nm_geo on 2011-09-04
> **lkljh said:**
> I am on Ubuntu 11.04

Broadcom Sta wireless N pci adapter.


It took me quite a lot of time but I finally got the drivers for the thing to work.

However to make it work I am forced into using an older version of the driver for it, and I guess for some reason it is being horribly slow.

I have been searching everywhere and can not find a solution to this slow thing.  I can't update stuff because it is TOO slow.  I have to fo into windows and down load stuff and then move it to ubuntu.  O_O

Sorry I should have said "Welcome to the Forum" first 

Would you please provide the results from these commands in terminal

```
lspci -nn
``````
lsmod
``````

sudo lshw -C network
```

---

### Post by owise1 on 2011-09-04
Not sure if this will help but check your router to see of QoS is enabled (Quality of service).  I had a similar problem with my daughters vista pc and once I disabled that all was well.

---

### Post by lkljh on 2011-09-05
@Owise1:  Thank you for the attempt, unfortunately it was a no go.  :<

@nm_geo

Some of the commands didn't seem to give anything I could copypasta back to you.  :<

```

joel@joel-X48-DS5:~$ lspci -nk | grep -iA2 net
joel@joel-X48-DS5:~$ sudo lspci -nnk | grep -iA2 net
[sudo] password for joel: 
05:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 02)
    Subsystem: Giga-byte Technology GA-EP45-DS5 Motherboard [1458:e000]
    Kernel driver in use: r8169
--
06:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 02)
    Subsystem: Giga-byte Technology GA-EP45-DS5 Motherboard [1458:e000]
    Kernel driver in use: r8169
--
07:01.0 Network controller [0280]: Broadcom Corporation BCM4321 802.11b/g/n [14e4:4329] (rev 01)
    Subsystem: Netgear Device [1385:7d00]
    Kernel driver in use: wl
    Kernel modules: wl, ssb
joel@joel-X48-DS5:~$ lsmod
Module                  Size  Used by
nls_iso8859_1          12713  1 
nls_cp437              16991  1 
vfat                   21708  1 
fat                    61374  1 vfat
usb_storage            53538  3 
uas                    17996  0 
nls_utf8               12557  2 
isofs                  40283  2 
binfmt_misc            17565  1 
vesafb                 13761  1 
nvidia              10709116  40 
ndiswrapper           249811  0 
lib80211_crypt_tkip    17387  0 
ppdev                  17113  0 
snd_hda_codec_realtek   336693  1 
snd_usb_audio         112426  1 
snd_usbmidi_lib        25139  1 snd_usb_audio
snd_hda_intel          33211  2 
snd_hda_codec         103804  2 snd_hda_codec_realtek,snd_hda_intel
parport_pc             36959  1 
wl                   1974427  0 
snd_seq_midi           13324  0 
snd_hwdep              13604  2 snd_usb_audio,snd_hda_codec
uvcvideo               72195  0 
snd_rawmidi            30486  2 snd_usbmidi_lib,snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
joydev                 17606  0 
lib80211               14991  2 lib80211_crypt_tkip,wl
snd_seq                61621  2 snd_seq_midi,snd_seq_midi_event
snd_pcm                96625  3 snd_usb_audio,snd_hda_intel,snd_hda_codec
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
videodev               82052  1 uvcvideo
lp                     17825  0 
x38_edac               13128  0 
snd_timer              29602  2 snd_seq,snd_pcm
wacom                  42238  0 
snd_seq_device         14462  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    67382  17 snd_hda_codec_realtek,snd_usb_audio,snd_usbmidi_lib,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_rawmidi,snd_seq,snd_pcm,snd_timer,snd_seq_device
soundcore              12680  1 snd
parport                46458  3 ppdev,parport_pc,lp
v4l2_compat_ioctl32    17078  1 videodev
edac_core              53845  2 x38_edac
psmouse                73535  0 
serio_raw              13166  0 
usbhid                 46956  0 
hid                    91020  1 usbhid
firewire_ohci          40370  0 
firewire_core          62646  1 firewire_ohci
r8169                  48022  0 
floppy                 74120  0 
crc_itu_t              12707  1 firewire_core
ahci                   25951  0 
libahci                26642  1 ahci
pata_jmicron           12747  0 
joel@joel-X48-DS5:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      no wireless extensions.

eth2      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:211  Noise level:165
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0


```
```

joel@joel-X48-DS5:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Interface doesn't support scanning.

eth2      Scan completed :
          Cell 01 - Address: A0:21:B7:A3:95:50
                    ESSID:"Lun8183"
                    Mode:Managed
                    Frequency:2.427 GHz (Channel 4)
                    Quality:3/5  Signal level:-68 dBm  Noise level:-91 dBm
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD8E0050F204104A0001101044000102103B0001031047001000000000000010000000A021B7A395501021000D4E6574676561722C20496E632E10230009574E523130303076321024000456324831104200046E6F6E651054000800060050F20400011011001E574E523130303076322D564328576972656C6573732041502D322E344729100800020086103C000103
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
          Cell 02 - Address: 0C:D5:02:54:63:3F
                    ESSID:"westell7010"
                    Mode:Managed
                    Frequency=2.437 GHz (Channel 6)
                    Quality:1/5  Signal level:-81 dBm  Noise level:-78 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
          Cell 03 - Address: C0:3F:0E:5E:D0:E0
                    ESSID:"NETGEAR"
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:1/5  Signal level:-89 dBm  Noise level:-67 dBm
                    IE: Unknown: DD7F0050F204104A00011010440001011041000100103B00010310470010B819CCD4B722D0A051F34E2C46E1ECF91021000D4E4554474541522C20496E632E10230009574752363134763130102400095747523631347631301042000538333235381054000800060050F204000110110009574752363134763130100800020084
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
          Cell 04 - Address: 98:FC:11:64:A8:E4
                    ESSID:"RouterJF"
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:5/5  Signal level:-39 dBm  Noise level:-67 dBm
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD0E0050F204104A0001101044000102
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s

```

```

joel@joel-X48-DS5:~$ dmesg | grep r8
joel@joel-X48-DS5:~$ sudo dmesg | grep r8
joel@joel-X48-DS5:~$ ^C
joel@joel-X48-DS5:~$ 

```

Thank you, both for helping me out.   :D

---

