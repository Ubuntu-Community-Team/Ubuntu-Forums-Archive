---
title: "Broadcom on thinkpad e530c (Can't detect available WIFI networks)"
date: 2013-07-19
forum: Networking &amp; Wireless
---

### Post by Amr7 on 2013-07-19
I tried using the open source driver (brcmsmac), but it can't seem to detect any available networks.

(Please note that the Proprietary driver installed via bcmwl-kernel-source works fine, but it has a weird problem causing other machines on the same network to lose all internet access. so if anyone knows a solution to this problem, that'd be cool)

Also, I'm using Ubuntu 13.04 and somehow a noob :D
```

lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation 2nd Generation Core Processor Family DRAM Controller [8086:0104] (rev 09)
00:01.0 PCI bridge [0604]: Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port [8086:0101] (rev 09)
00:02.0 VGA compatible controller [0300]: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller [8086:0126] (rev 09)
00:14.0 USB controller [0c03]: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller [8086:1e31] (rev 04)
00:16.0 Communication controller [0780]: Intel Corporation 7 Series/C210 Series Chipset Family MEI Controller #1 [8086:1e3a] (rev 04)
00:1a.0 USB controller [0c03]: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2 [8086:1e2d] (rev 04)
00:1b.0 Audio device [0403]: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller [8086:1e20] (rev 04)
00:1c.0 PCI bridge [0604]: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 1 [8086:1e10] (rev c4)
00:1c.1 PCI bridge [0604]: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 2 [8086:1e12] (rev c4)
00:1c.2 PCI bridge [0604]: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 3 [8086:1e14] (rev c4)
00:1c.3 PCI bridge [0604]: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 4 [8086:1e16] (rev c4)
00:1d.0 USB controller [0c03]: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1 [8086:1e26] (rev 04)
00:1f.0 ISA bridge [0601]: Intel Corporation HM77 Express Chipset LPC Controller [8086:1e57] (rev 04)
00:1f.2 SATA controller [0106]: Intel Corporation 7 Series Chipset Family 6-port SATA Controller [AHCI mode] [8086:1e03] (rev 04)
00:1f.3 SMBus [0c05]: Intel Corporation 7 Series/C210 Series Chipset Family SMBus Controller [8086:1e22] (rev 04)
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GF119M [GeForce 610M] [10de:1058] (rev ff)
02:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5229 PCI Express Card Reader [10ec:5229] (rev 01)
03:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)
0c:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168 PCI Express Gigabit Ethernet controller [10ec:8168] (rev 07)

```

```
rfkill list all
0: tpacpi_bluetooth_sw: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

```


```
iwconfig
eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=19 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

```

```

lsmod
Module                  Size  Used by
nls_utf8               12557  1 
udf                    89374  1 
crc_itu_t              12707  1 udf
bbswitch               13611  0 
parport_pc             28152  0 
ppdev                  17073  0 
rfcomm                 42641  12 
bnep                   18036  2 
nls_iso8859_1          12713  1 
snd_hda_codec_hdmi     36913  1 
snd_hda_codec_conexant    62000  1 
joydev                 17377  0 
arc4                   12615  2 
brcmsmac              550698  0 
uvcvideo               80847  0 
videobuf2_vmalloc      13056  1 uvcvideo
videobuf2_memops       13202  1 videobuf2_vmalloc
btusb                  22474  0 
videobuf2_core         40513  1 uvcvideo
bluetooth             228619  22 bnep,btusb,rfcomm
videodev              129260  2 uvcvideo,videobuf2_core
cordic                 12574  1 brcmsmac
brcmutil               14755  1 brcmsmac
mac80211              606457  1 brcmsmac
cfg80211              510937  2 brcmsmac,mac80211
coretemp               13355  0 
kvm                   443165  0 
ghash_clmulni_intel    13259  0 
cryptd                 20373  1 ghash_clmulni_intel
microcode              22881  0 
snd_hda_intel          39619  6 
thinkpad_acpi          81222  0 
snd_hda_codec         136453  3 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
wmi                    19070  0 
snd_pcm                97451  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
nvram                  14362  1 thinkpad_acpi
bcma                   41051  1 brcmsmac
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30180  1 snd_seq_midi
rtsx_pci_ms            13011  0 
memstick               16554  1 rtsx_pci_ms
psmouse                95870  0 
snd_seq                61554  2 snd_seq_midi_event,snd_seq_midi
mac_hid                13205  0 
serio_raw              13215  0 
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29425  2 snd_pcm,snd_seq
snd                    68876  23 snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,thinkpad_acpi,snd_seq_device
soundcore              12680  1 snd
i915                  600396  3 
lpc_ich                17061  0 
mei                    41158  0 
video                  19390  1 i915
drm_kms_helper         49394  1 i915
lp                     17759  0 
drm                   286028  4 i915,drm_kms_helper
parport                46345  3 lp,ppdev,parport_pc
i2c_algo_bit           13413  1 i915
hid_generic            12540  0 
usbhid                 47074  0 
hid                   101002  2 hid_generic,usbhid
rtsx_pci_sdmmc         17475  0 
r8169                  67446  0 
ahci                   25731  6 
libahci                31364  1 ahci
rtsx_pci               33355  2 rtsx_pci_ms,rtsx_pci_sdmmc

```


Any help is appreciated, thanks.

---

### Post by Amr7 on 2013-07-19
Looks like the problem with the proprietary driver (other machines not being able to connect) is a known bug, and it's fixed in 13.10

Solved by following the solution here [https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/1174145](https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/1174145):

- Go to [https://launchpad.net/ubuntu/saucy/+package/bcmwl-kernel-source](https://launchpad.net/ubuntu/saucy/+package/bcmwl-kernel-source)
- Click the link under Source package
- Under "Builds" click either saucy i386 (for 32-bit) or saucy AMD64 (for 64-bit)
- On the next page, under "Built files", click the link to download the .deb file
- Open the .deb and it should open in Ubuntu Software Center
- Click the Upgrade button

---

