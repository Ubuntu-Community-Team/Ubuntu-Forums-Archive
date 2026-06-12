---
title: "Help! Wireless not showing"
date: 2012-05-24
forum: Networking &amp; Wireless
---

### Post by gofastvolvo on 2012-05-24
I have Ubuntu 10.04 (CAElinux) installed.  The networking applet isn't showing in the notification area and the network connections isn't displaying any networks. When I try nm-tool it shows me plenty of available networks.

Please help out if you can, I have no wired conections available. I've tried many of the suggestions on the forum but none have worked for me.

```
~$ nm-tool

NetworkManager Tool

State: connected

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            e1000e
  State:             unmanaged
  Default:           no
  HW Address:        D8:D3:85:15:A3:57

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlagn
  State:             disconnected
  Default:           no
  HW Address:        00:21:6A:AB:E3:CC

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    Bingo:           Infra, 00:1C:F0:83:D5:D2, Freq 2437 MHz, Rate 54 Mb/s, Strength 34 WPA
    TN_private_EPJ9NE: Infra, C8:6C:87:88:79:14, Freq 2457 MHz, Rate 11 Mb/s, Strength 32 WEP
    LMH24:           Infra, 00:17:3F:5C:6C:FF, Freq 2427 MHz, Rate 54 Mb/s, Strength 37 WPA WPA2
    TN_private_EPJ9NE: Infra, C8:6C:87:88:79:14, Freq 2457 MHz, Rate 54 Mb/s, Strength 34 WPA
    HOTELL-3:        Infra, 34:21:09:02:F2:EC, Freq 2437 MHz, Rate 54 Mb/s, Strength 35 WEP
    624710:          Infra, 70:71:BC:2B:C2:B5, Freq 2437 MHz, Rate 54 Mb/s, Strength 34 WPA
    B2_private_0D:   Infra, 00:01:38:8E:75:D3, Freq 2462 MHz, Rate 54 Mb/s, Strength 38 WEP
    HOTELL-1-G:      Infra, 00:1F:33:36:D6:FB, Freq 2412 MHz, Rate 54 Mb/s, Strength 41 WEP


```

---

### Post by praseodym on 2012-05-24
Hi,

please show

```
uname -a
dmesg | grep iwl
lsmod
iwconfig
rfkill list
```

---

### Post by gofastvolvo on 2012-05-27
> **praseodym said:**
> Hi,

please show

```
uname -a
dmesg | grep iwl
lsmod
iwconfig
rfkill list
```

As requested, thanks for your help.

