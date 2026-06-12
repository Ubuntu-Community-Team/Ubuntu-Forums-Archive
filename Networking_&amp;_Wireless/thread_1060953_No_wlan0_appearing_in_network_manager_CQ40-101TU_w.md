---
title: "No wlan0 appearing in network manager CQ40-101TU with  BCM4312"
date: 2009-02-05
forum: Networking &amp; Wireless
---

### Post by SGMW on 2009-02-05
I would be very grateful of some help.  

I have been fighting to get wireless networking going on my HP CQ40-101TU with Broadcom BCM4312 for a couple of weeks.  I have read at least 10 sets of instructions on the topic and keep ending with the same results.  I am running 8.10 and have attempted to use the native drivers. the STA drivers and the ndiswrapper with the same results.  I can get the drivers and associations appearing in the command line queries but not in network manager.

Thanks very much.

Here is my current config:

lshw - C network

  *-network               
       description: Wireless interface
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 01
       serial: 00:21:00:45:92:73
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.53+Broadcom,03/21/2008, 4.170. latency=0 module=ndiswrapper multicast=yes wireless


iwconfig

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

lspci

03:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)


uname -mr

2.6.27-11-generic i686


lsmod

Module                  Size  Used by
btusb                  19736  0 
ipv6                  263972  14 
af_packet              25728  4 
i915                   38528  2 
drm                    86056  3 i915
binfmt_misc            16904  1 
rfcomm                 44432  2 
bridge                 56980  0 
stp                    10628  1 bridge
bnep                   20480  2 
sco                    18308  2 
l2cap                  30464  12 rfcomm,bnep
bluetooth              61924  9 btusb,rfcomm,bnep,sco,l2cap
b44                    35984  0 
ssb                    40580  1 b44
ndiswrapper           196380  0 
ppdev                  15620  0 
acpi_cpufreq           15500  1 
cpufreq_stats          13188  0 
cpufreq_conservative    14600  0 
cpufreq_powersave       9856  0 
cpufreq_userspace      11396  0 
cpufreq_ondemand       14988  1 
freq_table             12672  3 acpi_cpufreq,cpufreq_stats,cpufreq_ondemand
sbs                    19464  0 
container              11520  0 
pci_slot               12680  0 
sbshc                  13440  1 sbs
iptable_filter         10752  0 
ip_tables              19600  1 iptable_filter
x_tables               22916  1 ip_tables
parport_pc             39204  0 
lp                     17156  0 
parport                42604  3 ppdev,parport_pc,lp
joydev                 18368  0 
psmouse                45200  0 
uvcvideo               63624  0 
serio_raw              13444  0 
compat_ioctl32          9344  1 uvcvideo
videodev               41344  1 uvcvideo
evdev                  17696  13 
pcspkr                 10624  0 
snd_hda_intel         384176  3 
v4l1_compat            22404  2 uvcvideo,videodev
snd_pcm_oss            46848  0 
snd_mixer_oss          22784  1 snd_pcm_oss
snd_pcm                83204  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          10884  0 
snd_seq_oss            38528  0 
sdhci_pci              15360  0 
sdhci                  23940  1 sdhci_pci
snd_seq_midi           14336  0 
snd_rawmidi            29824  1 snd_seq_midi
mmc_core               58268  1 sdhci
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi
snd_seq                57776  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29960  2 snd_pcm,snd_seq
snd_seq_device         15116  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    63268  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
video                  25232  0 
output                 11008  1 video
ac                     12292  0 
soundcore              15328  1 snd
battery                18436  0 
wmi                    14504  0 
intel_agp              33724  1 
button                 14224  0 
snd_page_alloc         16136  2 snd_hda_intel,snd_pcm
agpgart                42184  3 drm,intel_agp
shpchp                 38036  0 
pci_hotplug            34976  1 shpchp
ext3                  133256  1 
jbd                    55828  1 ext3
mbcache                16004  1 ext3
sd_mod                 42392  3 
sr_mod                 22212  0 
crc_t10dif              9984  1 sd_mod
cdrom                  43168  1 sr_mod
sg                     39732  0 
usbhid                 35840  0 
hid                    50560  1 usbhid
ahci                   37132  2 
libata                178208  1 ahci
scsi_mod              155212  4 sd_mod,sr_mod,sg,libata
dock                   16656  1 libata
r8169                  36100  0 
mii                    13440  2 b44,r8169
ehci_hcd               43788  0 
uhci_hcd               30736  0 
usbcore               149360  7 btusb,ndiswrapper,uvcvideo,usbhid,ehci_hcd,uhci_hcd
thermal                23708  0 
processor              42156  4 acpi_cpufreq,thermal
fan                    12548  0 
fbcon                  47648  0 
tileblit               10880  1 fbcon
font                   16512  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
fuse                   60828  3

---

### Post by Ayuthia on 2009-02-05
Are you saying that you are able to see wireless sites from the command line, but not from Network Manager?

---

### Post by SGMW on 2009-02-05
Sorry I wasn't clear about that, I cannot see wireless networks in either the command line or using network manager.

---

