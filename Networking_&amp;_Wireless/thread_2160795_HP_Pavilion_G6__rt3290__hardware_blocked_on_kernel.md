---
title: "HP Pavilion G6 | rt3290 | hardware blocked on kernel 3.10.0"
date: 2013-07-08
forum: Networking &amp; Wireless
---

### Post by daaatz on 2013-07-08
Hi,

I've updated kernel to 3.10 now it seems that my wifi card rt3290 is working but I can't run it using button "F12" on laptop.
Even "Fn" + "F12" doesn't work.

Here are some details:

```


*************** info trace ***************

***** uname -a *****

Linux maciej-HP-Pavilion-g6-Notebook-PC 3.10.0-031000-generic #201306301935 SMP Sun Jun 30 23:36:16 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

***** lsb_release *****

Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.2 LTS
Release:    12.04
Codename:    precise

***** lspci *****

07:00.0 Network controller [0280]: Ralink corp. Device [1814:3290]
    Subsystem: Hewlett-Packard Company Device [103c:18ec]
    Kernel driver in use: rt2800pci
--
08:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
    Subsystem: Hewlett-Packard Company Device [103c:183e]
    Kernel driver in use: r8169

***** lsusb *****

Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 002 Device 003: ID 064e:e263 Suyin Corp. 
Bus 001 Device 004: ID 1bcf:0007 Sunplus Innovation Technology Inc. Optical Mouse

***** iwconfig *****

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

***** rfkill *****

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

***** lsmod *****

rt2800pci              19051  0 
rt2x00mmio             13661  1 rt2800pci
rt2800lib              81280  1 rt2800pci
crc_ccitt              12707  1 rt2800lib
rt2x00pci              13287  1 rt2800pci
rt2x00lib              55811  4 rt2800pci,rt2x00mmio,rt2800lib,rt2x00pci
mac80211              624025  3 rt2800lib,rt2x00pci,rt2x00lib
cfg80211              499487  2 rt2x00lib,mac80211
eeprom_93cx6           13344  1 rt2800pci

***** nm-tool *****

NetworkManager Tool

State: connected (global)

- Device: eth0  [Po&#322;&#261;czenie przewodowe 1] ------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.12
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             62.179.1.62
    DNS:             62.179.1.63


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rt2800pci
  State:             unavailable
  Default:           no
  HW Address:        <MAC address removed>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 



***** NetworkManager.state *****
[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

***** NetworkManager.conf *****

[main]
plugins=ifupdown,keyfile
dns=dnsmasq

[ifupdown]
managed=false

***** interfaces *****

auto lo
iface lo inet loopback


***** iwlist *****


***** resolv.conf *****

nameserver 127.0.0.1

***** blacklist *****

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist.conf]
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac
blacklist hp-wmi

***** dmesg *****

[   13.507333] ieee80211 phy0: rt2x00_set_rt: Info - RT chipset 3290, rev 0015 detected
[   13.511749] ieee80211 phy0: rt2x00_set_rf: Info - RF chipset 3290 detected

****************** done ******************



```

Any one knows how to unblock it ? Thanks

---

### Post by praseodym on 2013-07-08
Check the following:
```

sudo rfkill unblock all
```
and/or resetting the BIOS to default (BIOS or UEFI?). Please also show
```

lsmod
```
completely.

---

