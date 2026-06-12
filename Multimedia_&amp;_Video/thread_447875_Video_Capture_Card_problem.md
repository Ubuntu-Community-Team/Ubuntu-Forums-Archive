---
title: "Video Capture Card problem"
date: 2007-05-18
forum: Multimedia &amp; Video
---

### Post by chilidawg87 on 2007-05-18
Hi all,

I'm setting up mythTV. So i am going through all the tutorials i can get my hands on an cannot solve the problem. Here it is:

I went through this guide:
[http://parker1.co.uk/mythtv_ubuntu.php](http://parker1.co.uk/mythtv_ubuntu.php)

Where i started having problems was at the 
```

scan /usr/share/doc/dvb-utils/examples/scan/dvb-t/uk-WinterHill > /root/.tzap/channels.conf
```
step.

Here is my errors
```

scan /usr/share/doc/dvb-utils/examples/scan/atsc/us-NTSC-center-frequencies-8VSB > /root/.tzap/channels.conf
scanning /usr/share/doc/dvb-utils/examples/scan/atsc/us-NTSC-center-frequencies-8VSB
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
main:2247: FATAL: failed to open '/dev/dvb/adapter0/frontend0': 2 No such file or directory
```


I feel like i have tried everything. Please give me some guidance

---

### Post by newlinux on 2007-05-18
Can you give us a little more info? What distribution of Ubuntu? What tuner card are you using? What did you do to set it up?

Also,

I strongly recommend using the tutorials here instead:
[https://help.ubuntu.com/community/MythTV](https://help.ubuntu.com/community/MythTV)

---

### Post by chilidawg87 on 2007-05-18
> **newlinux said:**
> Can you give us a little more info? What distribution of Ubuntu? What tuner card are you using? What did you do to set it up?

Also,

I strongly recommend using the tutorials here instead:
[https://help.ubuntu.com/community/MythTV](https://help.ubuntu.com/community/MythTV)


sure! Feisty, my ```
 lspci
``` gives me ```
03:0b.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11)
03:0b.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)

```

to set it up i went through the toutorial that i listed and i also went through the one you suggested. I feel once i resolve the problem i am getting here the actual mythTV problems will be easier to fix. 

So as of now i am trying to fix the DVBstream problems fixed.

---

### Post by fenian on 2007-05-18
It seems as though you don't have DVB drivers set up for your tuner , more info on doing this can be found [here.]("http://www.linuxtv.org/wiki/index.php/How_to_install_DVB_device_drivers")

---

### Post by newlinux on 2007-05-18
What is the brand and model of the card? Also, what does lsmod produce?

---

### Post by chilidawg87 on 2007-05-19
My lsmod:

```
Module                  Size  Used by
binfmt_misc            12680  1 
rfcomm                 40856  0 
hci_usb                18204  0 
l2cap                  25728  5 rfcomm
bluetooth              55908  5 rfcomm,hci_usb,l2cap
vmnet                  39076  9 
vmmon                 113420  0 
ppdev                  10116  0 
i915                   24448  3 
drm                    81044  4 i915
speedstep_lib           6148  0 
cpufreq_userspace       5408  0 
cpufreq_stats           7360  0 
cpufreq_powersave       2688  0 
cpufreq_ondemand        9228  0 
freq_table              5792  2 cpufreq_stats,cpufreq_ondemand
cpufreq_conservative     8200  0 
tc1100_wmi              8068  0 
pcc_acpi               13184  0 
dev_acpi               12292  0 
sony_acpi               6284  0 
video                  16388  0 
sbs                    15652  0 
i2c_ec                  5888  1 sbs
dock                   10268  0 
button                  8720  0 
battery                10756  0 
container               5248  0 
ac                      6020  0 
asus_acpi              17308  0 
backlight               7040  1 asus_acpi
ipv6                  268704  14 
vfat                   14208  0 
fat                    53916  1 vfat
fuse                   46612  1 
lp                     12452  0 
bt878                  11960  0 
snd_bt87x              16804  0 
snd_intel8x0           35228  1 
snd_ac97_codec        100260  1 snd_intel8x0
ac97_bus                3456  1 snd_ac97_codec
snd_pcm_oss            44672  0 
snd_mixer_oss          17792  1 snd_pcm_oss
tuner                  65320  0 
tvaudio                24348  0 
bttv                  179508  1 bt878
video_buf              26116  1 bttv
ir_common              35460  1 bttv
compat_ioctl32          2304  1 bttv
btcx_risc               5896  1 bttv
tveeprom               16784  1 bttv
videodev               29312  1 bttv
v4l2_common            18432  4 tuner,tvaudio,bttv,videodev
v4l1_compat            15236  2 bttv,videodev
snd_seq_dummy           4996  0 
snd_seq_oss            35200  0 
snd_seq_midi            9728  0 
snd_rawmidi            25984  1 snd_seq_midi
snd_seq_midi_event      8576  2 snd_seq_oss,snd_seq_midi
snd_seq                54128  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd_pcm                81028  4 snd_bt87x,snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              24196  2 snd_seq,snd_pcm
parport_pc             36388  1 
parport                36936  3 ppdev,lp,parport_pc
psmouse                38920  0 
serio_raw               7940  0 
pcspkr                  4224  0 
i2c_i810                6276  0 
snd                    56324  14 snd_bt87x,snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_seq_device,snd_pcm,snd_timer
soundcore               8672  1 snd
snd_page_alloc         11272  3 snd_bt87x,snd_intel8x0,snd_pcm
i2c_algo_bit            8712  2 bttv,i2c_i810
intel_agp              25116  1 
agpgart                35400  3 drm,intel_agp
iTCO_wdt               11812  0 
iTCO_vendor_support     4868  1 iTCO_wdt
shpchp                 34324  0 
pci_hotplug            32576  1 shpchp
i2c_core               22784  7 i2c_ec,tuner,tvaudio,bttv,tveeprom,i2c_i810,i2c_algo_bit
af_packet              23816  2 
joydev                 10816  0 
tsdev                   8768  0 
evdev                  11008  4 
usbhid                 26592  0 
hid                    27392  1 usbhid
ext3                  133128  1 
jbd                    59816  1 ext3
mbcache                 9604  1 ext3
sg                     36252  0 
sr_mod                 17060  0 
cdrom                  37664  1 sr_mod
sd_mod                 23428  3 
ata_piix               15492  2 
ata_generic             9092  0 
libata                125720  2 ata_piix,ata_generic
scsi_mod              142348  4 sg,sr_mod,sd_mod,libata
floppy                 59524  0 
b44                    28044  0 
mii                     6528  1 b44
generic                 5124  0 [permanent]
ehci_hcd               34188  0 
uhci_hcd               25360  0 
usbcore               134280  5 hci_usb,usbhid,ehci_hcd,uhci_hcd
thermal                14856  0 
processor              31048  1 thermal
fan                     5636  0 
fbcon                  42656  0 
tileblit                3584  1 fbcon
font                    9216  1 fbcon
bitblit                 6912  1 fbcon
softcursor              3200  1 bitblit
vesafb                  9220  0 
capability              5896  0 
commoncap               8192  1 capability

```

---

### Post by chilidawg87 on 2007-05-19
Here is my card:

[http://hauppage.com/pages/products/data_goplus.html](http://hauppage.com/pages/products/data_goplus.html)

---

### Post by chilidawg87 on 2007-05-19
> **fenian said:**
> It seems as though you don't have DVB drivers set up for your tuner , more info on doing this can be found [here.]("http://www.linuxtv.org/wiki/index.php/How_to_install_DVB_device_drivers")

well i checked out that site before i posted here. Maybe its just me but i had trouble making heads or tails out of it. I tried installing the correct drivers and i feel like they are installed because i went through this: 

[http://www.mythtv.org/wiki/index.php?title=Hauppauge_WinTV-Go&printable=yes](http://www.mythtv.org/wiki/index.php?title=Hauppauge_WinTV-Go&printable=yes)

sorry... i know i am a pain.

---

### Post by fenian on 2007-05-19
The WinTV Go card is an analog card not a DVB card. I have used this card in a Ubuntu/Mythtv setup and I know it works without any card specific setup.To check that the card is in fact working use TVTime.To get the channel program data to load in Mythtv you need to install and setup [xmltv]("http://www.mythtv.org/wiki/index.php/Uk_xmltv")(link and instructions below are for theUK)...

sudo apt-get install xmltv-util
tv_grab_dk --configure tv_grab_uk_rt

---

