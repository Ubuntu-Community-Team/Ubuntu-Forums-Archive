---
title: "WLAN doesn't find a Network to connect"
date: 2010-12-11
forum: Networking &amp; Wireless
---

### Post by pepperMINT123 on 2010-12-11
Hello,

recently I risked a look to the Linux world and I'm happy so far, but now I've got a Problem, I'm unable to solve by myself.

I installed Mint (Julia) on my old Laptop to test Linux. The Laptop has a very old PCMCIA WLAN Card with a Realtek rtl8180 chipset. Everything seems to run perfectly so far with one exception: the WLAN doesn't find any Network to connect although the card and the driver seem to be installed correctly.

Here some code from the terminal:

```
lspci
00:00.0 Host bridge: ATI Technologies Inc RS200/RS200M AGP Bridge [IGP 340M] (rev 02)
00:01.0 PCI bridge: ATI Technologies Inc PCI Bridge [IGP 340M]
00:02.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
00:03.0 Modem: ALi Corporation M5457 AC'97 Modem Controller
00:04.0 Multimedia audio controller: ALi Corporation M5451 PCI AC-Link Controller Audio Device (rev 02)
00:06.0 Bridge: ALi Corporation M7101 Power Management Controller [PMU]
00:07.0 ISA bridge: ALi Corporation M1533/M1535/M1543 PCI to ISA Bridge [Aladdin IV/V/V+]
00:0b.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5901 100Base-TX (rev 01)
00:0c.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controller
00:0f.0 IDE interface: ALi Corporation M5229 IDE (rev c4)
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon IGP 330M/340M/350M
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8180L 802.11b MAC (rev 20)

```
```
iwconfig wlan0
wlan0     IEEE 802.11b  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

```
```
lsmod
Module                  Size  Used by
binfmt_misc             6599  1 
dm_crypt               11385  0 
arc4                    1165  2 
snd_ali5451            15875  2 
snd_ac97_codec         99227  1 snd_ali5451
ac97_bus                1014  1 snd_ac97_codec
rtl8180                27401  0 
snd_pcm                71475  2 snd_ali5451,snd_ac97_codec
mac80211              231541  1 rtl8180
thinkpad_acpi          67659  0 
snd_seq_midi            4588  0 
eeprom_93cx6            1345  1 rtl8180
snd_rawmidi            17783  1 snd_seq_midi
cfg80211              144470  2 rtl8180,mac80211
snd_seq_midi_event      6047  1 snd_seq_midi
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
ppdev                   5556  0 
snd_timer              19067  2 snd_pcm,snd_seq
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
pcmcia                 35973  0 
psmouse                59033  0 
snd                    49006  12 snd_ali5451,snd_ac97_codec,snd_pcm,thinkpad_acpi,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
led_class               2633  1 thinkpad_acpi
yenta_socket           21518  0 
parport_pc             26058  1 
nvram                   6342  1 thinkpad_acpi
serio_raw               4022  0 
pcmcia_rsrc            10566  1 yenta_socket
soundcore                880  1 snd
pcmcia_core            14657  3 pcmcia,yenta_socket,pcmcia_rsrc
lp                      7342  0 
i2c_ali15x3             5190  0 
i2c_ali1535             4865  0 
shpchp                 29886  0 
snd_page_alloc          7120  1 snd_pcm
parport                31492  3 ppdev,parport_pc,lp
dm_raid45              81721  0 
xor                    15136  1 dm_raid45
btrfs                 489451  0 
zlib_deflate           19266  1 btrfs
crc32c                  2531  1 
libcrc32c                887  1 btrfs
radeon                825934  2 
ttm                    56633  1 radeon
usbhid                 36882  0 
drm_kms_helper         30200  1 radeon
drm                   168054  4 radeon,ttm,drm_kms_helper
tg3                   123310  0 
hid                    67742  1 usbhid
ati_agp                 5202  1 
pata_ali                7976  2 
video                  18712  0 
i2c_algo_bit            5168  1 radeon
output                  1883  1 video
agpgart                32011  3 ttm,drm,ati_agp

```
```
nm-tool

NetworkManager Tool

State: connected

- Device: eth0  [Auto eth0] ----------------------------------------------------
  Type:              Wired
  Driver:            tg3
  State:             connected
  Default:           yes
  HW Address:        00:06:1B:CB:D5:57

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.0.195
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             192.168.0.1


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8180
  State:             disconnected
  Default:           no
  HW Address:        00:50:FC:D0:D1:37

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 

```"State: disconnected" may be an interesting fact. How can I force nm-tool to connect to a wireless network it doesn't find?

because:

```
iwlist wlan0 scan
wlan0     No scan results

```:-(

The WLAN card has two LEDs. One named "TX/Rx" and one named "Link". "Tx/Rx" blinks (how it should) but "Link" doesn't (what is bad).

Do you have an idea?

THX a lot.

---

### Post by pepperMINT123 on 2010-12-12
Doesn't someone have an idea?

---

