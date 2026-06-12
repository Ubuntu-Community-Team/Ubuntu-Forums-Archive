---
title: "Madwifi problem"
date: 2006-05-18
forum: Networking &amp; Wireless
---

### Post by mhmh2 on 2006-05-18
Hi, i am a new Breezy ubuntu user, i am having trouble getting my madwifi card to work on my new compiled kernel (2.6.16), which i downloaded the source for from kernel.com,then i downloaded a snapshot of madwifi current driver (revision 1529 at 2006-04-2). and it compiled flawlessly in my new kernel after changing the (COPTS+=-Werror) to (COPTS+=).
however, when i try to associate with a certain access point the way i used to do it with my old breezy kernel 2.6.12, by setting the ip address and wep key it doesnt work.

New kernel iwconfig

ath0      IEEE 802.11g  ESSID:"my ssid"  
          Mode:Managed  Frequency:2.442 GHz  Access Point: 00:00:00:00:00:00   
          Bit Rate:1 Mb/s   Tx-Power:16 dBm   Sensitivity=0/3  
          Retry: off   RTS thr: off   Fragment thr: off
          Encryption key:1234-1234-1234-1234-1234-1234-12 [2]   Security mode:restricted
          Power Management: off
          Link Quality=32/94  Signal level=-63 dBm  Noise level=-95 dBm
          Rx invalid nwid:170  Rx invalid crypt: 0  Rx invalid frag: 0
          Tx excessive retries: 0  Invalid misc: 0   Missed beacon: 0

Old kernel iwconfig

ath0      IEEE 802.11g  ESSID:"my ssid"  
          Mode:Managed  Frequency:2.442 GHz  Access Point: 00:11:95:05:80:B0   
          Bit Rate:2 Mb/s   Tx-Power:18 dBm   Sensitivity=0/3  
          Retry: off   RTS thr: off   Fragment thr: off
          Encryption key:1234-1234-1234-1234-1234-1234-12 [2]   Security mode:restricted
          Power Management: off
          Link Quality=31/94  Signal level=-64 dBm  Noise level=-95 dBm
          Rx invalid nwid: 0  Rx invalid crypt: 0  Rx invalid frag: 0
          Tx excessive retries:9  Invalid misc:9   Missed beacon: 0

ie my new kernel only sets the ssid, and does not select the AP. when i set the ap manually (iwconfig ath0 ap 00:11:95:05:80:B0) it sets the access point in addition to ssid, but still not a single packet sent or received.

my modprobe (new kernel ofcourse)

filename:       /lib/modules/2.6.16/net/ath_pci.ko
license:        Dual BSD/GPL
version:        svn 1529
description:    Support for Atheros 802.11 wireless LAN cards.
author:         Errno Consulting, Sam Leffler
srcversion:     18F3FF2121B2F45B58854F4
alias:          pci:v0000168Cd0000001Dsv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000001Csv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000001Bsv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000001Asv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000019sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000018sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000017sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000016sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000015sv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000101Asv*sd*bc*sc*i*
alias:          pci:v0000168Cd00001014sv*sd*bc*sc*i*
alias:          pci:v000010B7d00000013sv*sd*bc*sc*i*
alias:          pci:v0000A727d00000013sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000013sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000012sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000007sv*sd*bc*sc*i*
depends:        ath_hal,ath_rate_sample,wlan
vermagic:       2.6.16 386 gcc-4.0
parm:           countrycode:Override default country code (int)
parm:           outdoor:Enable/disable outdoor use (int)
parm:           xchanmode:Enable/disable extended channel mode (int)
parm:           rfkill:Enable/disable RFKILL capability (int)
parm:           autocreate:Create ath device in [sta|ap|wds|adhoc|ahdemo|monitor] mode. defaults to sta, use 'none' to disable (charp)
parm:           ath_debug:Load-time debug output enable (int)


my lsmod

Module                  Size  Used by
speedstep_lib           4612  0 
cpufreq_userspace       3988  0 
cpufreq_stats           4740  0 
freq_table              4484  1 cpufreq_stats
cpufreq_powersave       1920  0 
cpufreq_ondemand        5788  0 
cpufreq_conservative     6564  0 
video                  15236  0 
container               4480  0 
button                  6672  0 
battery                 9476  0 
ac                      4868  0 
analog                 10016  0 
gameport               13576  1 analog
floppy                 55852  0 
pcspkr                  3204  0 
rtc                    11572  0 
b2c2_flexcop_pci        8088  0 
b2c2_flexcop           24716  1 b2c2_flexcop_pci
mt352                   5892  1 b2c2_flexcop
mt312                   7172  1 b2c2_flexcop
bcm3510                 8836  1 b2c2_flexcop
stv0299                 9864  1 b2c2_flexcop
dvb_core               70336  2 b2c2_flexcop,stv0299
stv0297                 6912  1 b2c2_flexcop
nxt200x                11908  1 b2c2_flexcop
firmware_class          9728  3 b2c2_flexcop,bcm3510,nxt200x
dvb_pll                11396  2 b2c2_flexcop,nxt200x
lgdt330x                7324  1 b2c2_flexcop
i2c_core               19600  8 b2c2_flexcop,mt352,mt312,bcm3510,stv0299,stv0297,nxt200x,lgdt330x
wlan_scan_sta          11648  0 
ath_pci                80676  0 
ath_rate_sample        10880  1 ath_pci
wlan                  165084  4 wlan_scan_sta,ath_pci,ath_rate_sample
ath_hal               188752  3 ath_pci,ath_rate_sample
snd_intel8x0           29596  1 
snd_ac97_codec         82848  1 snd_intel8x0
snd_ac97_bus            2304  1 snd_ac97_codec
snd_pcm_oss            44064  0 
snd_mixer_oss          15104  1 snd_pcm_oss
snd_pcm                74120  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              20484  1 snd_pcm
snd                    45056  8 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               8928  1 snd
snd_page_alloc         10120  2 snd_intel8x0,snd_pcm
shpchp                 39232  0 
pci_hotplug            24116  1 shpchp
intel_agp              21148  1 
agpgart                29532  1 intel_agp
nls_iso8859_1           4224  3 
nls_cp437               5888  3 
vfat                   11520  3 
fat                    46876  1 vfat
tsdev                   7488  0 
dm_mod                 46644  0 
psmouse                34568  0 
mousedev               10688  1 
parport_pc             31728  1 
lp                     10688  0 
parport                31944  2 parport_pc,lp
md_mod                 64404  0 
ext3                  115720  1 
jbd                    46740  1 ext3
thermal                13192  0 
processor              21696  1 thermal
fan                     4740  0 
e100                   31876  0 
mii                     5376  1 e100
uhci_hcd               27152  0 
usbcore               109984  2 uhci_hcd
ide_cd                 35616  0 
cdrom                  32304  1 ide_cd
ide_disk               14848  6 
ide_generic             1408  0 [permanent]
piix                    9220  0 [permanent]
generic                 4484  0 [permanent]
ide_core              111152  5 ide_cd,ide_disk,ide_generic,piix,generic
unix                   24240  630

thanks in advance

---

### Post by mhmh2 on 2006-05-19
anyone pls

---

