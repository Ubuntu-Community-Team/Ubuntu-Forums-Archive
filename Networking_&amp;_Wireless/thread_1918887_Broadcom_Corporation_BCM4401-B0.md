---
title: "Broadcom Corporation BCM4401-B0"
date: 2012-02-01
forum: Networking &amp; Wireless
---

### Post by GregD001 on 2012-02-01
Hello,
I just installed ubuntu 11.10 on a dell e1505.
And I am another person with wireless problems.

Here are some photos:

[IMG]http://imageshack.us/photo/my-images/843/screenshotat20120201201.png[/IMG]

[http://imageshack.us/photo/my-images/843/screenshotat20120201201.png](http://imageshack.us/photo/my-images/843/screenshotat20120201201.png)


[IMG]http://imageshack.us/photo/my-images/819/wirelessl.jpg[/IMG]
[http://imageshack.us/photo/my-images/819/wirelessl.jpg](http://imageshack.us/photo/my-images/819/wirelessl.jpg)

Here are some things I have tried:

ubuntu@ubuntu-MM061:~$ sudo lshw -C network
[sudo] password for ubuntu: 
  *-network               
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:16 memory:dfcfc000-dfcfffff
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth1
       version: 02
       serial: 00:15:c5:13:ab:a5
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=192.168.2.5 latency=64 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:17 memory:df9fe000-df9fffff



ubuntu@ubuntu-MM061:~$ lspci -nnk | grep -iA2 net
03:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
	Subsystem: Dell Inspiron 6400 [1028:01af]
	Kernel driver in use: b44
--
0b:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
	Subsystem: Dell Wireless 1390 WLAN Mini-Card [1028:0007]
	Kernel driver in use: b43-pci-bridge


ubuntu@ubuntu-MM061:~$ iwconfig
lo        no wireless extensions.

eth1      no wireless extensions.


ubuntu@ubuntu-MM061:~$ lsmod
Module                  Size  Used by
usbhid                 41905  0 
hid                    77367  1 usbhid
parport_pc             32114  0 
ppdev                  12849  0 
bnep                   17923  2 
rfcomm                 38408  0 
bluetooth             148839  10 bnep,rfcomm
joydev                 17393  0 
binfmt_misc            17292  1 
dell_laptop            13519  0 
dcdbas                 14098  1 dell_laptop
b44                    31443  0 
snd_hda_codec_idt      60049  1 
radeon                925178  3 
snd_hda_intel          24262  2 
snd_hda_codec          91859  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80435  2 snd_hda_intel,snd_hda_codec
ssb                    50682  1 b44
wl                   2646601  0 
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
ttm                    65224  1 radeon
drm_kms_helper         32889  1 radeon
drm                   192194  5 radeon,ttm,drm_kms_helper
r592                   17808  0 
r852                   17901  0 
snd_seq_midi_event     14475  1 snd_seq_midi
sm_common              16737  1 r852
nand                   49706  2 r852,sm_common
nand_ids                8547  1 nand
nand_bch               13003  1 nand
bch                    21757  1 nand_bch
nand_ecc               13070  1 nand
psmouse                73673  0 
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
memstick               15857  1 r592
serio_raw              12990  0 
mtd                    35852  2 sm_common,nand
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
i2c_algo_bit           13199  1 radeon
lib80211               14570  1 wl
video                  18908  0 
snd                    55902  13 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
firewire_ohci          35854  0 
firewire_core          56937  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
sdhci_pci              13658  0 
sdhci                  27360  1 sdhci_pci
c

sudo apt-get purge bcmwl-kernel-source broadcom-sta-common broadcom-sta-source
sudo apt-get install b43-fwcutter firmware-b43-installer


Any ideas?

thanks

---

### Post by bkratz on 2012-02-02
Your lsmod listing also shows up the module wl (the sta driver) as well as b43. STA probably created a blacklist entry for the b43 driver which is the correct one for you card. See the last few paragraphs of this page for information about the blacklist.

[https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_Natty_11.04](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_Natty_11.04)

---

