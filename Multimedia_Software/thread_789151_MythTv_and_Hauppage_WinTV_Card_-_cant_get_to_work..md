---
title: "MythTv and Hauppage WinTV Card - cant get to work..."
date: 2008-05-10
forum: Multimedia Software
---

### Post by hatman on 2008-05-10
Been trying (unsuccesfully) since Dapper to get my TV card working in Ubuntu, never had any joy... thought I'd try again, downed/installed MythTV, ran the backend setup but still cant get the tv card working, even though a lspci recognises it... Googled, and followed instuctions [here](http://parker1.co.uk/mythtv_ubuntu.php) but MythTV still dont work with the card - has a Failed to Open message...

Output from lspci
> 00:00.0 Host bridge: Silicon Integrated Systems [SiS] SiS645 Host & Memory & AGP Controller (rev 02)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] Virtual PCI-to-PCI bridge (AGP)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS961 [MuTIOL Media IO]
00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
00:02.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 07)
00:02.3 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 07)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev d0)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:06.0 USB Controller: OPTi Inc. 82C861 (rev 10)
00:07.0 RAID bus controller: Silicon Image, Inc. PCI0680 Ultra ATA-133 Host Controller (rev 02)
**00:08.0 Multimedia video controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)**
00:0a.0 Ethernet controller: Intel Corporation 82557/8/9/0/1 Ethernet Pro 100 (rev 08)
01:00.0 VGA compatible controller: nVidia Corporation NV18 [GeForce4 MX 4000] (rev c1)

Output from lsmod
> vmnet                  38204  9 
vmmon                1824812  0 
binfmt_misc            12808  1 
rfcomm                 41744  2 
l2cap                  25728  13 rfcomm
bluetooth              61156  4 rfcomm,l2cap
ppdev                  10372  0 
speedstep_lib           6532  0 
cpufreq_userspace       5284  0 
cpufreq_ondemand        9740  0 
cpufreq_conservative     8712  0 
cpufreq_powersave       2688  0 
cpufreq_stats           7104  0 
freq_table              5536  2 cpufreq_ondemand,cpufreq_stats
sbs                    15112  0 
sbshc                   7680  1 sbs
dock                   11280  0 
video                  19856  0 
output                  4736  1 video
container               5632  0 
battery                14212  0 
iptable_filter          3840  0 
ip_tables              14820  1 iptable_filter
x_tables               16132  1 ip_tables
ac                      6916  0 
lp                     12324  0 
ipv6                  267780  16 
snd_mpu401              9448  0 
snd_mpu401_uart         9728  1 snd_mpu401
evdev                  13056  5 
parport_pc             36260  1 
tuner                  42912  0 
[B]tea5767                 6788  1 tuner
tda8290                12420  1 tuner
tuner_simple           10248  1 tuner
mt20xx                 13192  1 tuner
tea5761                 6020  1 tuner[/B]
parport                37832  3 ppdev,lp,parport_pc
serio_raw               7940  0 
analog                 13600  0 
psmouse                40336  0 
gameport               16008  1 analog
[B]cx8800                 35848  0 
cx88xx                 66088  1 cx8800
ir_common              36100  1 cx88xx
i2c_algo_bit            7300  1 cx88xx[/B]
pcspkr                  4224  0 
quickcam_messenger     14468  0 
usbvideo               28676  1 quickcam_messenger
[B]tveeprom               16656  1 cx88xx
videobuf_dma_sg        14980  2 cx8800,cx88xx
videobuf_core          18820  3 cx8800,cx88xx,videobuf_dma_sg
btcx_risc               5896  2 cx8800,cx88xx
compat_ioctl32          2304  2 cx8800,usbvideo
videodev               29440  3 cx8800,cx88xx,usbvideo
v4l2_common            18304  4 tuner,cx8800,cx88xx,videodev[/B]
v4l1_compat            15492  1 videodev
snd_usb_audio          83936  1 
snd_usb_lib            18432  1 snd_usb_audio
snd_hwdep              10500  1 snd_usb_audio
snd_intel8x0           35356  3 
snd_ac97_codec        101028  1 snd_intel8x0
ac97_bus                3072  1 snd_ac97_codec
snd_pcm_oss            42144  0 
snd_mixer_oss          17920  1 snd_pcm_oss
nvidia               4718832  32 
snd_pcm                78596  4 snd_usb_audio,snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           4868  0 
snd_seq_oss            35584  0 
snd_seq_midi            9376  0 
snd_rawmidi            25760  3 snd_mpu401_uart,snd_usb_lib,snd_seq_midi
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24836  2 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    56996  24 snd_mpu401,snd_mpu401_uart,snd_usb_audio,snd_usb_lib,snd_hwdep,snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
button                  9232  0 
i2c_sis96x              6148  0 
soundcore               8800  1 snd
snd_page_alloc         11400  2 snd_intel8x0,snd_pcm
i2c_core               24832  11 **tuner,tea5767,tda8290,tuner_simple,mt20xx,tea5761,cx88xx,i2c_algo_bit,tveeprom,nvidia,i2c_sis96x**
shpchp                 34452  0 
pci_hotplug            30880  1 shpchp
sis_agp                10116  1 
agpgart                34760  2 nvidia,sis_agp
ext3                  136712  1 
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
sr_mod                 17956  0 
cdrom                  37408  1 sr_mod
usb_storage            73664  0 
sg                     36880  0 
libusual               19108  1 usb_storage
sd_mod                 30720  3 
pata_sis               15236  2 
pata_acpi               8320  0 
floppy                 59588  0 
pata_sil680            11012  0 
ata_generic             8324  0 
e100                   37388  0 
mii                     6400  1 e100
ohci_hcd               25348  0 
libata                159344  4 pata_sis,pata_acpi,pata_sil680,ata_generic
scsi_mod              151436  5 sr_mod,usb_storage,sg,sd_mod,libata
usbcore               146028  8 quickcam_messenger,usbvideo,snd_usb_audio,snd_usb_lib,usb_storage,libusual,ohci_hcd
thermal                16796  0 
processor              36872  1 thermal
fan                     5636  0 
fbcon                  42912  0 
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50580  3 

I think I've highlighted the relevant parts...

Really rather stuck at the moment... Ubuntu picks it up on /dev/Video0 with the quickcam being picked up on /dev/video1 (if that helps)...

EDIT: Hmm... a quick check shows that the devices are the other wqay round... the TV card is on /dev/video1... I'll see if I can get it to go on that one...

EDIT1: Ok, MythTV now picks up the card on /dev/video1 but doesnt pick up any stations at all... it's set up for PAL/Europe-west but going to the mythTV frontend and clicking on watch television results in bouncing back to the same button....

---

### Post by hatman on 2008-05-15
Still no joy, removed and re-installed and still nothing.. Seem to keep going round in circles...

---

