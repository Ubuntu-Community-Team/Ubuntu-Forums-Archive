---
title: "wifi wont Authenticate at 2nd address on talktalk"
date: 2012-06-16
forum: Networking &amp; Wireless
---

### Post by ianma on 2012-06-16
Hi all

I have just set up a little netbook for Grandson at my home and it works perfect when connecting to the internet.

However at his house it can see the talktalk router and when I enter the wep key it fails as if the key entered is incorrect however that key works ok on a windows machine.

I am a little lost on what to try next does anyone have any ideas as I presume something is not compatible with the talktalk router which I a dlink router but it worked perfect on my sky router.

I have no technical knowledge on routers at all.

Thanks

Ian

---

### Post by wildmanne39 on 2012-06-23
Hi, please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:

```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
nm-tool
lsusb
iwconfig
rfkill list all
lsmod
```
by clicking on new reply and click # then paste the information between the brackets.
Thank you

---

### Post by ianma on 2012-07-02
Hi many thanks for the reply ok here are the results of the talktalk wireless router that wont authenticate

```
harrison@harrison-laptop:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04 LTS"
Linux harrison-laptop 3.2.0-26-generic #41-Ubuntu SMP Thu Jun 14 16:26:01 UTC 2012 i686 i686 i386 GNU/Linux
harrison@harrison-laptop:~$ lspci -nnk | grep -iA2 net
01:06.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
    Subsystem: QUANTA Computer Inc Device [152d:0771]
    Kernel driver in use: 8139too
harrison@harrison-laptop:~$ nm-tool

NetworkManager Tool

State: disconnected

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8187
  State:             disconnected
  Default:           no
  HW Address:        00:17:C4:28:64:9C

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    TALKTALK-721BC5: Infra, 84:C9:B2:72:1B:C5, Freq 2412 MHz, Rate 54 Mb/s, Strength 100 WPA WPA2
    SKY4A3AC:        Infra, 90:01:3B:74:A3:AD, Freq 2437 MHz, Rate 54 Mb/s, Strength 69 WPA WPA2
    talktalk1234:    Infra, 00:1F:9F:43:52:51, Freq 2412 MHz, Rate 54 Mb/s, Strength 69 WPA WPA2
    BTHub3-JC4C:     Infra, 00:AC:54:D8:7C:9A, Freq 2462 MHz, Rate 54 Mb/s, Strength 62 WPA WPA2
    virginmedia8512432: Infra, C4:3D:C7:46:1D:E8, Freq 2462 MHz, Rate 54 Mb/s, Strength 42 WPA WPA2
    SKY19427:        Infra, 5C:D9:98:BD:7A:A9, Freq 2437 MHz, Rate 54 Mb/s, Strength 47 WPA WPA2
    BTOpenzone-H:    Infra, 02:AC:54:D8:7C:9A, Freq 2462 MHz, Rate 54 Mb/s, Strength 59
    BTFON:           Infra, 12:AC:54:D8:7C:9A, Freq 2462 MHz, Rate 54 Mb/s, Strength 57
    BTBusinessHub-338: Infra, 00:21:7C:87:9D:11, Freq 2437 MHz, Rate 54 Mb/s, Strength 50 WEP


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            8139too
  State:             unavailable
  Default:           no
  HW Address:        00:1E:68:33:67:77

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


harrison@harrison-laptop:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0408:030c Quanta Computer, Inc. HP Webcam
Bus 001 Device 003: ID 0bda:8189 Realtek Semiconductor Corp. RTL8187B Wireless 802.11g 54Mbps Network Adapter
harrison@harrison-laptop:~$ iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
eth0      no wireless extensions.

harrison@harrison-laptop:~$ rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
harrison@harrison-laptop:~$ lsmod
Module                  Size  Used by
via                    45249  0 
drm                   197692  1 via
snd_hrtimer            12648  1 
vesafb                 13516  1 
snd_hda_codec_realtek   174055  1 
snd_hda_intel          32765  1 
snd_hda_codec         109562  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80845  2 snd_hda_intel,snd_hda_codec
arc4                   12473  2 
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  3 snd_seq_midi,snd_seq_midi_event
rtl8187                56323  0 
snd_timer              28931  3 snd_hrtimer,snd_pcm,snd_seq
mac80211              436455  1 rtl8187
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    62064  12 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
cfg80211              178679  2 rtl8187,mac80211
uvcvideo               67203  0 
videodev               86588  1 uvcvideo
eeprom_93cx6           12653  1 rtl8187
psmouse                87213  0 
soundcore              14635  1 snd
serio_raw              13027  0 
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
shpchp                 32325  0 
i2c_viapro             12969  0 
rfcomm                 38139  0 
bnep                   17830  2 
parport_pc             32114  0 
bluetooth             158438  8 rfcomm,bnep
ppdev                  12849  0 
video                  19068  0 
mac_hid                13077  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
8139too                23283  0 
8139cp                 22633  0 
pata_via               13428  2 
via_sdmmc              17426  0 
harrison@harrison-laptop:~$ 

```And just in case this helps here are the same results from my house where everything works perfect

