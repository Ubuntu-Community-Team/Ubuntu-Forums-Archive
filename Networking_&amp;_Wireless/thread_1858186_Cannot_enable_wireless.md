---
title: "Cannot enable wireless"
date: 2011-10-11
forum: Networking &amp; Wireless
---

### Post by rihard_marius on 2011-10-11
[SIZE=2]This is also a hardware issue, but this place is the right I think.

My wireless device is a Encore ENUWI-1x42[/SIZE] [SIZE=1][COLOR=Black][SIZE=2]

It is an external wireless adapter (usb)

[ENUWI-1X42 | ]("http://www.encore-usa.com/ma/taxonomy/term/450/all")[Wireless N150 Mini USB Adapter, 2dBi]("http://www.encore-usa.com/ma/taxonomy/term/450/all")

The system can't recognice the device, it needs a driver.

I don't have a network menu, but I ran nm-tool and it doesn't recognize the device

also ran sudo lshw -C network, there is no wireless device

ran lsusb and there is a Realtek Semiconductor Corp. device

I downloaded the driver from the page, there is a Linux driver and a windows driver.

I cannot use windows driver because I dont have ndiswrapper and I cant download it.

The linux driver is a bit complicated... I will attach the readme file.

[/SIZE]
[/COLOR][/SIZE]

---

### Post by lkjoel on 2011-10-11
Could you run the Network Info Script (in my signature), and upload the file generated?

---

### Post by rihard_marius on 2011-10-11
there is a "install.sh" script, but when I run it it gives an error, I'll attach script and error screenshot

---

### Post by lkjoel on 2011-10-11
Type this into a Terminal window:
```
sudo apt-get install gawk
bash ~/network-info.sh

```
And then could you attach the generated file?
I'll look into your install.sh problem.

---

