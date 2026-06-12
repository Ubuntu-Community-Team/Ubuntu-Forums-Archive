---
title: "Ubuntu wireless not working after 1 minute"
date: 2011-10-10
forum: Networking &amp; Wireless
---

### Post by Sso011 on 2011-10-10
Hi, I am a new ubuntu user (less than two months) and is having problems with the connection about one or two weeks ago. I used to click update whenever the update manager pops out. But one day the connection drops every 3 to 5 minutes, I have been searching a lot and tried a lot of different ways to try to solve the problem including:
- Remove network manager and install wicd
- Remove wicd and go back to network manager
- "sudo iwconfig wlan0 power off" in terminal
- black listing in etc/modprobe.d (couldn't remember what i black-listed)
- Installing backports
- Tried to update everything I could

But the internet has stayed the same by disconnecting with the connection icon say it's still on.
So I decided to re-install ubuntu and thought everything will work just as smooth as how I installed it two months ago. Unfortunately, the internet connection has become worse that it drops in every minute.
I tried to send the ping but the successful packets trasmitted is 0% (out of 5).
I really hope the networking can get back to live, since as a developer, ubuntu is quite important to me..

All the information I know about my laptop is the model name: HP Pavilion dv5

**sudo lshw -C network**
```

  *-network               
       description: Wireless interface
       product: PRO/Wireless 5100 AGN [Shiloh] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 00
       serial: 00:16:ea:d2:25:e0
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn ip=192.168.1.100 latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:33 memory:de200000-de201fff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:1e:68:db:4e:19
       size: 10MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:31 ioport:6000(size=256) memory:d4010000-d4010fff(prefetchable) memory:d4000000-d400ffff(prefetchable) memory:d4020000-d402ffff(prefetchable)

```

**nm-tool**
```

NetworkManager Tool

State: connected

- Device: wlan0  [Auto NOK] ----------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlagn
  State:             connected
  Default:           yes
  HW Address:        00:16:EA:D2:25:E0

  Capabilities:
    Speed:           54 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    TP-LINK:         Infra, 54:E6:FC:FF:60:F5, Freq 2437 MHz, Rate 54 Mb/s, Strength 34 WPA WPA2
    Hawkes:          Infra, 00:22:B0:8C:B5:D6, Freq 2412 MHz, Rate 54 Mb/s, Strength 32 WEP
    Router:          Infra, 00:25:86:BD:59:B2, Freq 2437 MHz, Rate 54 Mb/s, Strength 32 WPA WPA2
    SandS:           Infra, 00:1C:DF:03:D6:56, Freq 2437 MHz, Rate 54 Mb/s, Strength 47 WPA WPA2
    *NOK:            Infra, 74:EA:3A:B1:6F:AD, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WPA
    The Hurleys:     Infra, 54:E6:FC:FF:60:94, Freq 2412 MHz, Rate 54 Mb/s, Strength 37 WPA2
    vodafone94B1:    Infra, 62:C7:14:14:94:B0, Freq 2417 MHz, Rate 54 Mb/s, Strength 40 WPA

  IPv4 Settings:
    Address:         192.168.1.100
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        00:1E:68:DB:4E:19

  Capabilities:
    Carrier Detect:  yes
    Speed:           10 Mb/s

  Wired Properties
    Carrier:         off

```

**ispci -nn | grep 0208**
```
02:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 5100 AGN [Shiloh] Network Connection [8086:4237]

```

**iwconfig**
```

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:"NOK"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 74:EA:3A:B1:6F:AD   
          Bit Rate=54 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-33 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.


```

**rfkill list all**
```

0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

```

**lsmod**
```

Module                  Size  Used by
aes_i586                7268  2 
aes_generic            26863  1 aes_i586
nls_iso8859_1           3249  2 
nls_cp437               4919  2 
vfat                    8901  2 
fat                    47767  1 vfat
binfmt_misc             6587  1 
ppdev                   5259  0 
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
rfcomm                 33421  4 
sco                     7885  2 
bridge                 45582  0 
stp                     1655  1 bridge
bnep                    9436  2 
l2cap                  30624  16 rfcomm,bnep
snd_hda_codec_nvhdmi     3840  1 
snd_hda_codec_idt      51914  1 
arc4                    1153  2 
snd_hda_intel          21877  2 
snd_hda_codec          74201  3 snd_hda_codec_nvhdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70662  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26726  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
iwlagn                105566  0 
nouveau               467048  2 
iwlcore               105922  1 iwlagn
ttm                    49943  1 nouveau
jmb38x_ms               7311  0 
drm_kms_helper         29297  1 nouveau
snd                    54148  16 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
mac80211              204922  2 iwlagn,iwlcore
joydev                  8708  0 
uvcvideo               56990  0 
videodev               34361  1 uvcvideo
v4l1_compat            13251  2 uvcvideo,videodev
psmouse                63245  0 
serio_raw               3978  0 
btusb                  10925  2 
bluetooth              49892  9 rfcomm,sco,bnep,l2cap,btusb
memstick                8237  1 jmb38x_ms
sdhci_pci               5470  0 
sdhci                  15462  1 sdhci_pci
lirc_ene0100            6536  0 
lirc_dev                8884  1 lirc_ene0100
video                  17375  0 
output                  1871  1 video
drm                   162471  4 nouveau,ttm,drm_kms_helper
i2c_algo_bit            5028  1 nouveau
soundcore               6620  1 snd
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
hp_accel               11144  0 
lis3lv02d               6007  1 hp_accel
input_polldev           2482  1 lis3lv02d
led_class               2864  3 iwlcore,sdhci,hp_accel
cfg80211              126485  3 iwlagn,iwlcore,mac80211
intel_agp              24177  0 
agpgart                31724  3 ttm,drm,intel_agp
lp                      7028  0 
parport                32635  2 ppdev,lp
usbhid                 36110  0 
hid                    67032  1 usbhid
usb_storage            39425  2 
ohci1394               26950  0 
ahci                   32008  2 
ieee1394               81181  1 ohci1394
r8169                  33884  0 
mii                     4381  1 r8169


```

REALLY APPRECIATE YOUR HELP !! THANKS !!!!!

---

### Post by Sso011 on 2011-10-10
OOOOOOOOOOOOOOOOO

It's working now thanks to this thread =D
Will keep add on to this post if there is anymore problem ...

[http://ubuntuforums.org/showpost.php?p=9607280&postcount=2](http://ubuntuforums.org/showpost.php?p=9607280&postcount=2)

---

