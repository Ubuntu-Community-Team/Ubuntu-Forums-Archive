---
title: "Slow wifi connection (ubuntu 13.04)"
date: 2013-07-19
forum: Networking &amp; Wireless
---

### Post by PhilippSchaffrath on 2013-07-19
Good evening,

my wifi connection is very slow, wired connection has normal speed. I have tryed some possible solutions i found, but nothing worked yet.

Here are some information:

```

cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=13.04
DISTRIB_CODENAME=raring
DISTRIB_DESCRIPTION="Ubuntu 13.04"
Linux root 3.8.0-19-generic #29-Ubuntu SMP Wed Apr 17 18:16:28 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

```

```

lspci -nnk | grep -iA2 net
03:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. Yukon Optima 88E8059 [PCIe Gigabit Ethernet Controller with AVB] [11ab:4381] (rev 11)
    Subsystem: ASUSTeK Computer Inc. Device [1043:8439]
    Kernel driver in use: sky2

```

```

lsusb
Bus 001 Device 003: ID 0bda:8172 Realtek Semiconductor Corp. RTL8191SU 802.11n WLAN Adapter
Bus 004 Device 002: ID 1b1c:1b02 Corsair 
Bus 005 Device 002: ID 046d:c066 Logitech, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 009 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub

```

```

iwconfig
eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"***"  Nickname:"rtl_wifi"
          Mode:Managed  Frequency:2.412 GHz  Access Point: ***
          Bit Rate:54 Mb/s   Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=91/100  Signal level=42/100  Noise level=0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

```

rfkill list all

```

```

lsmod
Module                  Size  Used by
iwlwifi               173477  0 
rtl8192cu              67699  0 
rtlwifi                79673  1 rtl8192cu
rtl8192c_common        48779  1 rtl8192cu
mac80211              606457  3 rtlwifi,rtl8192c_common,rtl8192cu
cfg80211              510937  3 iwlwifi,mac80211,rtlwifi
snd_hda_codec_hdmi     36913  4 
parport_pc             28152  0 
ppdev                  17073  0 
rfcomm                 42641  0 
bnep                   18036  2 
bluetooth             228619  10 bnep,rfcomm
joydev                 17377  0 
hid_generic            12540  0 
usbhid                 47074  0 
hid                   101002  2 hid_generic,usbhid
r8712u                187938  0 
kvm_amd                59717  0 
kvm                   443165  1 kvm_amd
snd_hda_codec_via      51018  1 
adt7475                31316  0 
hwmon_vid              12783  1 adt7475
sp5100_tco             13735  0 
microcode              22881  0 
psmouse                95870  0 
serio_raw              13215  0 
snd_hda_intel          39619  3 
asus_atk0110           17646  0 
snd_hda_codec         136453  3 snd_hda_codec_hdmi,snd_hda_codec_via,snd_hda_intel
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30180  1 snd_seq_midi
snd_hwdep              13602  1 snd_hda_codec
snd_seq                61554  2 snd_seq_midi_event,snd_seq_midi
snd_pcm                97451  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
k10temp                13126  0 
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
edac_core              62003  0 
edac_mce_amd           23114  0 
snd_timer              29425  2 snd_pcm,snd_seq
i2c_piix4              13266  0 
snd                    68876  16 snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_hda_codec_via,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device
nouveau               939088  4 
mxm_wmi                13021  1 nouveau
video                  19390  1 nouveau
ttm                    83187  1 nouveau
drm_kms_helper         49394  1 nouveau
drm                   286313  6 ttm,drm_kms_helper,nouveau
soundcore              12680  1 snd
i2c_algo_bit           13413  1 nouveau
wmi                    19070  2 mxm_wmi,nouveau
mac_hid                13205  0 
lp                     17759  0 
parport                46345  3 lp,ppdev,parport_pc
firewire_ohci          40103  0 
firewire_core          64508  1 firewire_ohci
crc_itu_t              12707  1 firewire_core
pata_acpi              13038  0 
sky2                   57977  0 
pata_jmicron           12758  0 
ahci                   25731  2 
libahci                31364  1 ahci

```

```

nm-tool

NetworkManager Tool

State: connected (global)

- Device: wlan0  [***] -------------------------------------------------
  Type:              802.11 WiFi
  Driver:            r8712u
  State:             connected
  Default:           yes
  HW Address:        ***

  Capabilities:
    Speed:           54 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    ***:  Infra, 88:25:2C:24:53:3C, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WPA WPA2
    ***:         Infra, 20:C9:D0:A4:8A:EC, Freq 2412 MHz, Rate 54 Mb/s, Strength 62 WPA2
    ***: Infra, C0:25:06:26:BE:E1, Freq 2412 MHz, Rate 54 Mb/s, Strength 42 WPA WPA2
    ***:            Infra, 00:1A:4F:DF:5A:CB, Freq 2462 MHz, Rate 54 Mb/s, Strength 42 WPA2
    ***:   Infra, 24:65:11:F3:CE:66, Freq 2447 MHz, Rate 54 Mb/s, Strength 26 WPA WPA2
    ***:    Infra, 00:1A:2A:EE:4D:E4, Freq 2412 MHz, Rate 54 Mb/s, Strength 95 WPA WPA2
    ***:      Infra, 7C:4F:B5:BE:52:5F, Freq 2412 MHz, Rate 54 Mb/s, Strength 42 WPA2
    ***:  Infra, 00:23:08:5A:3A:BB, Freq 2412 MHz, Rate 54 Mb/s, Strength 72 WPA WPA2

  IPv4 Settings:
    Address:         192.168.2.101
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.2.1

    DNS:             192.168.2.1


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            sky2
  State:             unavailable
  Default:           no
  HW Address:        ***

  Capabilities:
    Carrier Detect:  yes

  Wired Properties

```


Do you think its possible that the sky2 module is buggy?

Regards,
Philipp

---

### Post by praseodym on 2013-07-20
sky2 is you LAN driver. There are two WLAn drivers loaded, blacklist the wrong one:
```

echo "blacklist rtl8192cu" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
Reboot.

---

