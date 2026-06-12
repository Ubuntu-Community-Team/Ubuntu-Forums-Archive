---
title: "Tuner Issue"
date: 2007-05-13
forum: Multimedia &amp; Video
---

### Post by binarykungfu on 2007-05-13
I have not been able to get sound from my tuner card. It's a BT878 chipset. If I plug my speaker into the audio out on the tuner I get audio. I have a cable running from the audio out on the tuner to the input on my sound card. I have searched and researched the forums and tried several different things. I'm running TvTime  and I have video. I'm sure its something simple. Thanks.

$ lsmod
Module                  Size  Used by
btaudio                17552  0 
binfmt_misc            12680  1 
rfcomm                 40856  0 
l2cap                  25728  5 rfcomm
bluetooth              55908  4 rfcomm,l2cap
ppdev                  10116  0 
acpi_cpufreq           10056  0 
cpufreq_stats           7360  0 
cpufreq_ondemand        9228  2 
freq_table              5792  3 acpi_cpufreq,cpufreq_stats,cpufreq_ondemand
cpufreq_powersave       2688  0 
cpufreq_userspace       5408  0 
cpufreq_conservative     8200  0 
pcc_acpi               13184  0 
sony_acpi               6284  0 
tc1100_wmi              8068  0 
dev_acpi               12292  0 
video                  16388  0 
container               5248  0 
dock                   10268  0 
button                  8720  0 
battery                10756  0 
ac                      6020  0 
sbs                    15652  0 
i2c_ec                  5888  1 sbs
asus_acpi              17308  0 
backlight               7040  1 asus_acpi
ipv6                  268704  10 
parport_pc             36388  0 
lp                     12452  0 
parport                36936  3 ppdev,parport_pc,lp
fuse                   46612  0 
bt878                  11960  0 
snd_bt87x              16292  0 
snd_hda_intel          21912  5 
snd_hda_codec         205440  1 snd_hda_intel
snd_pcm_oss            44544  0 
snd_mixer_oss          17408  2 snd_pcm_oss
snd_pcm                79876  5 snd_bt87x,snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           4740  0 
snd_seq_oss            32896  0 
snd_seq_midi            9600  0 
snd_rawmidi            25472  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                52592  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
af_packet              23816  2 
snd_timer              23684  3 snd_pcm,snd_seq
snd_seq_device          9100  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
tuner                  61864  0 
tvaudio                24220  0 
nvidia               4713780  32 
bttv                  173684  2 bt878
video_buf              26116  1 bttv
snd                    54020  17 snd_bt87x,snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
pcspkr                  4224  0 
intel_agp              25116  1 
agpgart                35400  2 nvidia,intel_agp
serio_raw               7940  0 
soundcore               8672  3 btaudio,snd
snd_page_alloc         10888  3 snd_bt87x,snd_hda_intel,snd_pcm
ir_common              31236  1 bttv
compat_ioctl32          2304  1 bttv
i2c_algo_bit            8712  1 bttv
btcx_risc               5896  1 bttv
tveeprom               15888  1 bttv
i2c_core               22784  7 i2c_ec,tuner,tvaudio,nvidia,bttv,i2c_algo_bit,tveeprom
videodev               28160  2 bttv
v4l2_common            25216  3 tuner,bttv,videodev
v4l1_compat            15236  1 videodev
psmouse                38920  0 
shpchp                 34324  0 
pci_hotplug            32576  1 shpchp
iTCO_wdt               11812  0 
iTCO_vendor_support     4868  1 iTCO_wdt
evdev                  11008  3 
tsdev                   8768  0 
ext3                  133128  1 
jbd                    59816  1 ext3
mbcache                 9604  1 ext3
sg                     36252  0 
usbhid                 26592  0 
hid                    27392  1 usbhid
sr_mod                 17060  0 
cdrom                  37664  1 sr_mod
sd_mod                 23428  3 
generic                 5124  0 [permanent]
ata_generic             9092  0 
usb_storage            72256  0 
libusual               17936  1 usb_storage
ata_piix               15492  2 
libata                125720  2 ata_generic,ata_piix
scsi_mod              142348  5 sg,sr_mod,sd_mod,usb_storage,libata
e1000                 126016  0 
ehci_hcd               34188  0 
uhci_hcd               25360  0 
usbcore               134280  6 usbhid,usb_storage,libusual,ehci_hcd,uhci_hcd
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

$lspci

04:04.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11)
04:04.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)


$ dmesg | grep bt878
[   14.454771] bttv0: using: Hauppauge (bt878) [card=10,autodetected]
[   14.749032] tuner 0-0061: chip found @ 0xc2 (bt878 #0 [sw])
[   15.381891] bt878: AUDIO driver version 0.0.0 loaded

---

### Post by azdragon on 2007-06-04
Have you tried running a wire from the output of your card to the line in of your sound card, that is the way you do it in Windows so maybe it will work here.

---

### Post by RayVad on 2007-07-22
[http://ubuntuforums.org/showthread.php?t=476263&highlight=tvtime+sound]("http://ubuntuforums.org/showthread.php?t=476263&highlight=tvtime+sound")

---

