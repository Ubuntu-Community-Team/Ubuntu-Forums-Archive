---
title: "Slow wifi in Thinkpad e430"
date: 2012-11-24
forum: Networking &amp; Wireless
---

### Post by Chet Hardin on 2012-11-24
Hey. 

I installed 12.10 on a Thinkpad e430.

The wifi speeds go intermittently from slow to crawl.  

I have tried this: [http://ubuntuforums.org/showpost.php?p=11348075&postcount=23](http://ubuntuforums.org/showpost.php?p=11348075&postcount=23)

Didn't work. 

Thanks in advance.

lspci:
```
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:14.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller (rev 04)
00:16.0 Communication controller: Intel Corporation 7 Series/C210 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 1 (rev c4)
00:1c.1 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 2 (rev c4)
00:1c.2 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 3 (rev c4)
00:1c.3 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 4 (rev c4)
00:1d.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation HM77 Express Chipset LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 7 Series Chipset Family 6-port SATA Controller [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation 7 Series/C210 Series Chipset Family SMBus Controller (rev 04)
02:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5229 PCI Express Card Reader (rev 01)
03:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller (rev 01)
0c:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 07)

```

ifconfig:
```
eth0      Link encap:Ethernet  HWaddr b8:88:e3:30:25:2c  
          inet addr:192.168.1.123  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: 2601:1:9340:25:1d0f:fec6:4a82:91bf/64 Scope:Global
          inet6 addr: fd3b:b01a:b4df:0:1d0f:fec6:4a82:91bf/64 Scope:Global
          inet6 addr: 2601:1:9340:25:ba88:e3ff:fe30:252c/64 Scope:Global
          inet6 addr: fd3b:b01a:b4df:0:ba88:e3ff:fe30:252c/64 Scope:Global
          inet6 addr: fe80::ba88:e3ff:fe30:252c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1659 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1303 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1680319 (1.6 MB)  TX bytes:199312 (199.3 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:9542 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9542 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:965101 (965.1 KB)  TX bytes:965101 (965.1 KB)

wlan0     Link encap:Ethernet  HWaddr 08:ed:b9:e2:12:95  
          inet addr:192.168.1.140  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: 2601:1:9340:25:3946:357:619f:25dd/64 Scope:Global
          inet6 addr: fd3b:b01a:b4df:0:3946:357:619f:25dd/64 Scope:Global
          inet6 addr: 2601:1:9340:25:aed:b9ff:fee2:1295/64 Scope:Global
          inet6 addr: fd3b:b01a:b4df:0:aed:b9ff:fee2:1295/64 Scope:Global
          inet6 addr: fe80::aed:b9ff:fee2:1295/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3240 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10337 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:963032 (963.0 KB)  TX bytes:1246277 (1.2 MB)
```

sudo lshw -C network:
```
*-network               
       description: Network controller
       product: BCM4313 802.11b/g/n Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=bcma-pci-bridge latency=0
       resources: irq:17 memory:f2d00000-f2d03fff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: eth0
       version: 07
       serial: b8:88:e3:30:25:2c
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8168e-3_0.0.4 03/27/12 ip=192.168.1.123 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:42 ioport:2000(size=256) memory:f1404000-f1404fff memory:f1400000-f1403fff
  *-network
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 08:ed:b9:e2:12:95
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=brcmsmac driverversion=3.5.0-18-generic firmware=N/A ip=192.168.1.140 link=yes multicast=yes wireless=IEEE 802.11bgn
```

lsmod:

```
Module                  Size  Used by
snd_hda_codec_hdmi     32007  1 
snd_hda_codec_conexant    57842  1 
joydev                 17457  0 
rfcomm                 46619  12 
bnep                   18140  2 
parport_pc             32688  0 
ppdev                  17073  0 
coretemp               13400  0 
kvm                   414070  0 
ghash_clmulni_intel    13180  0 
aesni_intel            51037  1 
cryptd                 20403  2 ghash_clmulni_intel,aesni_intel
aes_x86_64             17208  1 aesni_intel
arc4                   12529  2 
brcmsmac              531848  0 
mac80211              539908  1 brcmsmac
snd_hda_intel          33491  3 
brcmutil               14755  1 brcmsmac
cfg80211              206566  2 brcmsmac,mac80211
snd_hda_codec         134212  3 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel
cordic                 12535  1 brcmsmac
snd_hwdep              13602  1 snd_hda_codec
snd_pcm                96580  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
thinkpad_acpi          81198  0 
btusb                  18334  0 
bluetooth             209199  22 rfcomm,bnep,btusb
snd_seq_midi           13324  0 
snd_rawmidi            30512  1 snd_seq_midi
microcode              22803  0 
snd_seq_midi_event     14899  1 snd_seq_midi
uvcvideo               76749  0 
videobuf2_core         32851  1 uvcvideo
videodev              120309  2 uvcvideo,videobuf2_core
videobuf2_vmalloc      12860  1 uvcvideo
videobuf2_memops       13368  1 videobuf2_vmalloc
snd_seq                61521  2 snd_seq_midi,snd_seq_midi_event
psmouse                95552  0 
snd_timer              29425  2 snd_pcm,snd_seq
snd_seq_device         14497  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    78734  17 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,thinkpad_acpi,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15047  1 snd
nvram                  14362  1 thinkpad_acpi
i915                  520629  3 
bcma                   35656  1 brcmsmac
drm_kms_helper         46784  1 i915
drm                   275528  4 i915,drm_kms_helper
snd_page_alloc         18484  2 snd_hda_intel,snd_pcm
i2c_algo_bit           13413  1 i915
serio_raw              13215  0 
mei                    40690  0 
lpc_ich                17061  0 
wmi                    19070  0 
video                  19335  1 i915
mac_hid                13205  0 
lp                     17759  0 
parport                46345  3 parport_pc,ppdev,lp
r8169                  61650  0
```

---

### Post by chili555 on 2012-11-24
We wish we were seeing the complete details about your wireless devicce:```
lspci -nn | grep 0280
```Is your pci.id 14e4:4727? If so, please do:```
sudo apt-get install linux-headers-generic bcmwl-kernel-source
```Reboot and give us your report.> I have tried this: [http://ubuntuforums.org/showpost.php...5&postcount=23](http://ubuntuforums.org/showpost.php...5&postcount=23)

Didn't work. Fixes for Intel cards almost never help a Broadcom.

---

### Post by Chet Hardin on 2012-11-24
Hey Chili. 

Yes, my pci.id is 14e4:4727. So I ran the command you recommended, and voila, my wifi speed is back to normal. 

If you don't mind, what did we just do to my computer to fix this? 

Thanks!

---

### Post by chili555 on 2012-11-24
Glad it's working! We blacklisted the poorly performing for your device  brcmsmac driver and installed the much more appropriate for 4727 Broadcom STA driver; aka bcmwl-kernel-source. If you run:```
lsmod
```...you will see these are now missing:> brcmsmac              531848  0 
mac80211              539908  1 brcmsmac
brcmutil               14755  1 brcmsmac
cfg80211              206566  2 brcmsmac,mac80211
cordic                 12535  1 brcmsmac...and has been replaced with wl.

brcmsmac, bcma, and it's posse work well enough in other devices, just not 4727.

---

### Post by Chet Hardin on 2012-11-24
Good to know. 

Thanks.

---

