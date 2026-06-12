---
title: "HP dv6-7013tx Wireless not working"
date: 2012-12-25
forum: Networking &amp; Wireless
---

### Post by abhikandoi2000 on 2012-12-25
I installed Ubuntu 12.04 LTS on my laptop but I am not able to run wireless network. Mine is a BCM4313 802.11b/g/n Wireless LAN Controller. I am not able to turn on my wifi. It is orange light anytime. But the wireless works fine in Windows 7.

I have tried installing the drivers using ndiswrapper...but it just doesn't work.

Here are some of the outputs of commands.

```
sudo lshw -C network
```
```
*-network UNCLAIMED     
       description: Network controller
       product: BCM4313 802.11b/g/n Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0a:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:d4500000-d4503fff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:0b:00.0
       logical name: eth0
       version: 07
       serial: a0:b3:cc:44:12:c0
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8168e-3_0.0.4 03/27/12 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:43 ioport:2000(size=256) memory:d4404000-d4404fff memory:d4400000-d4403fff
  *-network
       description: Ethernet interface
       physical id: 3
       logical name: usb0
       serial: 1e:71:7f:d2:d9:52
       capabilities: ethernet physical
       configuration: broadcast=yes driver=rndis_host driverversion=22-Aug-2005 firmware=RNDIS device ip=192.168.42.9 link=yes multicast=yes]
```

```
lspci
```
```
00:00.0 Host bridge: Intel Corporation Ivy Bridge DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Ivy Bridge PCI Express Root Port (rev 09)
00:02.0 VGA compatible controller: Intel Corporation Ivy Bridge Graphics Controller (rev 09)
00:14.0 USB controller: Intel Corporation Panther Point USB xHCI Host Controller (rev 04)
00:16.0 Communication controller: Intel Corporation Panther Point MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation Panther Point USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation Panther Point High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 1 (rev c4)
00:1c.2 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 3 (rev c4)
00:1c.3 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 4 (rev c4)
00:1c.5 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 6 (rev c4)
00:1d.0 USB controller: Intel Corporation Panther Point USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation Panther Point LPC Controller (rev 04)
00:1f.2 RAID bus controller: Intel Corporation 82801 Mobile SATA Controller [RAID mode] (rev 04)
00:1f.3 SMBus: Intel Corporation Panther Point SMBus Controller (rev 04)
01:00.0 VGA compatible controller: NVIDIA Corporation Device 0de9 (rev a1)
08:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. Device 5229 (rev 01)
0a:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller (rev 01)
0b:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 07)
```

```
lsmod
```
```
Module                  Size  Used by
ndiswrapper           282672  0 
btusb                  18332  2 
rndis_host             13848  0 
cdc_ether              13536  1 rndis_host
usbnet                 26212  2 rndis_host,cdc_ether
uas                    18180  0 
usb_storage            49198  0 
pci_stub               12622  1 
vboxpci                23237  0 
vboxnetadp             25670  0 
vboxnetflt             23478  0 
vboxdrv               320210  3 vboxpci,vboxnetadp,vboxnetflt
rfcomm                 47604  12 
parport_pc             32866  0 
ppdev                  17113  0 
bnep                   18281  2 
bluetooth             180153  23 btusb,rfcomm,bnep
binfmt_misc            17540  1 
snd_hda_codec_hdmi     32474  1 
snd_hda_codec_idt      70795  1 
mxm_wmi                13021  0 
uvcvideo               72627  0 
nvidia               9367655  0 
videodev               98259  1 uvcvideo
v4l2_compat_ioctl32    17128  1 videodev
joydev                 17693  0 
snd_hda_intel          33773  3 
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              17764  1 snd_hda_codec
snd_pcm                97275  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30748  1 snd_seq_midi
psmouse                97485  0 
serio_raw              13211  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61929  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
i915                  477545  0 
snd                    79041  16 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm_kms_helper         46978  1 i915
drm                   241971  2 i915,drm_kms_helper
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
mei                    41616  0 
i2c_algo_bit           13423  1 i915
wmi                    19256  1 mxm_wmi
mac_hid                13253  0 
video                  19596  1 i915
hp_accel               25976  0 
lis3lv02d              19876  1 hp_accel
input_polldev          13896  1 lis3lv02d
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
usbhid                 47238  0 
hid                    99636  1 usbhid
r8169                  62154  0
```

Please help.

---

### Post by jack454 on 2012-12-25
If you have wired access to the internet you can type this command without the quotes in a terminal and it should get it working after a reboot.```
"sudo apt-get install bcmwl-kernel-source"
```

---

### Post by abhikandoi2000 on 2012-12-26
> **jack454 said:**
> If you have wired access to the internet you can type this command without the quotes in a terminal and it should get it working after a reboot.```
"sudo apt-get install bcmwl-kernel-source"
```

Already the latest. Still not working.
Help..

---

