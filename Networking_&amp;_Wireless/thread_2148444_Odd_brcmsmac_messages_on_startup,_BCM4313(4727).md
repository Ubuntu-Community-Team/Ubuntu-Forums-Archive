---
title: "Odd brcmsmac messages on startup, BCM4313(4727)"
date: 2013-05-25
forum: Networking &amp; Wireless
---

### Post by Rob Sayer on 2013-05-25
I'm finding that the connection on the wifi cafe I'm typing this at is iffy. It cuts in and out. Sometimes a restart helps. I think. Running kubuntu 13.04 on acer d270 netbook, atom 2600.

I've found some brcmsmac error messages on startup / shutdown I suspect may be related because accoring to:

lspci -nnk | grep -iA2 net
```
01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
        Subsystem: Acer Incorporated [ALI] Device [1025:061f]
        Kernel driver in use: r8169
02:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)
        Subsystem: Foxconn International, Inc. Device [105b:e042]
        Kernel driver in use: bcma-pci-bridge
```

... it's apparently using a different driver. According to:

lspci -nnk | grep -iA2 net
```
01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
        Subsystem: Acer Incorporated [ALI] Device [1025:061f]
        Kernel driver in use: r8169
02:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)
        Subsystem: Foxconn International, Inc. Device [105b:e042]
        Kernel driver in use: bcma-pci-bridge
```

I'm a wee bit weak on wireless but I'll try to come up with relevant info here.

On startup it seems to be trying to use brcmsmac (I cut the next couple of examples from kern.log):

```
May 25 08:09:01 WeePuter270 kernel: [   67.153789] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
May 25 08:09:01 WeePuter270 kernel: [   67.153807] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: enabled true, count 0 (implement)
May 25 08:09:01 WeePuter270 kernel: [   67.153818] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
```

Then it apparently doesn't work:

```
May 25 08:46:17 WeePuter270 kernel: [ 2302.479800] brcmsmac bcma0:0: START: tid 2 is not agg'able
May 25 08:48:55 WeePuter270 kernel: [ 2460.798566] brcmsmac bcma0:0: START: tid 1 is not agg'able
May 25 08:49:48 WeePuter270 kernel: [ 2513.897888] brcmsmac bcma0:0: START: tid 2 is not agg'able
```

This is info from the wifi site I'm talking about. Encryption mode seems to be WPA2 Version 1.

```
$ sudo iwlist scan

wlan0     Scan completed :
          Cell 01 - Address: 54:04:A6:CA:4E:0D
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=57/70  Signal level=-53 dBm  
                    Encryption key:on
                    ESSID:"******deleted******"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000015269ade183
                    Extra: Last beacon: 228ms ago
                    IE: Unknown: 00114A75737455732120576F6C6676696C6C65
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC191BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601001F00000000000000000000000000000000000000
                    IE: Unknown: DD09001018020EF02C0000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.
```

Hope that's enough and not too much.

Actually the wireless was much worse running 12.04. Installing linux backports 3.6 precise seemed to fix that, but there doesn't seem to be a raring version yet.

---

### Post by praseodym on 2013-05-25
Did you install the firmware for the driver?
```

wget media.cdn.ubuntu-de.org/forum/attachments/56/18/5007272-Broadcom_Firmware_070513.tar.gz
sudo tar xvf 5007272-Broadcom_Firmware_070513.tar.gz -C /lib/firmware 
```

---

### Post by Rob Sayer on 2013-05-26
No, but I'll definitely look into it.  After some bad experiences with Additional Drivers I've been reluctant to install those without a solid recommendation.

---

### Post by praseodym on 2013-05-26
Its the latest firmware from git:

[http://forum.ubuntuusers.de/topic/lenovo-s206-nach-installation-kein-wlan-discon/2/#post-5007272](http://forum.ubuntuusers.de/topic/lenovo-s206-nach-installation-kein-wlan-discon/2/#post-5007272)

---

### Post by Rob Sayer on 2013-05-26
I'll give it a try, but I think I may have to do blackisting modprobing etc, which I don't understand very well.  More research needed perhaps.  Thanks.

---

### Post by Rob Sayer on 2013-05-26
OK, I installed the tar file and rebooted.

Didn't get any "not agg'able" messages in kern.log.  Got this at the end of it:

```
kernel: [   62.045204] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: enabled true, count 1 (implement)
```

I'm taking this as a good sign.  I'll see how this works but I'm optimistic.  Thanks.

---

### Post by Rob Sayer on 2013-05-27
Hmm.  I'm not sure that worked now.  It's still cutting out and coming back.

And according to:

```
~$  lspci -nnk | grep -iA2 net
01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
        Subsystem: Acer Incorporated [ALI] Device [1025:061f]
        Kernel driver in use: r8169
02:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)
        Subsystem: Foxconn International, Inc. Device [105b:e042]
        Kernel driver in use: bcma-pci-bridge
```

It's still using the same wireless driver as before.  I was expecting it to be using brcmsmac.

Is there something else I need to do here?  I'm iffy on how to do modprobe etc.

---

### Post by praseodym on 2013-05-27
Check now:
```

lsmod
iwconfig
rfkill list
dmesg | egrep 'bcma|brcm'
```

---

### Post by Rob Sayer on 2013-05-28
OK, thanks.

I'm on a different wireless node now, hope that doesn't invalidate things.

lsmod:

```
~$ lsmod
Module                  Size  Used by
nls_iso8859_1          12617  1 
snd_hrtimer            12648  1 
parport_pc             27504  0 
rfcomm                 37420  0 
bnep                   17669  2 
ppdev                  12817  0 
bluetooth             202069  10 bnep,rfcomm
binfmt_misc            17260  1 
arc4                   12543  2 
brcmsmac              521468  0 
usb_storage            47684  1 
cordic                 12518  1 brcmsmac
uvcvideo               71279  0 
brcmutil               14355  1 brcmsmac
mac80211              526519  1 brcmsmac
videobuf2_vmalloc      12920  1 uvcvideo
snd_hda_codec_realtek    63791  1 
videobuf2_memops       13042  1 videobuf2_vmalloc
snd_hda_codec_hdmi     36185  1 
videobuf2_core         39161  1 uvcvideo
snd_hda_intel          38307  3 
cfg80211              436177  2 brcmsmac,mac80211
snd_hda_codec         117580  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
videodev               95806  2 uvcvideo,videobuf2_core
snd_hwdep              13272  1 snd_hda_codec
snd_pcm                80890  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_page_alloc         14230  2 snd_pcm,snd_hda_intel
snd_seq_midi           13132  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_rawmidi            25114  1 snd_seq_midi
snd_seq                51280  3 snd_seq_midi_event,snd_seq_midi
coretemp               13131  0 
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              24411  3 snd_hrtimer,snd_pcm,snd_seq
snd                    56485  17 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device
rtsx_pci_ms            12875  0 
soundcore              12600  1 snd
joydev                 17097  0 
acer_wmi               27592  0 
lp                     13299  0 
lpc_ich                16925  0 
bcma                   39645  1 brcmsmac
sparse_keymap          13658  1 acer_wmi
memstick               15842  1 rtsx_pci_ms
mac_hid                13037  0 
psmouse                81038  0 
serio_raw              13031  0 
microcode              18286  0 
parport                40753  3 lp,ppdev,parport_pc
hid_generic            12484  0 
usbhid                 41805  0 
hid                    82666  2 hid_generic,usbhid
rtsx_pci_sdmmc         17238  0 
gma500_gfx            167754  2 
ahci                   25507  2 
libahci                26108  1 ahci
i2c_algo_bit           13197  1 gma500_gfx
drm_kms_helper         47545  1 gma500_gfx
r8169                  61531  0 
drm                   228750  3 drm_kms_helper,gma500_gfx
wmi                    18590  1 acer_wmi
rtsx_pci               32018  2 rtsx_pci_ms,rtsx_pci_sdmmc
video                  18894  2 acer_wmi,gma500_gfx

```


iwconfig:
```
~$ iwconfig
wlan0     IEEE 802.11bgn  ESSID:"***different wireless from previous example***"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 0C:85:25:7E:C1:E0   
          Bit Rate=43.3 Mb/s   Tx-Power=19 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-40 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:4  Invalid misc:64   Missed beacon:0

lo        no wireless extensions.

eth0      no wireless extensions.
```

rfkill list:
```
~$ rfkill list
0: acer-wireless: Wireless LAN
        Soft blocked: no
        Hard blocked: no
1: phy0: Wireless LAN
        Soft blocked: no
        Hard blocked: no
```
 
dmesg | egrep 'bcma|brcm':
```
~$ dmesg | egrep 'bcma|brcm'
[   14.320283] bcma: bus0: Found chip with id 0x4313, rev 0x01 and package 0x08
[   14.320330] bcma: bus0: Core 0 found: ChipCommon (manuf 0x4BF, id 0x800, rev 0x24, class 0x0)
[   14.320418] bcma: bus0: Core 1 found: IEEE 802.11 (manuf 0x4BF, id 0x812, rev 0x18, class 0x0)
[   14.320659] bcma: bus0: Core 2 found: PCIe (manuf 0x4BF, id 0x820, rev 0x11, class 0x0)
[   14.335012] bcma: bus0: Bus registered
[   15.860459] brcmsmac bcma0:0: mfg 4bf core 812 rev 24 class 0 irq 17
[   19.595974] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[   19.595994] brcmsmac bcma0:0: brcms_ops_config: change power-save mode: false (implement)
[  115.765213] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[  115.765228] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: enabled true, count 0 (implement)
[  115.765237] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[  116.616906] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[  116.616945] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: enabled false, count 0 (implement)
[  116.616964] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[  117.535991] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[  117.536003] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: enabled true, count 0 (implement)
[  117.536009] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[  132.045495] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: enabled true, count 1 (implement)


```

---

### Post by praseodym on 2013-05-28
Try alternatively the Broadcom-STA driver.

---

### Post by Rob Sayer on 2013-05-29
OK, I'll try it in synaptic this time.  Thanks.

Edit:  Just installed bcmwl-kernel-source from synaptic and rebooted.  The wireless is working.  I'll have to rub it for a while to see if it cuts in and out.  Hopefully I'll be able to mark this 'solved'.

---

### Post by Rob Sayer on 2013-05-29
All right.  I've been using bcmwl-kernel-source on this machine on the original site I was bogging down badly on for a while.  No problems.  

In the past I've had 'additional drivers' bork the system so I was reluctant to use that stuff.  Maybe synaptic was a better way to install?

I'll mark it 'solved', and hopefully that works better than the last time I tried it.

Thanks.

---