### Post by rihard_marius on 2011-10-11
```
NetworkManager Tool

State: disconnected

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            via-rhine
  State:             unavailable
  Default:           no
  HW Address:        00:17:31:91:4D:14

  Capabilities:
    Carrier Detect:  yes
    Speed:           10 Mb/s

  Wired Properties
    Carrier:         off


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ndiswrapper
  State:             disconnected
  Default:           no
  HW Address:        00:08:54:9F:C7:B9

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    red mAx:         Infra, 00:1B:11:D1:67:D9, Freq 2437 MHz, Rate 54 Mb/s, Strength 9 WPA
    EstamosTodosLocos: Infra, 00:23:69:E9:A7:D6, Freq 2437 MHz, Rate 0 Mb/s, Strength 34
    Carmen:          Infra, 94:44:52:30:11:41, Freq 2437 MHz, Rate 54 Mb/s, Strength 21 WPA2
    CASA:            Infra, 00:21:29:A0:36:CE, Freq 2422 MHz, Rate 54 Mb/s, Strength 21 WEP
    RedFede:         Infra, 00:25:86:CB:91:FC, Freq 2437 MHz, Rate 54 Mb/s, Strength 21 WEP
    GyL:             Infra, D8:5D:4C:A6:BC:A0, Freq 2437 MHz, Rate 54 Mb/s, Strength 9 WPA WPA2
    default:         Infra, 00:17:9A:63:C0:A3, Freq 2437 MHz, Rate 54 Mb/s, Strength 7
    default:         Infra, 00:18:E7:53:59:6F, Freq 2437 MHz, Rate 54 Mb/s, Strength 21
    Fabiana y Fiorella: Infra, 74:EA:3A:F1:AB:2C, Freq 2427 MHz, Rate 54 Mb/s, Strength 21 WPA2
    Fibertel WiFi157:Infra, 1C:14:48:DB:5C:AE, Freq 2437 MHz, Rate 54 Mb/s, Strength 21 WPA
    CASA:            Infra, 00:21:29:A0:36:CE, Freq 2422 MHz, Rate 54 Mb/s, Strength 21 WPA
    Telecentro-4be0: Infra, E0:69:95:66:89:E5, Freq 2462 MHz, Rate 54 Mb/s, Strength 37 WEP
    WASC-001a6b1082be-PHILIPS: Ad-Hoc, F2:C5:8C:C9:B7:54, Freq 2462 MHz, Rate 54 Mb/s, Strength 20 WEP
    FT21145:         Infra, 00:21:00:5C:1F:69, Freq 2462 MHz, Rate 54 Mb/s, Strength 21
    AHTAN:           Infra, C8:D5:FE:70:2C:FE, Freq 2462 MHz, Rate 54 Mb/s, Strength 21 WEP
    linksys:         Infra, 00:23:69:EB:CF:4D, Freq 2437 MHz, Rate 54 Mb/s, Strength 34 WPA WPA2
    Telecentro-daa6: Infra, E0:69:95:40:94:F9, Freq 2412 MHz, Rate 54 Mb/s, Strength 35 WPA
    SANDRAC:         Infra, 00:24:8C:06:38:C6, Freq 2437 MHz, Rate 54 Mb/s, Strength 34
    EstamosTodosLocos: Infra, 00:23:69:E9:A7:D6, Freq 2437 MHz, Rate 54 Mb/s, Strength 34 WPA WPA2
    Warning!!! Virus in this Host: Infra, 1C:AF:F7:43:10:5E, Freq 2462 MHz, Rate 54 Mb/s, Strength 21 WPA WPA2
    Calzado:         Infra, 00:25:9C:51:67:59, Freq 2437 MHz, Rate 54 Mb/s, Strength 34
    Fastidio:        Infra, E0:CB:4E:52:AF:3B, Freq 2437 MHz, Rate 54 Mb/s, Strength 20
    linksys:         Infra, 00:1A:70:42:30:61, Freq 2437 MHz, Rate 54 Mb/s, Strength 35
    independiente:   Infra, 00:E0:4D:8F:54:78, Freq 2462 MHz, Rate 54 Mb/s, Strength 21 WEP
    MARIA WIFI:      Infra, E4:83:99:5F:67:3F, Freq 2447 MHz, Rate 54 Mb/s, Strength 21 WEP
    WLAN:            Infra, 00:15:E9:13:D6:F6, Freq 2437 MHz, Rate 54 Mb/s, Strength 9 WEP
    wifihagukv:      Infra, 50:67:F0:9E:33:3B, Freq 2462 MHz, Rate 54 Mb/s, Strength 45 WEP
    WifiQ:           Infra, 00:21:91:2B:33:65, Freq 2437 MHz, Rate 54 Mb/s, Strength 34 WPA
    Wifi_Casa:       Infra, 54:E6:FC:FA:DD:1A, Freq 2452 MHz, Rate 54 Mb/s, Strength 21 WPA2
    casa-jyf:        Infra, E0:69:95:48:99:14, Freq 2462 MHz, Rate 54 Mb/s, Strength 21 WPA
    dxnet2:          Infra, 00:25:9C:49:00:BA, Freq 2437 MHz, Rate 54 Mb/s, Strength 35 WPA WPA2
    Telecentro-4be0: Infra, E0:69:95:66:89:E5, Freq 2462 MHz, Rate 54 Mb/s, Strength 37 WPA
    Lorena y Carlos: Infra, 00:1B:11:3B:40:D3, Freq 2437 MHz, Rate 54 Mb/s, Strength 39 WPA WPA2
    Lucky Strike:    Infra, C8:D5:FE:6D:3C:60, Freq 2462 MHz, Rate 54 Mb/s, Strength 57 WPA


``````
  *-network
       description: Ethernet interface
       product: VT6102 [Rhine-II]
       vendor: VIA Technologies, Inc.
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 7c
       serial: 00:17:31:91:4d:14
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.5.0 duplex=half latency=64 link=no maxlatency=8 mingnt=3 multicast=yes port=MII speed=10Mbit/s
       resources: irq:23 ioport:c000(size=256) memory:fbdff800-fbdff8ff
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:08:54:9f:c7:b9
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+net8192cu driverversion=1.56+Realtek Semiconductor Corp. link=no multicast=yes wireless=IEEE 802.11g
``````
Module                  Size  Used by
ndiswrapper           192828  0 
uvcvideo               66851  0 
videodev               75143  1 uvcvideo
nls_iso8859_1          12617  1 
nls_cp437              12751  1 
vfat                   17335  1 
fat                    55505  1 vfat
snd_hda_codec_analog    75442  1 
snd_hda_intel          24140  2 
snd_hda_codec          90901  2 snd_hda_codec_analog,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80244  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
binfmt_misc            13213  1 
snd_seq_midi_event     14475  1 snd_seq_midi
radeon                896428  2 
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
ttm                    65184  1 radeon
ppdev                  12849  0 
snd                    55295  13 snd_hda_codec_analog,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm_kms_helper         40745  1 radeon
soundcore              12600  1 snd
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
drm                   180037  4 radeon,ttm,drm_kms_helper
usb_storage            43946  1 
uas                    17676  0 
parport_pc             32111  1 
asus_atk0110           17664  0 
shpchp                 32345  0 
i2c_viapro             12969  0 
i2c_algo_bit           13184  1 radeon
lp                     13349  0 
parport                36746  3 ppdev,parport_pc,lp
usbhid                 41704  0 
hid                    77084  1 usbhid
via_rhine              27131  0 
floppy                 60032  0 
sata_via               13464  2 
pata_via               13368  0 
``````
wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:48 Mb/s   Tx-Power:20 dBm   Sensitivity=0/3  
          RTS thr:off   Fragment thr:off
          Encryption key:1149-5806-40   Security mode:restricted
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

``````
rihard@Vladimir:~$ sudo iwlist
[sudo] password for rihard: 
Usage: iwlist [interface] scanning [essid NNN] [last]
              [interface] frequency 
              [interface] channel 
              [interface] bitrate 
              [interface] rate 
              [interface] encryption 
              [interface] keys 
              [interface] power 
              [interface] txpower 
              [interface] retry 
              [interface] ap 
              [interface] accesspoints 
              [interface] peers 
              [interface] event 
              [interface] auth 
              [interface] wpakeys 
              [interface] genie 
              [interface] modulation
```

---

### Post by lkjoel on 2011-10-12
It does recognize the device!
Try this in a Terminal window:
```
sudo ifconfig wlan0 down
sudo dhclient -r wlan0
sudo ifconfig wlan0 up
sudo iwconfig wlan0 essid "*YOUR_ESSID_HERE*"
sudo iwconfig wlan0 mode Managed
sudo dhclient wlan0

```

---

### Post by rihard_marius on 2011-10-13
no errors, but nothing happened

opened firefox, nothing

----------------------------------

tomorrow i'll try moving this heavy machine to a ethernet connection, the problem is that my router is an adsl, and i need a phone plug to connect it and it is 10 meters from the study
the only place in the house to do that is the kitchen, and this box can't be there
maybe updating everything will solve the problem

i'll post the news...

---

