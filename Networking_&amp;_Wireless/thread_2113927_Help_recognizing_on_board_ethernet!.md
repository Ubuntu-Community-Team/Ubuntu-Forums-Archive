---
title: "Help recognizing on board ethernet!"
date: 2013-02-08
forum: Networking &amp; Wireless
---

### Post by Magz999 on 2013-02-08
I have read quite a few threads now and it seems there are similar problems, but no one has had the same problem I am having. I'm pretty new to Ubuntu bot not computers so I am trying my best. Hopefully I can provide you with enough info.

I have a Gigabyte 78LMT-S2P MoBo

[COLOR="Blue"]root@megamind:/home/magz# sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: AR8151 v2.0 Gigabit Ethernet
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: c0
       serial: 90:2b:34:26:2f:8e
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.0-NAPI latency=0 link=no multicast=yes port=twisted pair
       resources: irq:41 memory:fddc0000-fddfffff ioport:df00(size=128)
  *-network
       description: Wireless interface
       product: RT2500 Wireless 802.11bg
       vendor: Ralink corp.
       physical id: 6
       bus info: pci@0000:03:06.0
       logical name: wlan0
       version: 01
       serial: 00:0f:66:6d:3f:47
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2500pci driverversion=3.5.0-23-generic firmware=N/A ip=192.168.1.30 latency=32 link=yes multicast=yes wireless=IEEE 802.11bg
       resources: irq:20 memory:fdcfe000-fdcfffff
[/COLOR]

[COLOR="Green"]root@megamind:/home/magz# lspci -nn | grep 0280
03:06.0 Network controller [0280]: Ralink corp. RT2500 Wireless 802.11bg [1814:0201] (rev 01)
[/COLOR]

[COLOR="Indigo"]root@megamind:/home/magz# iwconfig
eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"WENDY_Network"  
          Mode:Managed  Frequency:2.422 GHz  Access Point: E0:46:9A:3A:57:F2   
          Bit Rate=54 Mb/s   Tx-Power=27 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=53/70  Signal level=-57 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:1753  Invalid misc:87943   Missed beacon:0
[/COLOR]

[COLOR="Sienna"]root@megamind:/home/magz# rfkill list all
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
[/COLOR]

[COLOR="DarkSlateGray"]root@megamind:/home/magz# lsmod
Module                  Size  Used by
atl1e                  33209  0 
nls_utf8               12558  1 
udf                    89521  1 
crc_itu_t              12708  1 udf
nls_iso8859_1          12714  1 
pci_stub               12623  1 
vboxpci                23195  0 
vboxnetadp             25671  0 
vboxnetflt             23480  0 
vboxdrv               287190  3 vboxpci,vboxnetadp,vboxnetflt
bnep                   18141  2 
rfcomm                 46620  0 
bluetooth             209249  10 bnep,rfcomm
parport_pc             32689  0 
ppdev                  17074  0 
usblp                  18141  0 
snd_hda_codec_realtek    78048  1 
binfmt_misc            17501  1 
snd_hda_intel          33492  3 
arc4                   12530  2 
snd_hda_codec         134213  2 snd_hda_codec_realtek,snd_hda_intel
radeon                895730  5 
snd_usb_audio         130468  1 
rt2500pci              27182  0 
rt2x00pci              14476  1 rt2500pci
snd_hwdep              17699  2 snd_hda_codec,snd_usb_audio
rt2x00lib              54939  2 rt2500pci,rt2x00pci
snd_usbmidi_lib        24954  1 snd_usb_audio
snd_pcm                96668  3 snd_hda_intel,snd_hda_codec,snd_usb_audio
snd_seq_midi           13325  0 
snd_seq_midi_event     14900  1 snd_seq_midi
snd_rawmidi            30513  2 snd_usbmidi_lib,snd_seq_midi
ttm                    83596  1 radeon
mac80211              539958  2 rt2x00pci,rt2x00lib
snd_seq                61555  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29426  2 snd_pcm,snd_seq
snd_seq_device         14498  3 snd_seq_midi,snd_rawmidi,snd_seq
drm_kms_helper         49113  1 radeon
drm                   288721  7 radeon,ttm,drm_kms_helper
joydev                 17458  0 
cfg80211              206797  2 rt2x00lib,mac80211
kvm_amd                55605  0 
kvm                   414071  1 kvm_amd
snd                    78921  19 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_usb_audio,snd_hwdep,snd_usbmidi_lib,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
sp5100_tco             13698  0 
soundcore              15048  1 snd
i2c_algo_bit           13414  1 radeon
eeprom_93cx6           13345  1 rt2500pci
edac_core              52452  0 
snd_page_alloc         18485  2 snd_hda_intel,snd_pcm
i2c_piix4              13168  0 
edac_mce_amd           23304  0 
k10temp                13127  0 
microcode              22804  0 
mac_hid                13206  0 
shpchp                 37109  0 
serio_raw              13216  0 
wmi                    19071  0 
lp                     17760  0 
parport                46346  3 parport_pc,ppdev,lp
hid_logitech           26586  0 
ff_memless             13014  1 hid_logitech
hid_generic            12541  0 
usbhid                 46987  1 hid_logitech
hid                   100411  3 hid_logitech,hid_generic,usbhid
pata_atiixp            13205  0 
atl1c                  41102  0 
usb_storage            48839  1 
[/COLOR]

This is the error I get after following the directions from previous threads from other users:

[COLOR="Red"]magz@megamind:~$ tar -xzvf*AR81Family-Linux-v1.0.1.9.tar.gz
tar (child): *AR81Family-Linux-v1.0.1.9.tar.gz: Cannot open: No such file or directory
tar (child): Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error is not recoverable: exiting now[/COLOR]


Anybody think they can help a noob out? It would be greatly appreciated.

---

### Post by chili555 on 2013-02-08
It looks recognized to me:> *-network
description: Ethernet interface
product: AR8151 v2.0 Gigabit Ethernet
vendor: Atheros Communications Inc.
physical id: 0
bus info: pci@0000:02:00.0
logical name: [COLOR="Red"]eth0[/COLOR]
version: c0
serial: 90:2b:34:26:2f:8e
capacity: 1Gbit/s
width: 64 bits
clock: 33MHz
capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes [COLOR="Red"]driver=atl1c[/COLOR] driverversion=1.0.1.0-NAPI latency=0 link=no multicast=yes port=twisted pairWhat does it do or not do?

---

