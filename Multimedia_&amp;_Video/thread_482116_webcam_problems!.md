---
title: "webcam problems!"
date: 2007-06-23
forum: Multimedia &amp; Video
---

### Post by genefrench on 2007-06-23
> the webcam did work out of the box while i was running 2.6.20-15..
> i then upgraded to 2.6.20-16 AND installed tvtuner...i did both without
> checking inbetween to see if webcam was working...only after i
> installed both...i then got the new driver(gspcav1-20070508) , compiled, and sudo modprobe
> gspca would not load...
> videodev was not loaded...after sudo modprobe videodev...lsmod showed it loaded and associated with v4l2 and v4l1
> gene@acer2_ubuntu:~$ lsmod | grep videodev
> videodev               29312  2 em28xx,zc0301
> v4l2_common            18432  5 tvp5150,tuner,em28xx,zc0301,videodev
> v4l1_compat            15236  2 em28xx,videodev
> but still gspca will not load...error is:
> gene@acer2_ubuntu:~$ sudo modprobe gspca
> FATAL: Error inserting gspca
> (/lib/modules/2.6.20-16-generic/kernel/drivers/usb/media/gspca.ko):
> Unknown symbol in module, or unknown parameter (see dmesg)
>   
gene@acer2_ubuntu:~$ lsusb
> Bus 005 Device 003: ID 2040:6513 Hauppauge 
> Bus 005 Device 001: ID 0000:0000  
> Bus 003 Device 002: ID 041e:4036 Creative Technology, Ltd Webcam Live!/Live! Pro
> Bus 003 Device 001: ID 0000:0000  
> Bus 004 Device 001: ID 0000:0000  
> Bus 002 Device 001: ID 0000:0000  
> Bus 001 Device 001: ID 0000:0000  
>
>   
gene@acer2_ubuntu:~/downloads/creative_live$ lsmod
Module                  Size  Used by
lgdt330x               10244  1
qt1010                  7812  0
mt2060                  6532  0
mt352                   8328  0
zl10353                 7816  0
em2880_dvb             14980  0
dvb_core               82600  2 lgdt330x,em2880_dvb
em28xx_audio            7940  0
xc3028_tuner            9984  2
tvp5150                20752  0
tuner                  68008  0
em28xx                 96180  2 em2880_dvb,em28xx_audio
ir_common              40068  1 em28xx
tveeprom               16784  1 em28xx
zc0301                 48772  0
compat_ioctl32          2304  2 em28xx,zc0301
videodev               29312  2 em28xx,zc0301
v4l2_common            18432  5 tvp5150,tuner,em28xx,zc0301,videodev
v4l1_compat            15236  2 em28xx,videodev
ppp_deflate             6912  0
zlib_deflate           20504  1 ppp_deflate
bsd_comp                7040  0
ppp_async              13184  1
crc_ccitt               3072  1 ppp_async
ppp_generic            29076  7 ppp_deflate,bsd_comp,ppp_async
slhc                    7680  1 ppp_generic
nls_cp437               6784  1
isofs                  36284  1
udf                    85252  0
binfmt_misc            12680  1
rfcomm                 40856  0
l2cap                  25856  5 rfcomm
bluetooth              55908  4 rfcomm,l2cap
ipv6                  268960  12
i915                   24448  2
drm                    81044  3 i915
ppdev                  10116  0
acpi_cpufreq           10056  1
cpufreq_powersave       2688  0
cpufreq_ondemand        9228  1
cpufreq_conservative     8200  0
cpufreq_stats           7360  0
cpufreq_userspace       5408  0
freq_table              5792  3 acpi_cpufreq,cpufreq_ondemand,cpufreq_stats
pcc_acpi               13184  0
sony_acpi               6284  0
tc1100_wmi              8068  0
dev_acpi               12292  0
battery                10756  0
button                  8720  0
video                  16388  0
container               5248  0
dock                   10268  0
sbs                    15652  0
i2c_ec                  6016  1 sbs
i2c_core               22656  11 lgdt330x,qt1010,mt2060,mt352,zl10353,xc3028_tuner,tvp5150,tuner,em28xx,tveeprom,i2c_ec
asus_acpi              17308  0
backlight               7040  1 asus_acpi
ac                      6020  0
af_packet              23816  4
parport_pc             36388  0
lp                     12452  0
parport                36936  3 ppdev,parport_pc,lp
fuse                   46612  0
pcmcia                 39212  0
hsfhda                109224  3
hsfserial              24580  3 hsfhda
hsfengine            1296396  2 hsfhda,hsfserial
hsfosspec             104040  6 hsfhda,hsfserial,hsfengine
joydev                 10816  0
snd_hda_intel          22296  1
snd_hda_codec         233484  2 hsfhda,snd_hda_intel
snd_pcm_oss            44544  0
snd_mixer_oss          17408  1 snd_pcm_oss
serio_raw               7940  0
sdhci                  18700  0
snd_pcm                79876  4 em28xx_audio,snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           4740  0
snd_seq_oss            32896  0
psmouse                38920  0
mmc_core               26756  1 sdhci
yenta_socket           27532  1
rsrc_nonstatic         14080  1 yenta_socket
pcmcia_core            40852  3 pcmcia,yenta_socket,rsrc_nonstatic
iTCO_wdt               11812  0
ipw3945               118816  1
ieee80211              34760  1 ipw3945
ieee80211_crypt         7040  1 ieee80211
snd_seq_midi            9600  0
snd_rawmidi            25472  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                52592  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23684  2 snd_pcm,snd_seq
snd_seq_device          9100  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
iTCO_vendor_support     4868  1 iTCO_wdt
snd                    54020  13 em28xx_audio,snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8672  1 snd
snd_page_alloc         10888  2 snd_hda_intel,snd_pcm
intel_agp              25244  1
agpgart                35400  3 drm,intel_agp
shpchp                 34324  0
pci_hotplug            32576  1 shpchp
tsdev                   8768  0
evdev                  11008  5
ext3                  133128  1
jbd                    59816  1 ext3
mbcache                 9604  1 ext3
sg                     36252  0
sr_mod                 17060  1
cdrom                  37664  1 sr_mod
sd_mod                 23428  3
generic                 5124  0 [permanent]
ata_generic             9092  0
b44                    28044  0
mii                     6528  1 b44
ata_piix               15492  3
libata                125720  2 ata_generic,ata_piix
scsi_mod              142348  4 sg,sr_mod,sd_mod,libata
ehci_hcd               34188  0
uhci_hcd               25360  0
usbcore               134280  8 em2880_dvb,em28xx_audio,em28xx,zc0301,hsfosspec,ehci_hcd,uhci_hcd
thermal                14856  0
processor              31048  2 acpi_cpufreq,thermal
fan                     5636  0
fbcon                  42656  0
tileblit                3584  1 fbcon
font                    9216  1 fbcon
bitblit                 6912  1 fbcon
softcursor              3200  1 bitblit
vesafb                  9220  0
capability              5896  0
commoncap               8192  1 capability

thanks again for your time and help...

gene french

---

