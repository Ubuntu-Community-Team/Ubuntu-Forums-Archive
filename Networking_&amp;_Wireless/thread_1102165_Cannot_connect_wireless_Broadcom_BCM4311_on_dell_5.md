---
title: "Cannot connect wireless Broadcom BCM4311 on dell 5100 laptop Ubuntu 8.1"
date: 2009-03-21
forum: Networking &amp; Wireless
---

### Post by dphil6236 on 2009-03-21
Hi,
Having problems connecting with newly installed bcm4311 card. Have searched forums for a while and tried various solutions, nothing seems to get me going. Network connection gives me option for wlan0:avahi, but when I select it says it's disconnected. Hardware drivers only lists Broadcom 43 wireless driver and says it's activated and currently in use. Here's some info on my setup

Thanks

Dell Inspiron 5100
Ubuntu 8.10
don@don-laptop:~$ uname -mr
2.6.27-11-generic i686


02:02.0 Network controller: Broadcom Corporation BCM4311 [AirForce 54g] 802.11a/b/g PCI Express Transceiver (rev 02)

don@don-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

don@don-laptop:~$ lsmod
Module                  Size  Used by
xt_limit               10372  8 
xt_tcpudp              11008  7 
ipt_LOG                13700  8 
ipt_MASQUERADE         10752  0 
xt_DSCP                11264  0 
ipt_REJECT             11136  1 
nf_conntrack_irc       13348  0 
nf_conntrack_ftp       15652  0 
xt_state               10112  6 
ipv6                  263972  8 
af_packet              25728  8 
rfkill_input           12672  0 
binfmt_misc            16904  1 
radeon                147616  2 
drm                    86056  3 radeon
rfcomm                 44432  0 
bridge                 56980  0 
stp                    10628  1 bridge
bnep                   20480  2 
sco                    18308  2 
l2cap                  30464  6 rfcomm,bnep
bluetooth              61924  6 rfcomm,bnep,sco,l2cap
ppdev                  15620  0 
speedstep_lib          12676  0 
cpufreq_conservative    14600  0 
cpufreq_ondemand       14988  0 
cpufreq_userspace      11396  0 
cpufreq_powersave       9856  0 
cpufreq_stats          13188  0 
freq_table             12672  2 cpufreq_ondemand,cpufreq_stats
sbs                    19464  0 
sbshc                  13440  1 sbs
container              11520  0 
wmi                    14504  0 
pci_slot               12680  0 
sbp2                   29324  0 
parport_pc             39204  0 
lp                     17156  0 
parport                42604  3 ppdev,parport_pc,lp
joydev                 18368  0 
pcmcia                 43052  0 
snd_intel8x0           37532  3 
snd_ac97_codec        111652  1 snd_intel8x0
ac97_bus                9856  1 snd_ac97_codec
snd_pcm_oss            46848  0 
snd_mixer_oss          22784  1 snd_pcm_oss
snd_pcm                83204  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy          10884  0 
dcdbas                 15008  0 
snd_seq_oss            38528  0 
snd_seq_midi           14336  0 
snd_rawmidi            29824  1 snd_seq_midi
serio_raw              13444  0 
pcspkr                 10624  0 
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi
psmouse                45200  0 
snd_seq                57776  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
arc4                    9984  2 
ecb                    10880  2 
crypto_blkcipher       25476  1 ecb
snd_timer              29960  2 snd_pcm,snd_seq
snd_seq_device         15116  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    63268  16 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
evdev                  17696  15 
soundcore              15328  1 snd
snd_page_alloc         16136  2 snd_intel8x0,snd_pcm
b43                   131356  0 
rfkill                 17176  3 rfkill_input,b43
mac80211              216820  1 b43
cfg80211               32392  1 mac80211
led_class              12164  1 b43
input_polldev          11912  1 b43
video                  25232  0 
output                 11008  1 video
yenta_socket           31756  1 
rsrc_nonstatic         19072  1 yenta_socket
pcmcia_core            43412  3 pcmcia,yenta_socket,rsrc_nonstatic
iTCO_wdt               18596  0 
iTCO_vendor_support    11652  1 iTCO_wdt
button                 14224  0 
battery                18436  0 
ac                     12292  0 
shpchp                 38036  0 
pci_hotplug            34976  1 shpchp
intel_agp              33724  1 
agpgart                42184  2 drm,intel_agp
iptable_nat            13448  0 
nf_nat                 25368  2 ipt_MASQUERADE,iptable_nat
nf_conntrack_ipv4      21900  9 iptable_nat,nf_nat
nf_conntrack           72032  7 ipt_MASQUERADE,nf_conntrack_irc,nf_conntrack_ftp,xt_state,iptable_nat,nf_nat,nf_conntrack_ipv4
iptable_mangle         10880  0 
iptable_filter         10752  1 
ip_tables              19600  3 iptable_nat,iptable_mangle,iptable_filter
x_tables               22916  9 xt_limit,xt_tcpudp,ipt_LOG,ipt_MASQUERADE,xt_DSCP,ipt_REJECT,xt_state,iptable_nat,ip_tables
ext3                  133256  1 
jbd                    55828  1 ext3
mbcache                16004  1 ext3
usb_storage            82752  0 
libusual               30356  1 usb_storage
usbhid                 35840  0 
hid                    50560  1 usbhid
sd_mod                 42392  3 
crc_t10dif              9984  1 sd_mod
sr_mod                 22212  0 
cdrom                  43168  1 sr_mod
sg                     39732  0 
ata_piix               24580  2 
ata_generic            12932  0 
b44                    35984  0 
pata_acpi              12160  0 
ohci1394               37936  0 
libata                178208  3 ata_piix,ata_generic,pata_acpi
ieee1394               96324  2 sbp2,ohci1394
scsi_mod              155212  6 sbp2,usb_storage,sd_mod,sr_mod,sg,libata
ssb                    40580  2 b43,b44
uhci_hcd               30736  0 
mii                    13440  1 b44
ehci_hcd               43788  0 
dock                   16656  1 libata
usbcore               149360  6 usb_storage,libusual,usbhid,uhci_hcd,ehci_hcd
thermal                23708  0 
processor              42156  1 thermal
fan                    12548  0 
fbcon                  47648  0 
tileblit               10880  1 fbcon
font                   16512  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
fuse                   60828  3 

don@don-laptop:~$ sudo lshw -C network
[sudo] password for don: 
  *-network:0             
       description: Ethernet interface
       product: BCM4401 100Base-T
       vendor: Broadcom Corporation
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 01
       serial: 00:0d:56:b3:21:ae
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=192.168.1.3 latency=32 link=yes module=ssb multicast=yes port=twisted pair speed=100MB/s
  *-network:1
       description: Network controller
       product: BCM4311 [AirForce 54g] 802.11a/b/g PCI Express Transceiver
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:02:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=32 module=ssb
  *-network:0
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:14:a5:4a:8e:4f
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 3
       logical name: pan0
       serial: 46:67:6f:11:4b:b8
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

don@don-laptop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     No scan results

pan0      Interface doesn't support scanning.

---

