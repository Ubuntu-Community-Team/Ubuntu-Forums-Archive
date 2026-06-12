---
title: "[SOLVED] Hauppauge WinTv -NOVA-TD model 1174"
date: 2008-11-03
forum: Multimedia Software
---

### Post by darksoliton on 2008-11-03
I bought a Hauppauge WinTv-NOVA-TD model 1174 USB with diversity technology (two tuners and two antennas). I have Ubuntu 8.10 64-bits installed and the kernel version I'm using is 2.6.27-7-generic. I installed both xawtv and Mithtv but I didn't menage to let the device work.
```

matteo@univac:~$ xawtv
This is xawtv-3.95.dfsg.1, running on Linux/x86_64 (2.6.27-7-generic)
xinerama 0: 1440x900+0+0
WARNING: No DGA direct video mode for this display.
can't open /dev/video0: No such file or directory
v4l-conf had some trouble, trying to continue anyway
v4l2: open /dev/video0: No such file or directory
v4l2: open /dev/video0: No such file or directory
v4l: open /dev/video0: No such file or directory
no video grabber device available

```
Following the instruction I found here [http://duesenklipper.wordpress.com/2008/06/11/hauppauge-wintv-nova-td-on-ubuntu-804-hardy/]("http://duesenklipper.wordpress.com/2008/06/11/hauppauge-wintv-nova-td-on-ubuntu-804-hardy/") I downloaded the latest v4l drivers and install them. The device seem to be recognized properly, infact:
```

matteo@univac:~$ dmesg | grep dvb
[   12.405346] dvb-usb: found a 'Hauppauge Nova-TD Stick (52009)' in warm state.
[   12.405450] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   12.837212] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   13.173090] dvb-usb: Hauppauge Nova-TD Stick (52009) successfully initialized and connected.
[   13.173406] usbcore: registered new interface driver dvb_usb_dib0700
[   29.523184] Modules linked in: ppdev acpi_cpufreq cpufreq_stats cpufreq_ondemand cpufreq_userspace cpufreq_conservative freq_table cpufreq_powersave sbs video output container sbshc pci_slot battery iptable_filter ip_tables x_tables ac parport_pc lp parport arc4 ecb crypto_blkcipher rt73usb crc_itu_t rt2x00usb rt2x00lib dvb_usb_dib0700 rfkill dib7000p dib7000m led_class dvb_usb dvb_core mac80211 psmouse dib3000mc pcspkr serio_raw dibx000_common dib0070 evdev nvidia(P) cfg80211 i2c_core shpchp pci_hotplug snd_hda_intel wmi snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device snd button soundcore snd_page_alloc ext3 jbd mbcache sr_mod cdrom usb_storage libusual sd_mod crc_t10dif sg pata_amd pata_acpi r8169 ahci ata_generic ehci_hcd libata ohci_hcd scsi_mod dock usbcore thermal processor fan fuse vesafb fbcon tileblit font bitblit softcursor
[   29.523296] Modules linked in: ppdev acpi_cpufreq cpufreq_stats cpufreq_ondemand cpufreq_userspace cpufreq_conservative freq_table cpufreq_powersave sbs video output container sbshc pci_slot battery iptable_filter ip_tables x_tables ac parport_pc lp parport arc4 ecb crypto_blkcipher rt73usb crc_itu_t rt2x00usb rt2x00lib dvb_usb_dib0700 rfkill dib7000p dib7000m led_class dvb_usb dvb_core mac80211 psmouse dib3000mc pcspkr serio_raw dibx000_common dib0070 evdev nvidia(P) cfg80211 i2c_core shpchp pci_hotplug snd_hda_intel wmi snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device snd button soundcore snd_page_alloc ext3 jbd mbcache sr_mod cdrom usb_storage libusual sd_mod crc_t10dif sg pata_amd pata_acpi r8169 ahci ata_generic ehci_hcd libata ohci_hcd scsi_mod dock usbcore thermal processor fan fuse vesafb fbcon tileblit font bitblit softcursor

```
```

matteo@univac:~$ lsusb 
Bus 002 Device 003: ID 2040:5200 Hauppauge 
Bus 002 Device 002: ID 07d1:3c03 D-Link System DWL-G122 802.11g Adapter [ralink rt73]
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 058f:9360 Alcor Micro Corp. 8-in-1 Media Card Reader
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```
```

matteo@univac:~$ lsmod
Module                  Size  Used by
ipv6                  314312  14 
af_packet              29568  4 
binfmt_misc            18700  1 
ppdev                  16904  0 
acpi_cpufreq           16400  1 
cpufreq_stats          14468  0 
cpufreq_ondemand       16400  1 
cpufreq_userspace      12420  0 
cpufreq_conservative    16392  0 
freq_table             13568  3 acpi_cpufreq,cpufreq_stats,cpufreq_ondemand
cpufreq_powersave      10368  0 
sbs                    22288  0 
video                  28948  0 
output                 11776  1 video
container              12288  0 
sbshc                  14592  1 sbs
pci_slot               13704  0 
battery                21128  0 
iptable_filter         11520  0 
ip_tables              28176  1 iptable_filter
x_tables               31752  1 ip_tables
ac                     13448  0 
parport_pc             44200  0 
lp                     19588  0 
parport                50096  3 ppdev,parport_pc,lp
arc4                   10368  2 
ecb                    11520  2 
crypto_blkcipher       27780  1 ecb
rt73usb                32768  0 
crc_itu_t              10496  1 rt73usb
rt2x00usb              20480  1 rt73usb
rt2x00lib              40576  2 rt73usb,rt2x00usb
dvb_usb_dib0700        54408  0 
rfkill                 19364  1 rt2x00lib
dib7000p               26760  3 dvb_usb_dib0700
dib7000m               24068  1 dvb_usb_dib0700
led_class              13192  1 rt2x00lib
dvb_usb                30220  1 dvb_usb_dib0700
dvb_core              110380  1 dvb_usb
mac80211              253440  2 rt2x00usb,rt2x00lib
psmouse                51612  0 
dib3000mc              22408  1 dvb_usb_dib0700
pcspkr                 11136  0 
serio_raw              14596  0 
dibx000_common         12292  3 dib7000p,dib7000m,dib3000mc
dib0070                16644  3 dvb_usb_dib0700
evdev                  20512  6 
nvidia               7804864  36 
cfg80211               37136  2 rt2x00lib,mac80211
i2c_core               36128  8 dvb_usb_dib0700,dib7000p,dib7000m,dvb_usb,dib3000mc,dibx000_common,dib0070,nvidia
shpchp                 42140  0 
pci_hotplug            39472  1 shpchp
snd_hda_intel         489264  1 
wmi                    15808  0 
snd_pcm_oss            52608  0 
snd_mixer_oss          25088  1 snd_pcm_oss
snd_pcm                99208  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          11524  0 
snd_seq_oss            42368  0 
snd_seq_midi           15872  0 
snd_rawmidi            34176  1 snd_seq_midi
snd_seq_midi_event     16768  2 snd_seq_oss,snd_seq_midi
snd_seq                67168  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              34320  2 snd_pcm,snd_seq
snd_seq_device         16404  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    79432  11 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
button                 15904  0 
soundcore              16800  1 snd
snd_page_alloc         17680  2 snd_hda_intel,snd_pcm
ext3                  150544  1 
jbd                    66472  1 ext3
mbcache                17924  1 ext3
sr_mod                 24644  0 
cdrom                  47784  1 sr_mod
usb_storage            92864  0 
libusual               31784  1 usb_storage
sd_mod                 45864  3 
crc_t10dif             10240  1 sd_mod
sg                     45408  0 
pata_amd               22020  0 
pata_acpi              13568  0 
r8169                  40196  0 
ahci                   43148  2 
ata_generic            14212  0 
ehci_hcd               48908  0 
libata                200160  4 pata_amd,pata_acpi,ahci,ata_generic
ohci_hcd               34972  0 
scsi_mod              183160  5 sr_mod,usb_storage,sd_mod,sg,libata
dock                   18464  1 libata
usbcore               175376  9 rt73usb,rt2x00usb,dvb_usb_dib0700,dvb_usb,usb_storage,libusual,ehci_hcd,ohci_hcd
thermal                27424  0 
processor              47800  2 acpi_cpufreq,thermal
fan                    13576  0 
fuse                   68288  1 
vesafb                 15240  1 
fbcon                  51200  72 
tileblit               11264  1 fbcon
font                   17152  1 fbcon
bitblit                14592  1 fbcon
softcursor             10496  1 bitblit

```
In /dev there are two new devices:
```

matteo@univac:~$ ls /dev/dvb
adapter0  adapter1

```
which should correspond to the two tuners.
Does somebody have an idea about what is going on? Is this card supported by the v4l driver? Is there something I'm missing? Within a couple of day I could try to bring the card back to the seller and get another card (if he has an other one linux compatible...). Anyway before surrendering I would like to try again. Any suggestions?

---

### Post by darksoliton on 2008-11-03
Well...
I installed Me-Tv package and... That's it. The device works perfectly. The antenna I have at the moment is not really the best, but anyway the channels I'm able to connect with are working perfectly. I saw that during me-tv installation other packages were installed:
```

dvb-utils (1.1.1-3)
libgnet2.0-0 (2.0.8-1)
me-tv (0.5.30-1)

```
probably dvb-utils was the missing package...

---