```
harrison@harrison-laptop:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04 LTS"
Linux harrison-laptop 3.2.0-26-generic #41-Ubuntu SMP Thu Jun 14 16:26:01 UTC 2012 i686 i686 i386 GNU/Linux
harrison@harrison-laptop:~$ lspci -nnk | grep -iA2 net
01:06.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
    Subsystem: QUANTA Computer Inc Device [152d:0771]
    Kernel driver in use: 8139too
harrison@harrison-laptop:~$ nm-tool

NetworkManager Tool

State: connected (global)

- Device: wlan0  [SKY73424] ----------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8187
  State:             connected
  Default:           yes
  HW Address:        00:17:C4:28:64:9C

  Capabilities:
    Speed:           54 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    *SKY73424:       Infra, 00:1B:2F:9E:05:16, Freq 2437 MHz, Rate 54 Mb/s, Strength 82 WPA

  IPv4 Settings:
    Address:         192.168.0.7
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             192.168.0.1


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            8139too
  State:             unavailable
  Default:           no
  HW Address:        00:1E:68:33:67:77

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


harrison@harrison-laptop:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0408:030c Quanta Computer, Inc. HP Webcam
Bus 001 Device 003: ID 0bda:8189 Realtek Semiconductor Corp. RTL8187B Wireless 802.11g 54Mbps Network Adapter
harrison@harrison-laptop:~$ iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"SKY73424"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:1B:2F:9E:05:16   
          Bit Rate=48 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-38 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:3  Invalid misc:31   Missed beacon:0

eth0      no wireless extensions.

harrison@harrison-laptop:~$ rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
harrison@harrison-laptop:~$ lsmod
Module                  Size  Used by
snd_hrtimer            12648  1 
via                    45249  0 
drm                   197692  1 via
vesafb                 13516  1 
snd_hda_codec_realtek   174055  1 
snd_hda_intel          32765  1 
snd_hda_codec         109562  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80845  2 snd_hda_intel,snd_hda_codec
arc4                   12473  2 
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  3 snd_seq_midi,snd_seq_midi_event
rtl8187                56323  0 
mac80211              436455  1 rtl8187
snd_timer              28931  3 snd_hrtimer,snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
uvcvideo               67203  0 
snd                    62064  12 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
cfg80211              178679  2 rtl8187,mac80211
videodev               86588  1 uvcvideo
eeprom_93cx6           12653  1 rtl8187
soundcore              14635  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
shpchp                 32325  0 
psmouse                87213  0 
serio_raw              13027  0 
i2c_viapro             12969  0 
bnep                   17830  2 
bluetooth             158438  7 bnep
parport_pc             32114  0 
ppdev                  12849  0 
video                  19068  0 
mac_hid                13077  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
8139too                23283  0 
8139cp                 22633  0 
pata_via               13428  2 
via_sdmmc              17426  0 

```If any of this helps fix the problem it would be great.

Thanks all

Ian

---

### Post by wildmanne39 on 2012-07-02
Hi, change the encryption in the router to just wpa2, then set the channel to 1 or 11 in the router.
Thanks

---

### Post by ianma on 2012-09-27
Hi again

Well I logged into the router and changed the setting but sadly still not able to connect. I tried channel 1, 6 and 11 with it set to wpa2 only.

