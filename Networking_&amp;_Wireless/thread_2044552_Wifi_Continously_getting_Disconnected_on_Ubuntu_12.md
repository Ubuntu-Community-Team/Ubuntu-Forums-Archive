---
title: "Wifi Continously getting Disconnected on Ubuntu 12.04"
date: 2012-08-19
forum: Networking &amp; Wireless
---

### Post by anas22 on 2012-08-19
I have recently installed Ubuntu 12.04 LTS on my Lenovo Thinkpad dual booting it with Windows 7. My college Wifi works perfectly with Windows 7 and many people use it with Different distros of Linux too, even Ubuntu 12.04 with the same PC configuration.

I have installed all the upgradations suggesting my Update Manager too.

Here are the contents of my terminal for reference when i type these commands

lspci

```
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b4)
00:1c.1 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 (rev b4)
00:1c.2 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 3 (rev b4)
00:1c.3 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 4 (rev b4)
00:1c.5 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 6 (rev b4)
00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation HM65 Express Chipset Family LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 04)
03:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter (rev 01)
04:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5116 PCI Express Card Reader (rev 01)
09:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)

```sudo lshw -C network

```
  *-network               
       description: Wireless interface
       product: RTL8188CE 802.11b/g/n WiFi Adapter
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 01
       serial: ec:55:f9:c8:21:cf
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8192ce driverversion=3.2.0-29-generic firmware=N/A ip=10.75.2.55 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 ioport:2000(size=256) memory:f0500000-f0503fff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 03
       serial: e8:9a:8f:82:5d:ed
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl_nic/rtl8168d-2.fw latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:41 ioport:4000(size=256) memory:f0a04000-f0a04fff memory:f0a00000-f0a03fff

```lsmod

```
Module                  Size  Used by
snd_hda_codec_hdmi     32474  1 
snd_hda_codec_realtek   224066  1 
joydev                 17693  0 
bnep                   18281  2 
rfcomm                 47604  12 
parport_pc             32866  0 
ppdev                  17113  0 
arc4                   12529  2 
thinkpad_acpi          81819  0 
snd_seq_midi           13324  0 
snd_rawmidi            30748  1 snd_seq_midi
snd_hda_intel          33773  3 
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                97188  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi_event     14899  1 snd_seq_midi
rtl8192ce              84826  0 
rts_pstor             445196  0 
rtl8192c_common        75767  1 rtl8192ce
rtlwifi               111202  1 rtl8192ce
mac80211              506816  3 rtl8192ce,rtl8192c_common,rtlwifi
uvcvideo               72627  0 
videodev               98259  1 uvcvideo
v4l2_compat_ioctl32    17128  1 videodev
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
psmouse                87692  0 
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
serio_raw              13211  0 
cfg80211              205544  2 rtlwifi,mac80211
btusb                  18288  2 
snd                    78855  17 snd_hda_codec_hdmi,snd_hda_codec_realtek,thinkpad_acpi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_rawmidi,snd_pcm,snd_seq,snd_timer,snd_seq_device
bluetooth             180104  23 bnep,rfcomm,btusb
i915                  472941  3 
drm_kms_helper         46978  1 i915
drm                   242038  4 i915,drm_kms_helper
soundcore              15091  1 snd
nvram                  14413  1 thinkpad_acpi
i2c_algo_bit           13423  1 i915
wmi                    19256  0 
tpm_tis                18804  0 
mei                    41616  0 
video                  19596  1 i915
mac_hid                13253  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
r8169                  62099  0 
```Can you figure out whats wrong ? Thanks

---

### Post by wildmanne39 on 2012-08-19
Hi, do everything in post #6 at this link.
[http://ubuntuforums.org/showthread.php?p=12171877#post12171877](http://ubuntuforums.org/showthread.php?p=12171877#post12171877)
Thanks

---

### Post by SUPERFITTER on 2012-08-20
Hi Wild Man

Will this work for my Wifi Continously getting Disconnected on Ubuntu 12.04?

[http://ubuntuforums.org/showthread.php?t=2039038](http://ubuntuforums.org/showthread.php?t=2039038)

Looks like a lot of people are having this problem.

---

### Post by anas22 on 2012-08-20
I did as you said about creating a new file and writing that line

I cant find option to do this task

> change 802.11bgn to 802.11bg.How do I do this ? 

Thanks

---

### Post by wildmanne39 on 2012-08-20
Hi anas22, you need to be wired to your router then open your web browser and type 192.168.0.1 into the address bar and hopefully that will open your routers configuration page if not you will need to find out what numbers do then look until you see that setting and change it, then save and close.
Thanks

---

### Post by anas22 on 2012-08-21
Its a college Common Router.... I can connect through wire and change its settings...

Is there any other way to stop disconnects ?

---

### Post by wildmanne39 on 2012-08-21
Hi, if you are still having issues that is the last thing that usually fixes 
it.
Thanks

---

### Post by tbc on 2013-04-07
Try disabling IPv6. See [Wireless connection is lost periodically and without apparent reason and is quickly reestablished on a BCM4312]("http://askubuntu.com/questions/128024/wireless-connection-is-lost-periodically-and-without-apparent-reason-and-is-quic") (askubuntu.com).

---

