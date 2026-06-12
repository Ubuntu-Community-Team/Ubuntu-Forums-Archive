---
title: "Lenovo e530: 2.4Ghz not found on 13.04"
date: 2013-06-25
forum: Networking &amp; Wireless
---

### Post by bituser on 2013-06-25
First of all, I'm a linux newb and I've installed ubuntu 13.04 in a dual boot with Windows 8 so I can learn more about linux.

I'm using a Lenovo e530 to do the dual booting, but it's wireless didn't work initially. Today I learned about proprietary drivers and managed to get the broadcom drivers installed from the software update settings.

My issue now is that I can only see 5GHz networks and not my 2.4GHz one. I want it to connect to 2.4GHz as that is the frequency used at my university. I've searched online to no avail. Any ideas?

thanks,
Sam

---

### Post by praseodym on 2013-06-25
Hi,

please show the outputs of these terminal (CTRL+ALT+T) commands:
```

lspci -nnk | grep -iA2 net
lsmod
iwconfig
iwlist chan
sudo iwlist scan
dmesg | egrep 'bcma|brcm|wl|country'
```
Which country do you live? Does LAN work?

---

### Post by bituser on 2013-06-25
I have work today so I will update this post later with those outputs. Thanks for replying. I am in NZ and LAN does work, it is how I got the proprietary drivers.

---

### Post by bituser on 2013-06-26
lspci -nnk | grep -iA2 net
> 03:00.0 Network controller [0280]: Broadcom Corporation BCM43228 802.11a/b/g/n [14e4:4359]
    Subsystem: Broadcom Corporation Device [14e4:0607]
    Kernel driver in use: wl
0c:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168 PCI Express Gigabit Ethernet controller [10ec:8168] (rev 07)
    Subsystem: Lenovo Device [17aa:5000]
    Kernel driver in use: r8169



lsmod
> Module                  Size  Used by
parport_pc             28152  0 
ppdev                  17073  0 
snd_hda_codec_hdmi     36913  1 
snd_hda_codec_conexant    62000  1 
rfcomm                 42641  12 
bnep                   18036  2 
lib80211_crypt_tkip    17379  0 
wl                   3074449  0 
usb_storage            57204  0 
joydev                 17377  0 
uvcvideo               80847  0 
videobuf2_vmalloc      13056  1 uvcvideo
videobuf2_memops       13202  1 videobuf2_vmalloc
btusb                  22474  0 
videobuf2_core         40513  1 uvcvideo
bluetooth             228619  22 bnep,btusb,rfcomm
videodev              129260  2 uvcvideo,videobuf2_core
lib80211               14352  2 wl,lib80211_crypt_tkip
cfg80211              510937  1 wl
coretemp               13355  0 
kvm_intel             132891  0 
kvm                   443165  1 kvm_intel
ghash_clmulni_intel    13259  0 
cryptd                 20373  1 ghash_clmulni_intel
microcode              22881  0 
nouveau               939088  1 
snd_hda_intel          39619  3 
i915                  600351  3 
snd_hda_codec         136453  3 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
mxm_wmi                13021  1 nouveau
ttm                    83187  1 nouveau
snd_pcm                97451  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
psmouse                95870  0 
drm_kms_helper         49394  2 i915,nouveau
lpc_ich                17061  0 
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
serio_raw              13215  0 
drm                   286313  7 ttm,i915,drm_kms_helper,nouveau
rtsx_pci_ms            13011  0 
memstick               16554  1 rtsx_pci_ms
i2c_algo_bit           13413  2 i915,nouveau
mei                    41158  0 
wmi                    19070  2 mxm_wmi,nouveau
thinkpad_acpi          81222  0 
nvram                  14362  1 thinkpad_acpi
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30180  1 snd_seq_midi
snd_seq                61554  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29425  2 snd_pcm,snd_seq
snd                    68876  17 snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,thinkpad_acpi,snd_seq_device
soundcore              12680  1 snd
video                  19390  2 i915,nouveau
mac_hid                13205  0 
lp                     17759  0 
parport                46345  3 lp,ppdev,parport_pc
rtsx_pci_sdmmc         17475  0 
ahci                   25731  2 
libahci                31364  1 ahci
r8169                  67446  0 
rtsx_pci               33355  2 rtsx_pci_ms,rtsx_pci_sdmmc



iwconfig
> eth0      no wireless extensions.

eth1      IEEE 802.11abg  ESSID:"Router1_5GHZ"  
          Mode:Managed  Frequency:5.22 GHz  Access Point: 20:E5:2A:4A:F7:DF   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
lo        no wireless extensions.



iwlist chan
> eth0      no frequency information.

eth1      32 channels in total; available frequencies :
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
          Channel 14 : 2.484 GHz
          Channel 36 : 5.18 GHz
          Channel 38 : 5.19 GHz
          Channel 40 : 5.2 GHz
          Channel 42 : 5.21 GHz
          Channel 44 : 5.22 GHz
          Channel 46 : 5.23 GHz
          Channel 48 : 5.24 GHz
          Channel 149 : 5.745 GHz
          Channel 150 : 5.75 GHz
          Channel 151 : 5.755 GHz
          Channel 152 : 5.76 GHz
          Channel 153 : 5.765 GHz
          Channel 154 : 5.77 GHz
          Channel 155 : 5.775 GHz
          Channel 156 : 5.78 GHz
          Channel 157 : 5.785 GHz
          Channel 158 : 5.79 GHz
          Channel 159 : 5.795 GHz
          Current Frequency:5.22 GHz (Channel 44)

