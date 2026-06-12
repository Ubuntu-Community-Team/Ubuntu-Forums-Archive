---
title: "toshiba a215 atheros ar242x intrepid connection issues"
date: 2009-11-11
forum: Networking &amp; Wireless
---

### Post by jab06y on 2009-11-11
I have run into quite the problem getting my wifi to work on this laptop. Im using the mobo atheros ar242x with madwifi release 2.6. The wireless networks show up but the connection just stalls, always returning to the key input screen. Here is a print out of my iwconfig -

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"linksys"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

*Here is the printout from *lspci | grep Wireless
0e:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

Lastly here is a printout from lsmod
ipv6                  264356  10 
af_packet              25856  4 
binfmt_misc            16904  1 
radeon                147616  2 
drm                    86056  3 radeon
rfcomm                 44432  0 
bridge                 56980  0 
stp                    10628  1 bridge
bnep                   20352  2 
sco                    18308  2 
l2cap                  30464  6 rfcomm,bnep
bluetooth              62180  6 rfcomm,bnep,sco,l2cap
ppdev                  15748  0 
cpufreq_stats          13188  0 
cpufreq_conservative    14600  0 
cpufreq_powersave       9856  0 
cpufreq_ondemand       14988  0 
freq_table             12672  2 cpufreq_stats,cpufreq_ondemand
cpufreq_userspace      11396  0 
iptable_filter         10752  0 
ip_tables              19600  1 iptable_filter
x_tables               22916  1 ip_tables
sbp2                   29324  0 
parport_pc             39332  0 
lp                     17156  0 
parport                42604  3 ppdev,parport_pc,lp
joydev                 18368  0 
snd_hda_intel         385072  3 
snd_pcm_oss            46848  0 
snd_mixer_oss          22784  1 snd_pcm_oss
snd_pcm                83204  2 snd_hda_intel,snd_pcm_oss
arc4                    9984  2 
snd_seq_dummy          10884  0 
ecb                    10880  2 
crypto_blkcipher       25476  1 ecb
snd_seq_oss            38528  0 
psmouse                45200  0 
evdev                  17696  4 
snd_seq_midi           14336  0 
snd_rawmidi            29824  1 snd_seq_midi
serio_raw              13444  0 
ath5k                 116868  0 
pcspkr                 10624  0 
k8temp                 12416  0 
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi
snd_seq                57776  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
sdhci_pci              15360  0 
sdhci                  24068  1 sdhci_pci
mac80211              213808  1 ath5k
snd_timer              29960  2 snd_pcm,snd_seq
led_class              12164  1 ath5k
snd_seq_device         15116  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
mmc_core               58396  1 sdhci
cfg80211               43544  2 ath5k,mac80211
i2c_piix4              16144  0 
ati_agp                14988  0 
agpgart                42184  2 drm,ati_agp
i2c_core               31892  1 i2c_piix4
snd                    63396  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15328  1 snd
snd_page_alloc         16136  2 snd_hda_intel,snd_pcm
shpchp                 38036  0 
pci_hotplug            34976  1 shpchp
ext3                  133384  1 
jbd                    55956  1 ext3
mbcache                16004  1 ext3
sr_mod                 22212  0 
cdrom                  43168  1 sr_mod
sd_mod                 42392  3 
crc_t10dif              9984  1 sd_mod
pata_atiixp            12800  0 
ata_generic            12932  0 
sg                     39732  0 
pata_acpi              12160  0 
ehci_hcd               43788  0 
ohci_hcd               32016  0 
ahci                   37132  2 
ohci1394               37936  0 
libata                178336  4 pata_atiixp,ata_generic,pata_acpi,ahci
scsi_mod              155468  5 sbp2,sr_mod,sd_mod,sg,libata
ieee1394               96324  2 sbp2,ohci1394
usbcore               149616  3 ehci_hcd,ohci_hcd
dock                   16656  1 libata
r8169                  37764  0 
mii                    13440  1 r8169
fbcon                  47648  0 
tileblit               10880  1 fbcon
font                   16512  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
fuse                   60956  3 

Thank you in advance for any help you can provide. I love linux and really hate to see this not work. The wireless works fine in jaunty (though the ati is worthless in jaunty) and karmic has no support at all for anything i need. I have hardy but have yet to install it, have been somewhat hesitant after reading the forums.

---

### Post by jab06y on 2009-11-11
Disregard the previous post. I'm reluctantly giving karmic another shot. Heard that might do what i need it to.

---

