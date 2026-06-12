---
title: "Unable to connect to wireless router since upgrade to 13.04"
date: 2013-04-27
forum: Networking &amp; Wireless
---

### Post by fidelandche on 2013-04-27
Hi all,

Yesterday I upgraded both mine and my partners laptops to 13.04, now we are both unable to connect to the wireless router (BT HomeHub 3)Prior to the upgrade we had no problems with connecting. When you click on the wireless icon the router is there but we just cannot connect, we can connect via ethernet cable and as it is BT we can connect via their free hotspots  When I go on to system settings on my Toshiba satellite L300 and go to network settings my router is out of range, doing the same on my partners Samsung N150 plus netbook  the router is in range but the netbook just will not connect. When checking additional drivers I do not have any proprietary drivers in use, but the Samsung has a Broadcom BCM4313 802.1b/g/n Wireless LAN Controller, however I have tried to use that driver on the Samsung but there is a message saying this device is not working and as soon as I try to use it it just goes back to do not use the device. So not really sure where to go from here.

Cheers.

---

### Post by praseodym on 2013-04-27
Please show the outputs of these commands for both notebooks seperately:
```

lspci -nnk | grep -iA2 net
lsmod
iwconfig
rfkill list
```

---

### Post by fidelandche on 2013-04-27
oddly after turning the laptops off then on again after a few hours, they have now both connected to the router, so not really sure of the issue. However here is the output of the Toshiba.


```
andyandmillie@andyandmillie-Satellite-L300:~$ lspci -nnk | grep -iA2 net02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
	Subsystem: Toshiba America Info Systems Device [1179:ff66]
	Kernel driver in use: r8169
andyandmillie@andyandmillie-Satellite-L300:~$ lsmod
Module                  Size  Used by
parport_pc             27504  0 
ppdev                  12817  0 
rfcomm                 37420  0 
bnep                   17669  2 
bluetooth             202069  10 bnep,rfcomm
dm_crypt               22321  0 
binfmt_misc            17260  1 
joydev                 17097  0 
arc4                   12543  2 
snd_hda_codec_realtek    63791  1 
rtl8187                60184  0 
snd_hda_intel          38307  3 
snd_hda_codec         117580  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13272  1 snd_hda_codec
mac80211              526519  1 rtl8187
snd_pcm                80890  2 snd_hda_codec,snd_hda_intel
cfg80211              436177  2 mac80211,rtl8187
eeprom_93cx6           13168  1 rtl8187
snd_page_alloc         14230  2 snd_pcm,snd_hda_intel
snd_seq_midi           13132  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_rawmidi            25114  1 snd_seq_midi
snd_seq                51280  2 snd_seq_midi_event,snd_seq_midi
toshiba_acpi           18270  0 
sparse_keymap          13658  1 toshiba_acpi
wmi                    18590  1 toshiba_acpi
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              24411  2 snd_pcm,snd_seq
snd                    56485  15 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device
mac_hid                13037  0 
microcode              18286  0 
lpc_ich                16925  0 
psmouse                81038  0 
coretemp               13131  0 
serio_raw              13031  0 
soundcore              12600  1 snd
lp                     13299  0 
parport                40753  3 lp,ppdev,parport_pc
i915                  535507  3 
i2c_algo_bit           13197  1 i915
drm_kms_helper         47545  1 i915
r8169                  61531  0 
video                  18894  1 i915
drm                   228750  4 i915,drm_kms_helper
ahci                   25507  2 
libahci                26108  1 ahci
andyandmillie@andyandmillie-Satellite-L300:~$ iwconfig
wlan0     IEEE 802.11bg  ESSID:"BTHub3-RKM6"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:01:3B:96:2A:22   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-37 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:14  Invalid misc:20   Missed beacon:0


lo        no wireless extensions.


eth0      no wireless extensions.


andyandmillie@andyandmillie-Satellite-L300:~$ rfkill list
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
andyandmillie@andyandmillie-Satellite-L300:~$
```

---

### Post by fidelandche on 2013-04-27
Here is the output from the Samsung