I have redone the tests again while the router was on wpa2 only in case this offers any clues, the good news is he will be getting a new laptop for Christmas and the thing does work if plugged into the router with the cable.

Thanks for all advice.

Cheers

Ian

**RESULTS**

```
harrison@harrison-laptop:~$ cat /etc/lsb-release; uname -
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04.1 LTS"
uname: extra operand `-'
Try `uname --help' for more information.
harrison@harrison-laptop:~$ lspci -nnk | grep -iA2 net
01:06.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
    Subsystem: QUANTA Computer Inc Device [152d:0771]
    Kernel driver in use: 8139too
harrison@harrison-laptop:~$ nm-tool

NetworkManager Tool

State: disconnected

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8187
  State:             disconnected
  Default:           no
  HW Address:        00:17:C4:28:64:9C

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    TheAbbott's:     Infra, 84:C9:B2:72:1B:C5, Freq 2437 MHz, Rate 54 Mb/s, Strength 97 WPA WPA2
    SKY4A3AC:        Infra, 90:01:3B:74:A3:AD, Freq 2412 MHz, Rate 54 Mb/s, Strength 70 WPA WPA2
    talktalk1234:    Infra, 00:1F:9F:43:52:51, Freq 2412 MHz, Rate 54 Mb/s, Strength 65 WPA WPA2
    SKY19427:        Infra, 5C:D9:98:BD:7A:A9, Freq 2462 MHz, Rate 54 Mb/s, Strength 62 WPA WPA2
    BTHub3-JC4C:     Infra, 00:AC:54:D8:7C:9A, Freq 2437 MHz, Rate 54 Mb/s, Strength 60 WPA WPA2
    BTWiFi-with-FON: Infra, 12:AC:54:D8:7C:9A, Freq 2437 MHz, Rate 54 Mb/s, Strength 59
    BTWiFi:          Infra, 02:AC:54:D8:7C:9A, Freq 2437 MHz, Rate 54 Mb/s, Strength 54
    BTBusinessHub-338: Infra, 00:21:7C:87:9D:11, Freq 2442 MHz, Rate 54 Mb/s, Strength 49 WEP


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            8139too
  State:             unavailable
  Default:           no
  HW Address:        00:1E:68:33:67:77

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


harrison@harrison-laptop:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0408:030c Quanta Computer, Inc. HP Webcam
Bus 001 Device 003: ID 0bda:8189 Realtek Semiconductor Corp. RTL8187B Wireless 802.11g 54Mbps Network Adapter
Bus 001 Device 004: ID 13fe:4100 Kingston Technology Company Inc. 
harrison@harrison-laptop:~$ iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
eth0      no wireless extensions.

harrison@harrison-laptop:~$ rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
harrison@harrison-laptop:~$ lsmod
Module                  Size  Used by
nls_iso8859_1          12617  1 
nls_cp437              12751  1 
vfat                   17308  1 
fat                    55605  1 vfat
uas                    17828  0 
usb_storage            39646  1 
snd_hrtimer            12648  1 
via                    45249  0 
drm                   197692  1 via
vesafb                 13516  1 
snd_hda_codec_realtek   174222  1 
snd_hda_intel          32765  1 
snd_hda_codec         109562  2 snd_hda_codec_realtek,snd_hda_intel
arc4                   12473  2 
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80845  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
rtl8187                56323  0 
snd_rawmidi            25424  1 snd_seq_midi
mac80211              436455  1 rtl8187
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  3 snd_seq_midi,snd_seq_midi_event
cfg80211              178679  2 rtl8187,mac80211
snd_timer              28931  3 snd_hrtimer,snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
uvcvideo               67203  0 
eeprom_93cx6           12653  1 rtl8187
videodev               86588  1 uvcvideo
snd                    62064  12 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                87213  0 
serio_raw              13027  0 
shpchp                 32325  0 
soundcore              14635  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
i2c_viapro             12969  0 
rfcomm                 38139  0 
bnep                   17830  2 
bluetooth             158438  10 rfcomm,bnep
parport_pc             32114  0 
ppdev                  12849  0 
video                  19068  0 
mac_hid                13077  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
8139too                23283  0 
8139cp                 22633  0 
via_sdmmc              17426  0 
pata_via               13428  2 
harrison@harrison-laptop:~$ 

```

---

