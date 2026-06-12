---
title: "No wifi - no success after one day of searching"
date: 2013-02-17
forum: Networking &amp; Wireless
---

### Post by ingimar on 2013-02-17
Hello,

I was using Ubuntu 12 earlier with no problems. Then a course I'm taking in school has a system that only runs on Ubuntu 11 so I had to change. When I was installing Ubuntu 11 my computer could not find internet - and it is in that state now. The internet dropdown only displays Wired Network, Mobile Broadband - no Wifi's.

I'm using Ubuntu along side Windows 8 with dual boot. Windows 8 has internet, so the problem is not the hardware.

I've tried plugging in the cable and updating Ubuntu and also downloaded Windows Wireless Drivers and the right Windows driver - with no success.

Any help appreciated..

Here are some related print outs from commands in terminal that I have seen on forums:

```

ingimar@ingimar-ThinkPad-Edge-S430:~$ **fconfig**
eth0      Link encap:Ethernet  HWaddr b8:88:e3:32:87:11  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:42 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

usb0      Link encap:Ethernet  HWaddr 02:15:e0:ec:01:00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

----------------------------------------------------------------------

ingimar@ingimar-ThinkPad-Edge-S430:~$ **sudo lshw -C network**
[sudo] password for ingimar: 
  *-network UNCLAIMED     
       description: Network controller
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: c4
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list
       configuration: latency=0
       resources: memory:d1d00000-d1d01fff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 07
       serial: b8:88:e3:32:87:11
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=N/A latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:42 ioport:2000(size=256) memory:d0c04000-d0c04fff memory:d0c00000-d0c03fff
  *-network
       description: Ethernet interface
       physical id: 2
       logical name: usb0
       serial: 02:15:e0:ec:01:00
       capabilities: ethernet physical
       configuration: broadcast=yes driver=cdc_ncm driverversion=04-Aug-2011 firmware=CDC NCM link=no multicast=yes

----------------------------------------------------------------------

ingimar@ingimar-ThinkPad-Edge-S430:~$ **lspci -nnk | grep -iA2 net**
03:00.0 Network controller [0280]: Intel Corporation Device [8086:0888] (rev c4)
    Subsystem: Intel Corporation Device [8086:4262]
    Kernel modules: iwlagn
04:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 07)
    Subsystem: Lenovo Device [17aa:21fc]
    Kernel driver in use: r8169

----------------------------------------------------------------------

ingimar@ingimar-ThinkPad-Edge-S430:~$ **iwconfig**
lo        no wireless extensions.

eth0      no wireless extensions.

usb0      no wireless extensions.

----------------------------------------------------------------------

ingimar@ingimar-ThinkPad-Edge-S430:~$ **rfkill list all**
0: tpacpi_bluetooth_sw: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: tpacpi_wwan_sw: Wireless WAN
    Soft blocked: no
    Hard blocked: no
2: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no


----------------------------------------------------------------------

ingimar@ingimar-ThinkPad-Edge-S430:~$ **lsmod**
Module                  Size  Used by
nls_iso8859_1          12617  0 
nls_cp437              12751  0 
vfat                   17308  0 
fat                    55577  1 vfat
usb_storage            44172  0 
bnep                   17923  2 
rfcomm                 38408  8 
parport_pc             32114  0 
ppdev                  12849  0 
joydev                 17393  0 
binfmt_misc            17292  1 
snd_hda_codec_hdmi     31426  1 
snd_hda_codec_realtek   254163  1 
cdc_ncm                17199  0 
usbnet                 25214  1 cdc_ncm
uvcvideo               67271  0 
videodev               85626  1 uvcvideo
cdc_wdm                17317  0 
cdc_acm                22276  0 
snd_hda_intel          28358  2 
snd_hda_codec          91888  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
i915                  513895  3 
drm_kms_helper         32889  1 i915
drm                   192194  4 i915,drm_kms_helper
i2c_algo_bit           13199  1 i915
snd_pcm                80469  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
btusb                  18160  2 
bluetooth             148869  23 bnep,rfcomm,btusb
iwlagn                273980  0 
mac80211              393421  1 iwlagn
cfg80211              172427  2 iwlagn,mac80211
mei                    36466  0 
psmouse                73673  0 
serio_raw              12990  0 
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
wmi                    18744  0 
tpm_tis                14002  0 
thinkpad_acpi          73942  0 
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    56056  15 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,thinkpad_acpi,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
video                  19116  1 i915
soundcore              12600  1 snd
nvram                  14029  1 thinkpad_acpi
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
r8169                  47630  0 
ahci                   25730  3 
libahci                25727  1 ahci
xhci_hcd               77341  0 

----------------------------------------------------------------------

ingimar@ingimar-ThinkPad-Edge-S430:~$ **sudo cat /var/log/syslog | grep -e b43 -e wl -e firmware -e wlan0 | tail -n35**
Feb 17 01:16:47 ingimar-ThinkPad-Edge-S430 kernel: [ 2426.920453] Modules linked in: joydev parport_pc ppdev bnep rfcomm snd_hda_codec_hdmi snd_hda_codec_realtek cdc_ncm usbnet cdc_wdm cdc_acm uvcvideo videodev snd_hda_intel snd_hda_codec snd_hwdep iwlagn mac80211 btusb snd_pcm bluetooth cfg80211 psmouse snd_page_alloc serio_raw i915 drm_kms_helper drm binfmt_misc i2c_algo_bit mei(C) wmi tpm_tis thinkpad_acpi snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device snd soundcore nvram video lp parport ahci libahci r8169 xhci_hcd
Feb 17 01:20:01 ingimar-ThinkPad-Edge-S430 kernel: [   12.190714] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
Feb 17 01:20:01 ingimar-ThinkPad-Edge-S430 kernel: [   12.190717] iwlagn: Copyright(c) 2003-2011 Intel Corporation
Feb 17 01:20:01 ingimar-ThinkPad-Edge-S430 kernel: [   12.193623] iwlagn 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Feb 17 01:20:01 ingimar-ThinkPad-Edge-S430 kernel: [   12.193653] iwlagn 0000:03:00.0: setting latency timer to 64
Feb 17 01:20:01 ingimar-ThinkPad-Edge-S430 kernel: [   12.193693] iwlagn 0000:03:00.0: Detected 2000 Series 2x2 BGN/BT, REV=0xC8
Feb 17 01:20:01 ingimar-ThinkPad-Edge-S430 kernel: [   12.212653] iwlagn 0000:03:00.0: device EEPROM VER=0x81c, CALIB=0x6
Feb 17 01:20:01 ingimar-ThinkPad-Edge-S430 kernel: [   12.212656] iwlagn 0000:03:00.0: Device SKU: 0X9
Feb 17 01:20:01 ingimar-ThinkPad-Edge-S430 kernel: [   12.212658] iwlagn 0000:03:00.0: Valid Tx ant: 0X3, Valid Rx ant: 0X3
Feb 17 01:20:01 ingimar-ThinkPad-Edge-S430 kernel: [   12.213540] iwlagn 0000:03:00.0: Tunable channels: 13 802.11bg, 0 802.11a channels
Feb 17 01:20:01 ingimar-ThinkPad-Edge-S430 kernel: [   12.213672] iwlagn 0000:03:00.0: irq 44 for MSI/MSI-X
Feb 17 01:20:01 ingimar-ThinkPad-Edge-S430 kernel: [   12.361551] Modules linked in: uvcvideo videodev snd_hda_intel(+) snd_hda_codec snd_hwdep cdc_ncm usbnet cdc_wdm cdc_acm snd_pcm btusb bluetooth iwlagn psmouse mac80211 snd_page_alloc serio_raw i915(+) cfg80211 drm_kms_helper drm i2c_algo_bit mei(C) wmi tpm_tis thinkpad_acpi snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device snd soundcore nvram video lp parport xhci_hcd r8169 ahci libahci
Feb 17 01:20:01 ingimar-ThinkPad-Edge-S430 kernel: [   12.361808] Modules linked in: uvcvideo videodev snd_hda_intel(+) snd_hda_codec snd_hwdep cdc_ncm usbnet cdc_wdm cdc_acm snd_pcm btusb bluetooth iwlagn psmouse mac80211 snd_page_alloc serio_raw i915(+) cfg80211 drm_kms_helper drm i2c_algo_bit mei(C) wmi tpm_tis thinkpad_acpi snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device snd soundcore nvram video lp parport xhci_hcd r8169 ahci libahci
Feb 17 01:20:01 ingimar-ThinkPad-Edge-S430 kernel: [   12.370940] iwlagn 0000:03:00.0: request for firmware file 'iwlwifi-2030-5.ucode' failed.
Feb 17 01:20:01 ingimar-ThinkPad-Edge-S430 kernel: [   12.370943] iwlagn 0000:03:00.0: no suitable firmware found!
Feb 17 01:20:01 ingimar-ThinkPad-Edge-S430 kernel: [   12.371110] iwlagn 0000:03:00.0: PCI INT A disabled
Feb 17 01:20:01 ingimar-ThinkPad-Edge-S430 NetworkManager[828]: <info> monitoring kernel firmware directory '/lib/firmware'.
Feb 17 01:20:10 ingimar-ThinkPad-Edge-S430 kernel: [   22.317624] IBM TrackPoint firmware: 0x0e, buttons: 3/3
Feb 17 09:33:47 ingimar-ThinkPad-Edge-S430 kernel: [   12.488456] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
Feb 17 09:33:47 ingimar-ThinkPad-Edge-S430 kernel: [   12.488458] iwlagn: Copyright(c) 2003-2011 Intel Corporation
Feb 17 09:33:47 ingimar-ThinkPad-Edge-S430 kernel: [   12.488528] iwlagn 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Feb 17 09:33:47 ingimar-ThinkPad-Edge-S430 kernel: [   12.488559] iwlagn 0000:03:00.0: setting latency timer to 64
Feb 17 09:33:47 ingimar-ThinkPad-Edge-S430 kernel: [   12.488613] iwlagn 0000:03:00.0: Detected 2000 Series 2x2 BGN/BT, REV=0xC8
Feb 17 09:33:47 ingimar-ThinkPad-Edge-S430 kernel: [   12.506001] iwlagn 0000:03:00.0: device EEPROM VER=0x81c, CALIB=0x6
Feb 17 09:33:47 ingimar-ThinkPad-Edge-S430 kernel: [   12.506004] iwlagn 0000:03:00.0: Device SKU: 0X9
Feb 17 09:33:47 ingimar-ThinkPad-Edge-S430 kernel: [   12.506006] iwlagn 0000:03:00.0: Valid Tx ant: 0X3, Valid Rx ant: 0X3
Feb 17 09:33:47 ingimar-ThinkPad-Edge-S430 kernel: [   12.518480] iwlagn 0000:03:00.0: Tunable channels: 13 802.11bg, 0 802.11a channels
Feb 17 09:33:47 ingimar-ThinkPad-Edge-S430 kernel: [   12.519074] iwlagn 0000:03:00.0: irq 43 for MSI/MSI-X
Feb 17 09:33:47 ingimar-ThinkPad-Edge-S430 kernel: [   12.682537] iwlagn 0000:03:00.0: request for firmware file 'iwlwifi-2030-5.ucode' failed.
Feb 17 09:33:47 ingimar-ThinkPad-Edge-S430 kernel: [   12.682541] iwlagn 0000:03:00.0: no suitable firmware found!
Feb 17 09:33:47 ingimar-ThinkPad-Edge-S430 kernel: [   12.682712] iwlagn 0000:03:00.0: PCI INT A disabled
Feb 17 09:33:47 ingimar-ThinkPad-Edge-S430 kernel: [   13.237603] Modules linked in: snd_hda_codec_hdmi snd_hda_codec_realtek cdc_ncm usbnet uvcvideo videodev cdc_wdm cdc_acm snd_hda_intel snd_hda_codec snd_hwdep i915(+) drm_kms_helper drm i2c_algo_bit snd_pcm btusb bluetooth iwlagn mac80211 cfg80211 mei(C) psmouse serio_raw snd_page_alloc wmi tpm_tis thinkpad_acpi snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device snd video soundcore nvram lp parport r8169 ahci libahci xhci_hcd
Feb 17 09:33:47 ingimar-ThinkPad-Edge-S430 kernel: [   13.237863] Modules linked in: snd_hda_codec_hdmi snd_hda_codec_realtek cdc_ncm usbnet uvcvideo videodev cdc_wdm cdc_acm snd_hda_intel snd_hda_codec snd_hwdep i915(+) drm_kms_helper drm i2c_algo_bit snd_pcm btusb bluetooth iwlagn mac80211 cfg80211 mei(C) psmouse serio_raw snd_page_alloc wmi tpm_tis thinkpad_acpi snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device snd video soundcore nvram lp parport r8169 ahci libahci xhci_hcd
Feb 17 09:33:47 ingimar-ThinkPad-Edge-S430 NetworkManager[881]: <info> monitoring kernel firmware directory '/lib/firmware'.
Feb 17 09:33:56 ingimar-ThinkPad-Edge-S430 kernel: [   22.811850] IBM TrackPoint firmware: 0x0e, buttons: 3/3
```

---

### Post by praseodym on 2013-02-17
Deactivate the N-mode of the driver (bug):

```

echo "options iwlagn 11n_disable=1" | sudo tee /etc/modprobe.d/iwlagn.conf
sudo modprobe -rfv iwlagn
sudo modprobe -v iwlagn
```

---

### Post by ingimar on 2013-02-17
That did not work. Any other ideas?

---