```
~$ uname -a
Linux matthew 2.6.32-41-generic #88-Ubuntu SMP Thu Mar 29 13:10:32 UTC 2012 x86_64 GNU/Linux
matthew@matthew:~$ dmesg |grep iwl
[   15.871644] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27k
[   15.871646] iwlagn: Copyright(c) 2003-2009 Intel Corporation
[   15.871735] iwlagn 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   15.871764] iwlagn 0000:03:00.0: setting latency timer to 64
[   15.871835] iwlagn 0000:03:00.0: Detected Intel Wireless WiFi Link 5300AGN REV=0x24
[   15.926884] iwlagn 0000:03:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[   15.926968] iwlagn 0000:03:00.0: irq 31 for MSI/MSI-X
[   15.933701] phy0: Selected rate control algorithm 'iwl-agn-rs'
[   16.418138] iwlagn 0000:03:00.0: firmware: requesting iwlwifi-5000-2.ucode
[   16.444173] iwlagn 0000:03:00.0: loaded firmware version 8.24.2.12
[   16.626274] Registered led device: iwl-phy0::radio
[   16.626288] Registered led device: iwl-phy0::assoc
[   16.626300] Registered led device: iwl-phy0::RX
[   16.626311] Registered led device: iwl-phy0::TX
matthew@matthew:~$ lsmod
Module                  Size  Used by
binfmt_misc             7960  1 
rfcomm                 40425  4 
sco                     9649  2 
bridge                 53280  0 
stp                     2171  1 bridge
bnep                   11916  2 
l2cap                  34839  16 rfcomm,bnep
dm_crypt               13043  0 
nfsd                  304310  11 
lockd                  75079  1 nfsd
nfs_acl                 2709  1 nfsd
auth_rpcgss            44516  1 nfsd
sunrpc                228463  10 nfsd,lockd,nfs_acl,auth_rpcgss
exportfs                4202  1 nfsd
pata_pcmcia            10856  1 
snd_hda_codec_analog    78702  1 
tpm_infineon            9217  0 
pcmcia                 35580  1 pata_pcmcia
snd_hda_intel          25805  2 
snd_hda_codec          85791  2 snd_hda_codec_analog,snd_hda_intel
snd_hwdep               6924  1 snd_hda_codec
snd_pcm_oss            41394  0 
snd_mixer_oss          16299  1 snd_pcm_oss
snd_pcm                87946  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1782  0 
snd_seq_oss            31191  0 
snd_seq_midi            5829  0 
arc4                    1473  2 
snd_rawmidi            23420  1 snd_seq_midi
snd_seq_midi_event      7267  2 snd_seq_oss,snd_seq_midi
snd_seq                57481  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23681  2 snd_pcm,snd_seq
snd_seq_device          6888  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ppdev                   6375  0 
joydev                 11104  0 
iwlagn                123060  0 
hp_accel               12168  0 
yenta_socket           22901  3 
rsrc_nonstatic          9830  1 yenta_socket
snd                    71283  16 snd_hda_codec_analog,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
uvcvideo               62915  0 
videodev               40614  1 uvcvideo
v4l1_compat            15495  2 uvcvideo,videodev
v4l2_compat_ioctl32    11892  1 videodev
parport_pc             29958  1 
iwlcore               125250  1 iwlagn
mac80211              238928  2 iwlagn,iwlcore
tpm_tis                 9912  0 
lis3lv02d               7648  1 hp_accel
tpm                    16368  2 tpm_infineon,tpm_tis
tpm_bios                6402  1 tpm
ricoh_mmc               3416  0 
sdhci_pci               6700  0 
sdhci                  17960  1 sdhci_pci
btusb                  13097  2 
bluetooth              58717  9 rfcomm,sco,bnep,l2cap,btusb
pcmcia_core            38176  3 pcmcia,yenta_socket,rsrc_nonstatic
input_polldev           3106  1 lis3lv02d
led_class               3764  3 hp_accel,iwlcore,sdhci
psmouse                65040  0 
serio_raw               4918  0 
soundcore               8052  1 snd
snd_page_alloc          8500  2 snd_hda_intel,snd_pcm
cfg80211              148725  3 iwlagn,iwlcore,mac80211
lp                      9336  0 
parport                37160  3 ppdev,parport_pc,lp
raid10                 21450  0 
raid456                54720  0 
async_pq                3891  1 raid456
async_xor               3111  2 raid456,async_pq
async_memcpy            1537  1 raid456
async_raid6_recov       1816  1 raid456
raid6_pq               80147  2 async_pq,async_raid6_recov
async_tx                2545  5 raid456,async_pq,async_xor,async_memcpy,async_raid6_recov
raid1                  22610  0 
raid0                   6778  0 
multipath               7181  0 
linear                  4126  0 
dm_raid45              75532  0 
xor                     4685  2 async_xor,dm_raid45
fbcon                  39270  71 
tileblit                2487  1 fbcon
font                    8053  1 fbcon
bitblit                 5811  1 fbcon
softcursor              1565  1 bitblit
vga16fb                12757  0 
vgastate                9857  1 vga16fb
nouveau               515227  2 
ttm                    61039  1 nouveau
drm_kms_helper         30742  1 nouveau
ohci1394               30260  0 
video                  20623  0 
output                  2503  1 video
ieee1394               94771  1 ohci1394
ahci                   38350  2 
drm                   200448  4 nouveau,ttm,drm_kms_helper
i2c_algo_bit            6024  1 nouveau
intel_agp              29319  0 
e1000e                136301  0 
ramzswap                7857  1 
xvmalloc                5054  1 ramzswap
lzo_decompress          2533  1 ramzswap
lzo_compress            2325  1 ramzswap
matthew@matthew:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=14 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
pan0      no wireless extensions.

matthew@matthew:~$ rfkill list
0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

```

---

### Post by praseodym on 2012-05-27
Reboot, hold the SHIFT-Button pressed, and try an earlier kernel version. Obviously, it worked before (Kernel -41 is shown). Install there

> sudo apt-get install linux-backports-modules-wireless-lucid-generic
and reboot into the latest kernel.

---