```
millie@millie-N150P-N210P-N220P:~$ lspci -nnk | grep -iA2 net05:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)
	Subsystem: Wistron NeWeb Corp. Device [185f:051a]
	Kernel driver in use: bcma-pci-bridge
09:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller [11ab:4354]
	Subsystem: Samsung Electronics Co Ltd Notebook N150P [144d:c072]
	Kernel driver in use: sky2
millie@millie-N150P-N210P-N220P:~$ lsmod
Module                  Size  Used by
easy_slow_down_manager    12985  0 
snd_hrtimer            12648  1 
arc4                   12543  2 
brcmsmac              521468  0 
cordic                 12518  1 brcmsmac
brcmutil               14355  1 brcmsmac
mac80211              526519  1 brcmsmac
cfg80211              436177  2 brcmsmac,mac80211
coretemp               13131  0 
joydev                 17097  0 
gpio_ich               13236  0 
snd_hda_codec_realtek    63791  1 
samsung_backlight      13685  0 
snd_hda_intel          38307  3 
parport_pc             27504  0 
ppdev                  12817  0 
snd_hda_codec         117580  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13272  1 snd_hda_codec
microcode              18286  0 
snd_pcm                80890  2 snd_hda_codec,snd_hda_intel
snd_page_alloc         14230  2 snd_pcm,snd_hda_intel
bnep                   17669  2 
snd_seq_midi           13132  0 
uvcvideo               71279  0 
snd_seq_midi_event     14475  1 snd_seq_midi
videobuf2_vmalloc      12920  1 uvcvideo
videobuf2_memops       13042  1 videobuf2_vmalloc
videobuf2_core         39161  1 uvcvideo
rfcomm                 37420  12 
snd_rawmidi            25114  1 snd_seq_midi
videodev               95806  2 uvcvideo,videobuf2_core
snd_seq                51280  3 snd_seq_midi_event,snd_seq_midi
i915                  535507  3 
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
video                  18894  1 i915
snd_timer              24411  3 snd_hrtimer,snd_pcm,snd_seq
drm_kms_helper         47545  1 i915
psmouse                81038  0 
binfmt_misc            17260  1 
bcma                   39645  1 brcmsmac
mac_hid                13037  0 
serio_raw              13031  0 
btusb                  17986  0 
drm                   228750  4 i915,drm_kms_helper
bluetooth             202069  22 bnep,btusb,rfcomm
snd                    56485  16 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device
lpc_ich                16925  0 
i2c_algo_bit           13197  1 i915
soundcore              12600  1 snd
lp                     13299  0 
parport                40753  3 lp,ppdev,parport_pc
ahci                   25507  2 
libahci                26108  1 ahci
sky2                   52846  0 
millie@millie-N150P-N210P-N220P:~$ iwconfig
wlan0     IEEE 802.11bgn  ESSID:"BTHub3-RKM6"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:01:3B:96:2A:22   
          Bit Rate=72.2 Mb/s   Tx-Power=19 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=56/70  Signal level=-54 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:47   Missed beacon:0


lo        no wireless extensions.


eth0      no wireless extensions.


millie@millie-N150P-N210P-N220P:~$ rfkill list
0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
millie@millie-N150P-N210P-N220P:~$ 



```

---

### Post by praseodym on 2013-04-28
Obviously, the Toshiba has a Realtek device connected via USB. Check
```

lsusb
```
For the Samsung you need to install the missing firmware:```

wget http://media.cdn.ubuntu-de.org/forum/attachments/39/45/5007272-Broadcom_Firmware_fae7121.tar.gz
sudo tar xvf 5007272-Broadcom_Firmware_fae7121.tar.gz -C /lib/firmware 
```

---

### Post by fidelandche on 2013-04-28
Here is the output from that code

```
andyandmillie@andyandmillie-Satellite-L300:~$ lsusbBus 002 Device 002: ID 0bda:8197 Realtek Semiconductor Corp. RTL8187B Wireless Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
andyandmillie@andyandmillie-Satellite-L300:~$ 





```

---

### Post by praseodym on 2013-04-28
The driver for the Realtek device should work...Please show from the Toshiba:
```

sudo iwlist scan
ifconfig -a
dmesg | grep rtl8
cat /etc/network/interfaces
cat /etc/resolv.conf
route -n
```

---

### Post by fidelandche on 2013-04-28
Here's the output