lo        no frequency information.




sudo iwlist scan

> eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 20:E5:2A:4A:F7:DF
                    Channel:44
                    Frequency:5.22 GHz (Channel 44)
                    Quality=53/70  Signal level=-57 dBm  
                    Encryption key:on
                    ESSID:"Router1_5GHZ"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 32ms ago
                    IE: Unknown: 000C526F75746572315F3547485A
                    IE: Unknown: 01088C129824B048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2D1AFF081BFFFFFF0001000000000000000000000000000000000000
                    IE: Unknown: 3D162C0D0000000000000000000000000000000000000000
                    IE: Unknown: DD7F0050F204104A0001101044000102103B00010310470010C15A31CEA8E7AD295E407243CB06BF3A102100074E6574676561721023000844474E44343030301024000844474E443430303010420004313233341054000800060050F20400011011000844474E443430303010080002200C103C0001031049000600372A000120
                    IE: Unknown: DD090010180200F03C0000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 02 - Address: 00:15:6D:70:1A:4D
                    Channel:36
                    Frequency:5.18 GHz (Channel 36)
                    Quality=47/70  Signal level=-63 dBm  
                    Encryption key:on
                    ESSID:"Chooks"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 32ms ago
                    IE: Unknown: 000643686F6F6B73
                    IE: Unknown: 01088C129824B048606C
                    IE: Unknown: 030124
                    IE: Unknown: 050400010000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD26000C42000000011E000000001F660902FF0F484F5553455F4150000000000000000000000000
                    IE: Unknown: DD180050F202010185000364000027A4000041435E0061322F00
                    IE: Unknown: DD1E00904C334C001BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 2D1A4C001BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3424080800000000000000000000000000000000000000
                    IE: Unknown: 3D1624080800000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010002004000
                    IE: Unknown: DD0E00156D0000000102A5E002021200

lo        Interface doesn't support scanning.



dmesg | egrep 'bcma|brcm|wl|country'
> [   16.579602] wl: module license 'MIXED/Proprietary' taints kernel.
[   16.610181] INFO @wl_cfg80211_attach : Registered CFG80211 phy
[  611.901262] ERROR @wl_cfg80211_get_station : Could not get rate (-1)
[  611.901269] ERROR @wl_cfg80211_get_station : Could not get rssi (-1)
[  611.901279] ERROR @wl_cfg80211_get_station : Could not get rate (-1)
[  611.901282] ERROR @wl_cfg80211_get_station : Could not get rssi (-1)
[  611.901290] ERROR @wl_dev_intvar_get : error (-1)
[  611.901293] ERROR @wl_cfg80211_get_tx_power : error (-1)
[ 2624.066752] ERROR @wl_cfg80211_get_station : Could not get rate (-1)
[ 2624.066759] ERROR @wl_cfg80211_get_station : Could not get rssi (-1)
[ 2624.066768] ERROR @wl_cfg80211_get_station : Could not get rate (-1)
[ 2624.066771] ERROR @wl_cfg80211_get_station : Could not get rssi (-1)
[ 2624.066779] ERROR @wl_dev_intvar_get : error (-1)
[ 2624.066781] ERROR @wl_cfg80211_get_tx_power : error (-1)



---

### Post by praseodym on 2013-06-26
Try
```

sudo apt-get install iw
iw reg get
sudo iw reg set NZ
iw reg get
sudo rmmod lib80211_crypt_tkip
```

---

### Post by bituser on 2013-06-27
```
sam@sam-ubuntu:~$ iw reg get
country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 20), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBsam@sam-ubuntu:~$ iw reg get
country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 20), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
sam@sam-ubuntu:~$ sudo iw reg set NZ
sam@sam-ubuntu:~$ iw reg get
country NZ:
    (2402 - 2482 @ 40), (N/A, 30)
    (5170 - 5250 @ 20), (3, 23)
    (5250 - 5330 @ 20), (3, 23), DFS
    (5735 - 5835 @ 20), (3, 30)
sam@sam-ubuntu:~$ sudo rmmod lib80211_crypt_tkip


```

I'm just going to restart to see if this solved it, but there is the output. Thanks.

EDIT: sadly it did not work

---

### Post by praseodym on 2013-06-28
Try the patched driver:
```

sudo apt-get install linux-headers-$(uname -r) linux-headers-generic dkms build-essential 
sudo apt-get remove --purge bcmwl-kernel-source 
```

Check for 32 or 64bit from here "with dkms" for kernel 3.2/3.5:
[http://forum.ubuntuusers.de/topic/w-lan-acer-4820tg-broadcom-installation-schlae/#Version-V5-100-82-112-DKMS](http://forum.ubuntuusers.de/topic/w-lan-acer-4820tg-broadcom-installation-schlae/#Version-V5-100-82-112-DKMS)

---

