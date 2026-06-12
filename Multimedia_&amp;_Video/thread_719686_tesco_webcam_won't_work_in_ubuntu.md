---
title: "tesco webcam won't work in ubuntu"
date: 2008-03-09
forum: Multimedia &amp; Video
---

### Post by twright on 2008-03-09
hi,

i'm having no luck trying to get my tesco webcam working in ubuntu, i have tried easycam, gspca, camorama, cheese and skype 2 (beta)

someone here appears to have got it working with gspca:
[http://cullaloe.stumbleupon.com/tag/ubuntu/](http://cullaloe.stumbleupon.com/tag/ubuntu/)

camorama error message attached

thanks in advance,
tom

lsusb output:
```
tom@tom-laptop:~$ lsusb
Bus 006 Device 001: ID 0000:0000  
Bus 004 Device 002: ID 093a:2468 Pixart Imaging, Inc. Easy Snap Snake Eye WebCam
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
```lsdev output:
```
Device            DMA   IRQ  I/O Ports
------------------------------------------------
0000:00:12.0                 8400-840f 8430-8437 8438-843f 8450-8453 8454-8457
0000:00:14.0                 8410-841f
0000:00:14.1                 0170-0177 01f0-01f7 0376-0376 03f6-03f6 8420-842f
0000:01:05.0                   9000-90ff
acpi                      9 
ACPI                         8000-8003 8004-8005 8008-800b 8010-8015 8020-8027 8200-8200 8204-8207
ahci                     21 
cascade             4       
dma                          0080-008f
dma1                         0000-001f
dma2                         00c0-00df
ehci_hcd:usb6            20 
eth0                     19 
fglrx                    17 
fpu                          00f0-00ff
i8042                  1 12 
ide0                     14    01f0-01f7   03f6-03f6   8420-8427
Intel                    16 
keyboard                     0060-006f
ndiswrapper              18 
PCI                          0cf8-0cff 9000-9fff
pic1                         0020-0021
pic2                         00a0-00a1
piix4_smbus                    8410-8417
pnp                          0220-022f 1080-1080
rtc                       8  0070-0077
sdhci:slot0              22 
timer                     0 
timer0                       0040-0043
timer1                       0050-0053
vga+                         03c0-03df
```lsmod output:
```
gspca                 608336  0 
nls_iso8859_1           5120  0 
vfat                   14080  0 
fat                    54300  1 vfat
ext2                   67208  0 
usb_storage            73024  0 
libusual               18448  1 usb_storage
videodev               29312  1 gspca
v4l2_common            18432  1 videodev
v4l1_compat            15364  1 videodev
battery                11012  0 
ac                      6148  0 
thermal                14344  0 
fan                     5764  0 
button                  8976  0 
b44                    28300  0 
mii                     6528  1 b44
ndiswrapper           185240  0 
snd_rtctimer            4384  0 
af_packet              24840  6 
nls_cp437               6784  1 
isofs                  36412  1 
udf                    87204  0 
binfmt_misc            12936  1 
rfcomm                 42136  2 
l2cap                  26240  11 rfcomm
bluetooth              57060  4 rfcomm,l2cap
ipv6                  273892  12 
ppdev                  10244  0 
powernow_k8            16960  1 
cpufreq_ondemand        9612  1 
cpufreq_stats           7232  0 
freq_table              5792  3 powernow_k8,cpufreq_ondemand,cpufreq_stats
cpufreq_userspace       5280  0 
cpufreq_conservative     8072  0 
cpufreq_powersave       2688  0 
sbs                    19592  0 
video                  18060  0 
container               5504  0 
dock                   10656  0 
parport_pc             37412  0 
lp                     12580  0 
parport                37448  3 ppdev,parport_pc,lp
hsfhda                110120  1 
hsfserial              24740  1 hsfhda
hsfengine            1266700  2 hsfhda,hsfserial
hsfosspec             105832  6 hsfhda,hsfserial,hsfengine
snd_hda_intel          22936  3 
snd_hda_codec         254608  2 hsfhda,snd_hda_intel
snd_pcm_oss            44672  0 
snd_mixer_oss          17664  1 snd_pcm_oss
snd_pcm                80388  4 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           4740  0 
snd_seq_oss            33152  0 
snd_seq_midi            9600  0 
snd_rawmidi            25728  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                53232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
joydev                 11328  0 
snd_timer              24324  4 snd_rtctimer,snd_pcm,snd_seq
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54660  14 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
sdhci                  18828  0 
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
mmc_core               28420  1 sdhci
fglrx                1476940  24 
k8temp                  6656  0 
serio_raw               8068  0 
psmouse                39952  0 
pcspkr                  4224  0 
i2c_piix4               9740  0 
i2c_core               26112  1 i2c_piix4
shpchp                 34580  0 
pci_hotplug            32704  1 shpchp
ati_agp                10124  0 
agpgart                35016  2 fglrx,ati_agp
evdev                  11136  6 
ide_cd                 32672  1 
cdrom                  37536  1 ide_cd
ext3                  133896  3 
jbd                    60456  1 ext3
mbcache                 9732  2 ext2,ext3
sg                     36764  0 
sd_mod                 30336  5 
atiixp                  7056  0 [permanent]
ide_core              116804  3 usb_storage,ide_cd,atiixp
ahci                   23300  4 
ehci_hcd               36492  0 
ata_generic             8452  0 
libata                125168  2 ahci,ata_generic
scsi_mod              147084  4 usb_storage,sg,sd_mod,libata
ohci_hcd               22916  0 
usbcore               138632  8 gspca,usb_storage,libusual,ndiswrapper,hsfosspec,ehci_hcd,ohci_hcd
processor              32072  2 thermal,powernow_k8
fuse                   47124  1 
apparmor               40728  0 
commoncap               8320  1 apparmor
```

---

### Post by linuxwizard on 2008-03-09
Try using Ekiga see if the cam works/detected. You may have to work with the settings > Open Ekiga > Edit > Preferences > Video > Video Devices > try changing some of the settings. And there are other settings you can work with for color & brightness.

---

### Post by twright on 2008-03-09
ekiga says "no devices detected", i have tried both the v4l and v4l2 plugins

---

### Post by linuxwizard on 2008-03-09
Doing some searching on your cam > Bus 004 Device 002: ID 093a:2468 Pixart Imaging, Inc. Easy Snap Snake Eye WebCam > I found here almost to bottom of page > [http://mxhaard.free.fr/spca5xx.html](http://mxhaard.free.fr/spca5xx.html) > 7 or 8 listing with ID 093a:2468 which IDs your cam. Looks like you need the spca5xx driver > [http://mxhaard.free.fr/download.html](http://mxhaard.free.fr/download.html)

---

### Post by twright on 2008-03-10
it say's it's only for kernel 2.6.16 and lower :(

i get various errors when trying to compile:
```
tom@tom-laptop:~/Desktop/spca5xx-v4l1goodbye$ make
   Building SPCA5XX driver for 2.5/2.6 kernel.
   Remember: you must have read/write access to your kernel source tree.
make -C /lib/modules/`uname -r`/build SUBDIRS=/home/tom/Desktop/spca5xx-v4l1goodbye CC=cc modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  CC [M]  /home/tom/Desktop/spca5xx-v4l1goodbye/drivers/usb/spca5xx.o
/home/tom/Desktop/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:39:26: error: linux/config.h: No such file or directory
/home/tom/Desktop/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c: In function ‘spca50x_init_isoc’:
/home/tom/Desktop/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:1623: warning: assignment from incompatible pointer type
/home/tom/Desktop/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c: In function ‘spca5xx_open’:
/home/tom/Desktop/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:2394: warning: implicit declaration of function ‘video_devdata’
/home/tom/Desktop/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:2394: warning: initialization makes pointer from integer without a cast
/home/tom/Desktop/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:2399: warning: implicit declaration of function ‘video_get_drvdata’
/home/tom/Desktop/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:2399: warning: initialization makes pointer from integer without a cast
/home/tom/Desktop/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c: In function ‘spca5xx_close’:
/home/tom/Desktop/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:2489: warning: initialization makes pointer from integer without a cast
/home/tom/Desktop/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c: In function ‘spca5xx_do_ioctl’:
/home/tom/Desktop/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:2549: warning: initialization makes pointer from integer without a cast
/home/tom/Desktop/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c: In function ‘spca5xx_ioctl’:
/home/tom/Desktop/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:3093: warning: implicit declaration of function ‘video_usercopy’
/home/tom/Desktop/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c: In function ‘spca5xx_read’:
/home/tom/Desktop/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:3112: warning: initialization makes pointer from integer without a cast
/home/tom/Desktop/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c: In function ‘spca5xx_mmap’:
/home/tom/Desktop/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:3211: warning: initialization makes pointer from integer without a cast
/home/tom/Desktop/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c: At top level:
/home/tom/Desktop/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:3263: error: variable ‘spca50x_template’ has initializer but incomplete type
/home/tom/Desktop/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:3264: error: unknown field ‘owner’ specified in initializer
/home/tom/Desktop/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:3264: warning: excess elements in struct initialiser
/home/tom/Desktop/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:3264: warning: (near initialization for ‘spca50x_template’)
/home/tom/Desktop/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:3265: error: unknown field ‘name’ specified in initializer
/home/tom/Desktop/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:3265: warning: excess elements in struct initialiser
/home/tom/Desktop/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:3265: warning: (near initialization for ‘spca50x_template’)
/home/tom/Desktop/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:3266: error: unknown field ‘type’ specified in initializer
/home/tom/Desktop/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:3266: warning: excess elements in struct initialiser
/home/tom/Desktop/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:3266: warning: (near initialization for ‘spca50x_template’)
/home/tom/Desktop/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:3267: error: unknown field ‘hardware’ specified in initializer
/home/tom/Desktop/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:3267: warning: excess elements in struct initialiser
/home/tom/Desktop/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:3267: warning: (near initialization for ‘spca50x_template’)
/home/tom/Desktop/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:3268: error: unknown field ‘fops’ specified in initializer
/home/tom/Desktop/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:3268: warning: excess elements in struct initialiser
/home/tom/Desktop/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:3268: warning: (near initialization for ‘spca50x_template’)
/home/tom/Desktop/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:3270: error: unknown field ‘release’ specified in initializer
/home/tom/Desktop/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:3270: error: ‘video_device_release’ undeclared here (not in a function)
/home/tom/Desktop/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:3270: warning: excess elements in struct initialiser
/home/tom/Desktop/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:3270: warning: (near initialization for ‘spca50x_template’)
/home/tom/Desktop/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:3272: error: unknown field ‘minor’ specified in initializer
/home/tom/Desktop/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:3272: warning: excess elements in struct initialiser
/home/tom/Desktop/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:3272: warning: (near initialization for ‘spca50x_template’)
/home/tom/Desktop/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c: In function ‘cd_to_spca50x’:
/home/tom/Desktop/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:3340: warning: implicit declaration of function ‘to_video_device’
/home/tom/Desktop/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:3340: warning: initialization makes pointer from integer without a cast
/home/tom/Desktop/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:3341: warning: return makes pointer from integer without a cast
/home/tom/Desktop/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c: In function ‘spca50x_create_sysfs’:
/home/tom/Desktop/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:3450: warning: implicit declaration of function ‘video_device_create_file’
/home/tom/Desktop/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c: In function ‘spca5xx_probe’:
/home/tom/Desktop/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:5509: warning: implicit declaration of function ‘video_device_alloc’
/home/tom/Desktop/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:5509: warning: assignment makes pointer from integer without a cast
/home/tom/Desktop/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:5512: error: invalid application of ‘sizeof’ to incomplete type ‘struct video_device’ 
/home/tom/Desktop/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:5512: error: invalid application of ‘sizeof’ to incomplete type ‘struct video_device’ 
/home/tom/Desktop/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:5512: error: invalid application of ‘sizeof’ to incomplete type ‘struct video_device’ 
/home/tom/Desktop/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:5514: error: dereferencing pointer to incomplete type
/home/tom/Desktop/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:5516: warning: implicit declaration of function ‘video_set_drvdata’
/home/tom/Desktop/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:5521: warning: implicit declaration of function ‘video_register_device’
/home/tom/Desktop/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:5521: error: ‘VFL_TYPE_GRABBER’ undeclared (first use in this function)
/home/tom/Desktop/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:5521: error: (Each undeclared identifier is reported only once
/home/tom/Desktop/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:5521: error: for each function it appears in.)
/home/tom/Desktop/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:5550: error: dereferencing pointer to incomplete type
/home/tom/Desktop/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:5551: warning: implicit declaration of function ‘video_device_release’
/home/tom/Desktop/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:5553: warning: implicit declaration of function ‘video_unregister_device’
make[2]: *** [/home/tom/Desktop/spca5xx-v4l1goodbye/drivers/usb/spca5xx.o] Error 1
make[1]: *** [_module_/home/tom/Desktop/spca5xx-v4l1goodbye] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
make: *** [default] Error 2

```

---

### Post by mag9lubuskie on 2008-03-21
You've got problems because you downloaded 'goodbye' version of gspca which is developed for older kernels. Step by step how I managed to run Tesco webcam on Ubuntu 7.10 and Red Hat EL 5:

1. Download source from [http://mxhaard.free.fr/download.html](http://mxhaard.free.fr/download.html). You got there two versions:
 [LIST]
[*]for kernel up from 2.6.11 : gspcav1-20071224.tar.gz
[*] for kernel below 2.6.11: spca5xx version 0.60.00-1: spca5xx-v4l1goodbye.tar.gz
[/LIST]
```
wget http://mxhaard.free.fr/spca50x/Download/gspcav1-20071224.tar.gz
```

2. Unpack it. ```
 tar zxvf gspcav1-20071224.tar.gz
``` and get into this directory```
 cd gspcav1-20071224
```
3.```
 sudo apt-get install camorama build-essential linux-headers-$(uname -r)
```
4. ```
sudo make
```
5. ```
sudo make install
```
6.```
 sudo modprobe gspca
```

and that is it!
----
in RedHat don't forget to install kernel souce : ```
yum install kernel-devel kernel-xen-devel
```

---