```
andyandmillie@andyandmillie-Satellite-L300:~$ sudo iwlist scan[sudo] password for andyandmillie: 
Sorry, try again.
[sudo] password for andyandmillie: 
Sorry, try again.
[sudo] password for andyandmillie: 
wlan0     Scan completed :
          Cell 01 - Address: 00:01:3B:96:2A:22
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=-39 dBm  
                    Encryption key:on
                    ESSID:"BTHub3-RKM6"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000001c1902f180
                    Extra: Last beacon: 508ms ago
                    IE: Unknown: 000B4254487562332D524B4D36
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1AAC011BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601001300000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101890003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DDA70050F204104A000110104400010210570001001041000100103B00010310470010565AA94967C14C0EAA8FF349E6F5931110210002425410230017486F6D652048756220332E30204D756C7469204D6F646510240010425420486F6D652048756220332E3041104200122B3035383732302B313133303031303037391054000800060050F204000110110010425420486F6D652048756220332E3041100800020084103C000101
          Cell 02 - Address: 00:18:4D:3F:68:DA
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=59/70  Signal level=-51 dBm  
                    Encryption key:on
                    ESSID:"jansnetwork"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000005e5209bdbd1
                    Extra: Last beacon: 5952ms ago
                    IE: Unknown: 000B6A616E736E6574776F726B
                    IE: Unknown: 010582848B962C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 32080C1218243048606C
          Cell 03 - Address: 02:81:D8:7E:9A:62
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=-39 dBm  
                    Encryption key:off
                    ESSID:"BTWiFi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000741a467ec
                    Extra: Last beacon: 3972ms ago
                    IE: Unknown: 0006425457694669
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1AAC011BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606001100000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD180050F2020101870003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
          Cell 04 - Address: 02:24:17:E6:DF:BC
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=43/70  Signal level=-67 dBm  
                    Encryption key:off
                    ESSID:"BTWiFi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000023afcd82ead
                    Extra: Last beacon: 3004ms ago
                    IE: Unknown: 0006425457694669
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030107
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180200F0050000
                    IE: Unknown: DD180050F2020101880003A4000027A4000042435E0062322F00
          Cell 05 - Address: 02:24:17:E6:DF:BD
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=42/70  Signal level=-68 dBm  
                    Encryption key:off
                    ESSID:"BTWiFi-with-FON"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000023afcd83437
                    Extra: Last beacon: 3004ms ago
                    IE: Unknown: 000F4254576946692D776974682D464F4E
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030107
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180200F0050000
                    IE: Unknown: DD180050F2020101880003A4000027A4000042435E0062322F00
          Cell 06 - Address: 00:81:D8:7E:9A:62
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=-39 dBm  
                    Encryption key:on
                    ESSID:"BTHub3-9QQT"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000741b26920
                    Extra: Last beacon: 3000ms ago
                    IE: Unknown: 000B4254487562332D39515154
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1AAC011BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606001100000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101870003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DDA70050F204104A000110104400010210570001001041000100103B00010310470010565AA94967C14C0EAA8FF349E6F5931110210002425410230017486F6D652048756220332E30204D756C7469204D6F646510240010425420486F6D652048756220332E3041104200122B3035383732302B313234303030323331371054000800060050F204000110110010425420486F6D652048756220332E3041100800020084103C000101
          Cell 07 - Address: 12:81:D8:7E:9A:62
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=-39 dBm  
                    Encryption key:off
                    ESSID:"BTWiFi-with-FON"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000741b36c42
                    Extra: Last beacon: 2988ms ago
                    IE: Unknown: 000F4254576946692D776974682D464F4E
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1AAC011BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606001100000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD180050F2020101870003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
          Cell 08 - Address: 02:FE:F4:29:99:08
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=53/70  Signal level=-57 dBm  
                    Encryption key:off
                    ESSID:"BTWiFi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000015420903d
                    Extra: Last beacon: 1024ms ago
                    IE: Unknown: 0006425457694669
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1AAC011BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B080000000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD180050F2020101890003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
          Cell 09 - Address: 12:FE:F4:29:99:08
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=48/70  Signal level=-62 dBm  
                    Encryption key:off
                    ESSID:"BTWiFi-with-FON"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000154209948
                    Extra: Last beacon: 1020ms ago
                    IE: Unknown: 000F4254576946692D776974682D464F4E
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1AAC011BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B080000000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD180050F2020101890003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F


lo        Interface doesn't support scanning.


eth0      Interface doesn't support scanning.


andyandmillie@andyandmillie-Satellite-L300:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:1e:33:81:a6:8b  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:1188 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1188 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:121268 (121.2 KB)  TX bytes:121268 (121.2 KB)


wlan0     Link encap:Ethernet  HWaddr 00:22:5f:48:1c:14  
          inet addr:192.168.1.65  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::222:5fff:fe48:1c14/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:793240 errors:0 dropped:0 overruns:0 frame:0
          TX packets:501808 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1063769118 (1.0 GB)  TX bytes:50348912 (50.3 MB)


andyandmillie@andyandmillie-Satellite-L300:~$ dmesg | grep rtl8
[   22.471822] ieee80211 phy0: hwaddr 00:22:5f:48:1c:14, RTL8187BvE V0 + rtl8225z2, rfkill mask 4
[   22.496087] rtl8187: Customer ID is 0x04
[   22.502966] rtl8187: wireless switch is on
[   22.503864] usbcore: registered new interface driver rtl8187
andyandmillie@andyandmillie-Satellite-L300:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback


andyandmillie@andyandmillie-Satellite-L300:~$ cat /etc/resolv.conf
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.1.1
search home
andyandmillie@andyandmillie-Satellite-L300:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.254   0.0.0.0         UG    0      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0
andyandmillie@andyandmillie-Satellite-L300:~$ 
```

---

### Post by praseodym on 2013-04-28
Try pure WPA2-AES (CCMP) encryption, if possible. Maybe changing the (fixed!!!) channel to 13?!

---