### Post by daaatz on 2013-07-08
```

maciej@maciej-HP-Pavilion-g6-Notebook-PC:~$ lsmod
Module                  Size  Used by
pci_stub               12622  1 
vboxpci                23236  0 
vboxnetadp             25670  0 
vboxnetflt             23478  0 
vboxdrv               320274  3 vboxpci,vboxnetadp,vboxnetflt
bnep                   18258  2 
rfcomm                 47852  0 
bluetooth             253156  10 bnep,rfcomm
parport_pc             32866  0 
ppdev                  17106  0 
binfmt_misc            17508  1 
uvcvideo               82296  0 
videobuf2_core         40785  1 uvcvideo
videodev              131388  2 uvcvideo,videobuf2_core
videobuf2_vmalloc      13056  1 uvcvideo
videobuf2_memops       13202  1 videobuf2_vmalloc
intel_powerclamp       18951  0 
arc4                   12573  2 
snd_hda_codec_hdmi     41552  1 
coretemp               13596  0 
snd_hda_codec_idt      55089  1 
snd_hda_intel          48664  5 
snd_hda_codec         194680  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
kvm                   436454  0 
rt2800pci              19051  0 
rt2x00mmio             13661  1 rt2800pci
rt2800lib              81280  1 rt2800pci
snd_hwdep              13613  1 snd_hda_codec
crc32_pclmul           13160  0 
ghash_clmulni_intel    13259  0 
crc_ccitt              12707  1 rt2800lib
snd_pcm               107180  4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
aesni_intel            55720  0 
ablk_helper            13597  1 aesni_intel
snd_rawmidi            30416  1 snd_seq_midi
joydev                 17613  0 
rt2x00pci              13287  1 rt2800pci
snd_seq_midi_event     14899  1 snd_seq_midi
rt2x00lib              55811  4 rt2800pci,rt2x00mmio,rt2800lib,rt2x00pci
snd_seq                66061  2 snd_seq_midi,snd_seq_midi_event
cryptd                 20501  3 ghash_clmulni_intel,aesni_intel,ablk_helper
lrw                    13294  1 aesni_intel
gf128mul               14951  1 lrw
snd_timer              29989  2 snd_pcm,snd_seq
mac80211              624025  3 rt2800lib,rt2x00pci,rt2x00lib
glue_helper            14095  1 aesni_intel
snd_seq_device         14497  3 snd_seq_midi,snd_rawmidi,snd_seq
cfg80211              499487  2 rt2x00lib,mac80211
aes_x86_64             17131  1 aesni_intel
snd                    73821  20 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_seq_midi,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i915                  640374  2 
soundcore              12680  1 snd
rtsx_pci_ms            13180  0 
psmouse               102030  0 
snd_page_alloc         18798  2 snd_hda_intel,snd_pcm
drm_kms_helper         53178  1 i915
microcode              22923  0 
drm                   295647  3 i915,drm_kms_helper
memstick               16569  1 rtsx_pci_ms
wmi                    19256  0 
serio_raw              13253  0 
i2c_algo_bit           13564  1 i915
lpc_ich                17060  0 
mac_hid                13253  0 
eeprom_93cx6           13344  1 rt2800pci
video                  19624  1 i915
lp                     17799  0 
parport                42466  3 parport_pc,ppdev,lp
hid_generic            12548  0 
usbhid                 47196  0 
hid                   105557  2 hid_generic,usbhid
rtsx_pci_sdmmc         17842  0 
ahci                   30063  3 
libahci                32088  1 ahci
rtsx_pci               34273  2 rtsx_pci_ms,rtsx_pci_sdmmc
r8169                  68812  0 
maciej@maciej-HP-Pavilion-g6-Notebook-PC:~$ 



```

I tried unblock and it doesnt work..

---

### Post by praseodym on 2013-07-08
Why is the module hp-wmi blacklisted? Try it on the fly
```

sudo modprobe -v hp-wmi
```
Try Fn+F12 now. If its freezing: hard reset

---

### Post by daaatz on 2013-07-08
```

maciej@maciej-HP-Pavilion-g6-Notebook-PC:~$ sudo modprobe -v hp-wmi
maciej@maciej-HP-Pavilion-g6-Notebook-PC:~$ modprobe hp-wmi
maciej@maciej-HP-Pavilion-g6-Notebook-PC:~$ rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
maciej@maciej-HP-Pavilion-g6-Notebook-PC:~$ 



```

hmmm.

---

### Post by praseodym on 2013-07-08
Any additional button/switch? Try to press Fn+F12 permanently or repeatedly during boot-up

---

### Post by daaatz on 2013-07-09
Is it possible maybe that smth is wrong with drivers for rt3290 ? Maybe it just look like problem with button ( for example buttons for sound works fine ) but its problem with drivers..

---

### Post by daaatz on 2013-07-18
To other ppl with rt3290 and ubuntu problem.
After fighitng with it I found solution good.
Install ubuntu again ,
dont install any drivers !!
update kernel to 3.6.6
and copy firmware to lib/firmware and its working great !

If I tried for example on fresh ubuntu install using kernel 3.2.0-31 installing drivers from ralink next moving to new kernel ( some other day ) and coping firmware didnt help.

Thank for help anyway :)

---

