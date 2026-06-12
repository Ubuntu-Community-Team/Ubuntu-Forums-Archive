---
title: "Broadcom driver - Help"
date: 2010-06-09
forum: Networking &amp; Wireless
---

### Post by ether3al on 2010-06-09
Hi All,

I am having difficulties getting the broadcom drivers installed on my laptop. It is working fine with the propriety linux drivers however they lack functionality.

I have found articles about using fwcutter however I have not had any success. 

I am hoping someone can assist! 

I have tried the following:
wget [http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2](http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2)
tar xjf broadcom-wl-4.150.10.5.tar.bz2
cd broadcom-wl-4.150.10.5/driver
sudo b43-fwcutter -w /lib/firmware/b43 wl_apsta_mimo.o

However I encounter this error:
Sorry, the input file is either wrong or not supported by b43-fwcutter.
This file has an unknown MD5sum 80c7bb743de4025f57ac7166dac7bc4a

Hope information below can offer some assistance:

lshw -C Network
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: BCM4312 802.11a/b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth1
       version: 01
       serial: 00:1a:73:03:eb:4d
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.60.48.36 ip=10.1.1.2 latency=0 multicast=yes wireless=IEEE 802.11
       resources: irq:19 memory:b3000000-b3003fff
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes

lsmod

Module                  Size  Used by
binfmt_misc             7960  1 
rfcomm                 40329  4 
ppdev                   6375  0 
sco                     9617  2 
bridge                 53152  0 
stp                     2171  1 bridge
bnep                   11820  2 
l2cap                  34774  16 rfcomm,bnep
vboxnetadp              5235  0 
vboxnetflt             12242  0 
vboxdrv              1768311  2 vboxnetadp,vboxnetflt
snd_hda_codec_conexant    28745  1 
joydev                 11072  0 
iptable_nat             5219  0 
nf_nat                 19501  1 iptable_nat
nf_conntrack_ipv4      12980  3 iptable_nat,nf_nat
nf_conntrack           73934  3 iptable_nat,nf_nat,nf_conntrack_ipv4
nf_defrag_ipv4          1481  1 nf_conntrack_ipv4
iptable_mangle          3315  0 
iptable_filter          2791  0 
lib80211_crypt_tkip     8676  0 
ip_tables              18390  3 iptable_nat,iptable_mangle,iptable_filter
x_tables               22429  2 iptable_nat,ip_tables
fbcon                  39270  71 
tileblit                2487  1 fbcon
font                    8053  1 fbcon
bitblit                 5811  1 fbcon
softcursor              1565  1 bitblit
btusb                  12969  2 
bluetooth              58621  9 rfcomm,sco,bnep,l2cap,btusb
ricoh_mmc               3416  0 
sdhci_pci               6700  0 
sdhci                  17928  1 sdhci_pci
led_class               3732  1 sdhci
snd_hda_intel          25645  2 
snd_hda_codec          85727  2 snd_hda_codec_conexant,snd_hda_intel
snd_hwdep               6924  1 snd_hda_codec
snd_pcm_oss            41394  0 
snd_mixer_oss          16299  1 snd_pcm_oss
snd_pcm                87850  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1782  0 
snd_seq_oss            31219  0 
snd_seq_midi            5829  0 
snd_rawmidi            23388  1 snd_seq_midi
snd_seq_midi_event      7267  2 snd_seq_oss,snd_seq_midi
snd_seq                57417  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23553  2 snd_pcm,snd_seq
snd_seq_device          6824  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    70978  16 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
edac_core              45423  0 
edac_mce_amd            9214  0 
psmouse                64608  0 
serio_raw               4918  0 
k8temp                  3912  0 
soundcore               8052  1 snd
snd_page_alloc          8500  2 snd_hda_intel,snd_pcm
wl                   1964968  0 
lib80211                6119  2 lib80211_crypt_tkip,wl
i2c_nforce2             6099  0 
nvidia              10799466  40 
vga16fb                12757  1 
vgastate                9857  1 vga16fb
video                  20623  0 
output                  2503  1 video
lp                      9336  0 
parport                37160  2 ppdev,lp
ohci1394               30260  0 
ieee1394               94675  1 ohci1394
pata_amd               11962  0 
forcedeth              55592  0 
sata_nv                23778  2 

lspci -nn

01:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11a/b/g [14e4:4312] (rev 01)


Thanks in advance!

---

### Post by ether3al on 2010-06-10
Ok.

So I found the 64bit driver on the broadcom site and have successfully installed it however, when I ifconfig it shows as eth1 instead of wlan0 which also results in me not being able to perform functions such as iwlist scanning...

anyone have a solution to this ?

---

### Post by SlidingHorn on 2010-06-10
The device shows as "works" with ndiswrapper...have you tried that instead of the b43?

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

[http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Broadcom_BCM4310](http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Broadcom_BCM4310)

[ndiswrapper troubleshooting]("http://ubuntuforums.org/showthread.php?t=885847") - if you run into problems

---

### Post by ether3al on 2010-06-10
thanks!!! ill give this a go

---

### Post by ether3al on 2010-06-14
Hi SlidingHorn,

I have tried your link with little success... 

I get the following error:

Jun 15 13:36:09 blah-laptop kernel: [  793.820193] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)
Jun 15 13:36:09 blah-laptop kernel: [  794.096639] usbcore: registered new interface driver ndiswrapper

[Edit]
I restarted my laptop and now do not have any wireless adapters available for use....

The driver file used was: bcmwl5.inf

Anymore suggestions?

Thanks!

---

### Post by ether3al on 2010-06-14
Got it working! 

Just had to move all the files into the correct folder!

---

