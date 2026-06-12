---
title: "Toshiba NB505 realtek chipset wifi problem"
date: 2011-09-01
forum: Networking &amp; Wireless
---

### Post by yungballla6 on 2011-09-01
Hi i have a toshiba netbook which i recently dual booted ubuntu 11.04 with windows 7. on win 7 the wireless is speedy but with ubuntu i sometimes cant connect and if i am able to connect it craps out after a few minutes. i really like ubuntu but i need internet for school. If anyone can help i would really appreciate it, thank you.

---

### Post by wildmanne39 on 2011-09-01
Hi, run these commands and post the results here please:
```
sudo lshw -C network
```
```
nm-tool
```
```
lspci -nn | grep 0280
```
```
lsusb
```
```
iwconfig
```
```
rfkill list all
```
```
lsmod
```
and post the outcome here by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by yungballla6 on 2011-09-01
```
sarah@sarah-TOSHIBA-NB505:~$ sudo lshw -C network
[sudo] password for sarah: 
  *-network               
       description: Wireless interface
       product: RTL8188CE 802.11b/g/n WiFi Adapter
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: wlan0
       version: 01
       serial: 7c:4f:b5:5d:cf:18
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8192ce driverversion=2.6.38-11-generic firmware=N/A ip=192.168.0.130 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 ioport:2000(size=256) memory:f0100000-f0103fff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 05
       serial: b8:70:f4:58:ca:4b
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:43 ioport:3000(size=256) memory:f050c000-f050cfff memory:f0508000-f050bfff
sarah@sarah-TOSHIBA-NB505:~$ nm-tool

NetworkManager Tool

State: connected

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        B8:70:F4:58:CA:4B

  Capabilities:
    Carrier Detect:  yes
    Speed:           10 Mb/s

  Wired Properties
    Carrier:         off


- Device: wlan0  [Auto default] ------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8192ce
  State:             connected
  Default:           yes
  HW Address:        7C:4F:B5:5D:CF:18

  Capabilities:
    Speed:           11 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    *default:        Infra, 00:0D:88:43:07:B5, Freq 2437 MHz, Rate 11 Mb/s, Strength 85

  IPv4 Settings:
    Address:         192.168.0.130
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             192.168.0.1


sarah@sarah-TOSHIBA-NB505:~$ lspci -nn | grep 0280
07:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter [10ec:8176] (rev 01)
sarah@sarah-TOSHIBA-NB505:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 04f2:b1d6 Chicony Electronics Co., Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
sarah@sarah-TOSHIBA-NB505:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"default"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:0D:88:43:07:B5   
          Bit Rate=11 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=60/70  Signal level=-50 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:1219   Missed beacon:0

sarah@sarah-TOSHIBA-NB505:~$ rfkill list all
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
sarah@sarah-TOSHIBA-NB505:~$ lsmod
Module                  Size  Used by
parport_pc             32111  0 
ppdev                  12849  0 
snd_hda_codec_realtek   255882  1 
snd_hda_intel          24113  2 
snd_hda_codec          90901  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
arc4                   12473  2 
snd_pcm                80042  2 snd_hda_intel,snd_hda_codec
rtl8192ce             131689  0 
i915                  451033  3 
snd_seq_midi           13132  0 
rtlwifi               106737  1 rtl8192ce
snd_rawmidi            25269  1 snd_seq_midi
mac80211              257001  2 rtl8192ce,rtlwifi
snd_seq_midi_event     14475  1 snd_seq_midi
joydev                 17322  0 
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
binfmt_misc            13213  1 
drm_kms_helper         40745  1 i915
drm                   184164  4 i915,drm_kms_helper
snd_timer              28659  2 snd_pcm,snd_seq
cfg80211              156212  2 rtlwifi,mac80211
uvcvideo               66851  0 
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
psmouse                73312  0 
videodev               75143  1 uvcvideo
snd                    55295  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i2c_algo_bit           13184  1 i915
serio_raw              12990  0 
soundcore              12600  1 snd
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
video                  18951  1 i915
sparse_keymap          13666  0 
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
ahci                   21591  2 
libahci                25548  1 ahci
r8169                  42534  0 
sarah@sarah-TOSHIBA-NB505:~
```

---

### Post by wildmanne39 on 2011-09-01
Hi, please post the results of these commands:
```
sudo iwlist scan
```
```
dmesg | grep wlan0
```
```
dmesg | grep rtl
```
```
lsmod | grep rtl
```
Thank you

---

