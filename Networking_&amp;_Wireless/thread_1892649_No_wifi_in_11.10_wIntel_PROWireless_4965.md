---
title: "No wifi in 11.10 w/Intel PRO/Wireless 4965"
date: 2011-12-08
forum: Networking &amp; Wireless
---

### Post by rdhddad on 2011-12-08
Please advise. Posted a week ago but only go so far.

Thanks!

-rdhddad

---

### Post by rdhddad on 2011-12-08
Here's some data gathered from a command in another posting about the same driver:

lshw -c network && lspci -nn && lsmod && lspci -nn | awk '/Wireless/ {print $11 ,$15}'&& rfkill list all
  *-network               
       description: Ethernet interface
       product: 82566MM Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 03
       serial: 00:1e:ec:8e:d5:6a
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.3.10-k2 duplex=full firmware=0.3-0 ip=10.12.33.66 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:44 memory:d8520000-d853ffff memory:d8540000-d8540fff ioport:5040(size=32)
  *-network DISABLED
       description: Wireless interface
       product: PRO/Wireless 4965 AG or AGN [Kedron] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:10:00.0
       logical name: wlan0
       version: 61
       serial: 00:21:5c:69:e2:5d
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwl4965 driverversion=3.0.0-13-generic firmware=228.61.2.24 latency=0 link=no multicast=yes wireless=IEEE 802.11abg
       resources: irq:47 memory:d8000000-d8001fff
00:00.0 Host bridge [0600]: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub [8086:2a00] (rev 0c)
00:01.0 PCI bridge [0604]: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port [8086:2a01] (rev 0c)
00:03.0 Communication controller [0780]: Intel Corporation Mobile PM965/GM965 MEI Controller [8086:2a04] (rev 0c)
00:03.2 IDE interface [0101]: Intel Corporation Mobile PM965/GM965 PT IDER Controller [8086:2a06] (rev 0c)
00:03.3 Serial controller [0700]: Intel Corporation Mobile PM965/GM965 KT Controller [8086:2a07] (rev 0c)
00:19.0 Ethernet controller [0200]: Intel Corporation 82566MM Gigabit Network Connection [8086:1049] (rev 03)
00:1a.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 [8086:2834] (rev 03)
00:1a.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 [8086:2835] (rev 03)
00:1a.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 [8086:283a] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801H (ICH8 Family) HD Audio Controller [8086:284b] (rev 03)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 [8086:283f] (rev 03)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 [8086:2841] (rev 03)
00:1c.4 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 [8086:2847] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 [8086:2830] (rev 03)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 [8086:2831] (rev 03)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 [8086:2832] (rev 03)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 [8086:2836] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev f3)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801HBM (ICH8M-E) LPC Interface Controller [8086:2811] (rev 03)
00:1f.1 IDE interface [0101]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller [8086:2850] (rev 03)
00:1f.2 SATA controller [0106]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller [8086:2829] (rev 03)
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc M64-S [Mobility Radeon X2300] [1002:7188]
02:06.0 CardBus bridge [0607]: Ricoh Co Ltd RL5c476 II [1180:0476] (rev b9)
02:06.1 CardBus bridge [0607]: Ricoh Co Ltd RL5c476 II [1180:0476] (rev b9)
02:06.2 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832] (rev 03)
02:06.3 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 20)
10:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection [8086:4229] (rev 61)
Module                  Size  Used by
nls_iso8859_1          12713  0 
nls_cp437              16991  0 
vfat                   17585  0 
fat                    61475  1 vfat
usb_storage            57901  0 
uas                    18027  0 
rfcomm                 47946  0 
bnep                   18436  2 
bluetooth             166112  10 rfcomm,bnep
pci_stub               12622  1 
vboxpci                23200  0 
vboxnetadp             13382  0 
vboxnetflt             23441  0 
vboxdrv               282739  4 vboxpci,vboxnetadp,vboxnetflt
binfmt_misc            17540  1 
dm_crypt               23199  1 
pata_pcmcia            17074  1 
tpm_infineon           17536  0 
arc4                   12529  2 
joydev                 17693  0 
pcmcia                 49378  1 pata_pcmcia
ppdev                  17113  0 
hp_wmi                 18092  0 
sparse_keymap          13890  1 hp_wmi
snd_hda_codec_analog    93522  1 
snd_hda_intel          33390  2 
snd_hda_codec         104802  2 snd_hda_codec_analog,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
yenta_socket           28084  0 
snd_pcm                96755  2 snd_hda_intel,snd_hda_codec
pcmcia_rsrc            18430  1 yenta_socket
pcmcia_core            22614  3 pcmcia,yenta_socket,pcmcia_rsrc
snd_seq_midi           13324  0 
iwl4965               132375  0 
psmouse                73882  0 
irda                  201273  0 
iwl_legacy             83487  1 iwl4965
serio_raw              13166  0 
snd_rawmidi            30547  1 snd_seq_midi
crc_ccitt              12667  1 irda
mac80211              462092  2 iwl4965,iwl_legacy
parport_pc             36962  1 
tpm_tis                18546  0 
cfg80211              199587  3 iwl4965,iwl_legacy,mac80211
snd_seq_midi_event     14899  1 snd_seq_midi
hp_accel               21880  0 
lis3lv02d              19888  1 hp_accel
input_polldev          13896  1 lis3lv02d
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
lm63                   14398  0 
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
mei                    41480  0 
snd                    68266  13 snd_hda_codec_analog,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
lp                     17799  0 
parport                46562  3 ppdev,parport_pc,lp
usbhid                 47198  0 
hid                    95463  1 usbhid
radeon               1016085  3 
firewire_ohci          40722  0 
sdhci_pci              14032  0 
sdhci                  32166  1 sdhci_pci
firewire_core          63626  1 firewire_ohci
crc_itu_t              12707  1 firewire_core
ahci                   26002  2 
libahci                26861  1 ahci
video                  19412  0 
ttm                    76805  1 radeon
drm_kms_helper         42558  1 radeon
drm                   236330  5 radeon,ttm,drm_kms_helper
wmi                    19256  1 hp_wmi
e1000e                160582  0 
i2c_algo_bit           13423  1 radeon
AGN [8086:4229]
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
1: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
2: hp-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: yes

---

### Post by rdhddad on 2011-12-08
This is now fixed. Resetting my BIOS settings back to 'default' worked. Thanks...

---

