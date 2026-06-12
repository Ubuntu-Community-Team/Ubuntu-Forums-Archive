---
title: "[SOLVED] trust wb 1400t webcam recognised, modules loaded but not working on gutsy"
date: 2007-10-29
forum: Multimedia &amp; Video
---

### Post by Ubuntwan on 2007-10-29
Hi, My Trust wb 1400t webcam is not working on my gutsy system (upgraded from feisty). When plugging in the webcam the light comes on, but after 1 second it switches off again.
The camera does show up with dmesg and lsusb but I have no idea where to go frome here. In Ekiga the only device that shows up is my hauppauge tuner card.

the tail of my dmesg output: [ 2099.014776] usb 2-3: new full speed USB device using ohci_hcd and address 6
[ 2099.227471] usb 2-3: configuration #1 chosen from 1 choice
[ 2099.230436] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/gspcav1/gspca_core.c: USB SPCA5XX camera found. (PAC207)

and my lsusb shows:
Bus 002 Device 007: ID 093a:2468 Pixart Imaging, Inc. Easy Snap Snake Eye WebCam
which should be supported by the spca5xx driver according to [http://mxhaard.free.fr/spca5xx.html](http://mxhaard.free.fr/spca5xx.html) 

and my ls -l /dev/video* shows:
crw-rw---- 1 root video 81,  0 2007-10-29 10:54 /dev/video0
crw-rw---- 1 root video 81,  1 2007-10-29 12:08 /dev/video1
crw-rw---- 1 root video 81, 24 2007-10-29 10:54 /dev/video24
crw-rw---- 1 root video 81, 32 2007-10-29 10:54 /dev/video32

the vidoe0, video24 and video32 belong to the tuner card and the video1 is added as the webcam is plugged in. (ekiga actually shows three tuner cards which could be a result from these three devices(?))

anyway, my lsmod shows:
binfmt_misc            12936  1 
cx8800                 34944  0 
cx88xx                 68132  1 cx8800
bttv                  177012  0 
video_buf              26244  3 cx8800,cx88xx,bttv
ir_common              35460  2 cx88xx,bttv
compat_ioctl32          2304  2 cx8800,bttv
btcx_risc               5896  3 cx8800,cx88xx,bttv
lirc_i2c               11268  0 
lirc_dev               15860  1 lirc_i2c
rfcomm                 42136  2 
l2cap                  26240  11 rfcomm
bluetooth              57060  4 rfcomm,l2cap
ipv6                  273892  14 
ppdev                  10244  0 
cpufreq_stats           7232  0 
cpufreq_powersave       2688  0 
cpufreq_ondemand        9612  0 
freq_table              5792  2 cpufreq_stats,cpufreq_ondemand
cpufreq_userspace       5280  0 
cpufreq_conservative     8072  0 
video                  18060  0 
ac                      6148  0 
dock                   10656  0 
button                  8976  0 
sbs                    19592  0 
container               5504  0 
battery                11012  0 
parport_pc             37412  0 
lp                     12580  0 
parport                37448  3 ppdev,parport_pc,lp
wm8775                  7180  0 
cx25840                26640  0 
tuner                  63144  0 
ivtv                  134928  1 
i2c_algo_bit            7428  3 cx88xx,bttv,ivtv
cx2341x                13316  1 ivtv
tveeprom               16784  3 cx88xx,bttv,ivtv
videodev               29312  6 gspca,cx8800,cx88xx,bttv,ivtv
v4l2_common            18432  9 cx8800,cx88xx,bttv,wm8775,cx25840,tuner,ivtv,cx2341x,videodev
v4l1_compat            15364  3 bttv,ivtv,videodev
snd_intel8x0           34972  4 
snd_ac97_codec        100644  1 snd_intel8x0
analog                 13344  0 
gameport               16776  1 analog
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            44672  0 
snd_mixer_oss          17664  1 snd_pcm_oss
snd_pcm                80388  4 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           4740  0 
snd_seq_oss            33152  0 
snd_seq_midi            9600  0 
snd_mpu401              9640  0 
snd_mpu401_uart         9600  1 snd_mpu401
nvidia               4716468  32 
lmpcm_usb               7168  0 
psmouse                39952  0 
k8temp                  6656  0 
snd_rawmidi            25728  2 snd_seq_midi,snd_mpu401_uart
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
serio_raw               8068  0 
pcspkr                  4224  0 
xpad                    9988  0 
shpchp                 34580  0 
snd_seq                53232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24324  3 snd_pcm,snd_seq
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
pci_hotplug            32704  1 shpchp
snd                    54660  18 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_mpu401,snd_mpu401_uart,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i2c_nforce2             7040  0 
soundcore               8800  1 snd
snd_page_alloc         11400  2 snd_intel8x0,snd_pcm
i2c_core               26112  11 cx88xx,bttv,lirc_i2c,wm8775,cx25840,tuner,ivtv,i2c_algo_bit,tveeprom,nvidia,i2c_nforce2
amd64_agp              13700  1 
agpgart                35016  2 nvidia,amd64_agp
evdev                  11136  4 
ext3                  133896  1 
jbd                    60456  1 ext3
mbcache                 9732  1 ext3
sg                     36764  0 
sd_mod                 30336  5 
8139too                27776  0 
ide_cd                 32672  1 
cdrom                  37536  1 ide_cd
ata_generic             8452  0 
usbhid                 29536  0 
hid                    28928  1 usbhid
floppy                 60004  0 
8139cp                 25088  0 
mii                     6528  2 8139too,8139cp
sata_nv                20612  4 
libata                125168  2 ata_generic,sata_nv
scsi_mod              147084  3 sg,sd_mod,libata
amd74xx                15260  0 [permanent]
ide_core              116804  2 ide_cd,amd74xx
forcedeth              51592  0 
ehci_hcd               36492  0 
ohci_hcd               22916  0 
usbcore               138632  7 gspca,lmpcm_usb,xpad,usbhid,ehci_hcd,ohci_hcd
thermal                14344  0 
processor              32072  1 thermal
fan                     5764  0 
fuse                   47124  5 
apparmor               40728  0 
commoncap               8320  1 apparmor

sudo xawtv -hwscan shows:
[: 12: (opcode:: unexpected operator
This is xawtv-3.95.dfsg.1, running on Linux/i686 (2.6.22-14-generic)
looking for available devices
port 126-126
    type : Xvideo, image scaler
    name : NV17 Video Texture

port 127-158
    type : Xvideo, image scaler
    name : NV05 Video Blitter

/dev/video0: OK                         [ -device /dev/video0 ]
    type : v4l2
    name : Hauppauge WinTV PVR-150
    flags:  capture tuner 

/dev/video1: Invalid argument



So after it is recognised and modules are loaded i really have no idea why it does not work.
**camorama -d /dev/video1** gives 'could not connect to video device /dev/video1 please check connection'. 

As I'm a bit new to Linux I've no idea what is actually going on and where the problem could be. Anyone has an idea what more i can try?
thanx in advance

---

### Post by freedom.sr on 2007-11-10
I have exactly the same problem.

---

### Post by hermz2507 on 2007-11-12
To solve this:

Open pac207.h (gspcav1-20070508/pixart)
Goto line 137
change:

if (id[0] != 0x27 || id[1] != 0x00)
return -ENODEV;

to:

if (id[0] != 0x27 || id[1] != 0x08)
return -ENODEV;

and rerun "sudo ./gspca_build" to rebuild the driver.

Your camera should now work when plugged in.

This solution was found at: [http://lists.zerezo.com/spca50x-devs/msg01290.html]("http://lists.zerezo.com/spca50x-devs/msg01290.html")

---

### Post by Ubuntwan on 2007-11-15
Wow, thanx for helping, it worked! 
I would have never found the answer to that...
Of course I had to move the newly built driver to the correct location (/lib/modules/2.6.22-14-generic/ubuntu/media/gspcav1/gspca.ko or  /lib/modules/2.6.22-14-generic/kernel/drivers/usb/media/gspca.ko , dont know which one did the trick) and remove the gspca module and reload it again. But i had done this before so it was not a big problem, just had to find out how i did it again

Thanx very, very much, now i can see why the cam costed 10,- euros with my own eyes :)

---

### Post by flaimo on 2007-12-08
i have have the same camera in use with my parents computer. the funny think is, that it works in skype beta, when i'm using my ubuntu-account, but when i switch to any other account the device is not found even if the other account has admin-rights too.

where is this pac207.h file located? i have never compiled anything before.

---

### Post by isparkes on 2008-01-19
This works also on my Trust WB-1200p. USB ID:

Bus 001 Device 020: ID 093a:2468 Pixart Imaging, Inc. Easy Snap Snake Eye WebCam

Now just to get Skype using it...

---

### Post by isparkes on 2008-01-19
Just if it helps others, the guide to installing the source and recompiling is found at the top of this thread:

[https://answers.launchpad.net/ubuntu/+question/19033](https://answers.launchpad.net/ubuntu/+question/19033)

A summary of it - it worked for me :

--------
marcobra said on 2007-11-30:

To install the webcam ( you must have an active internet connection ):
1) - We do all from terminal
2) - When the system ask you for password, give your user password, you don't see nothing when you type it, then press enter

Open a terminal from Applications->Accessories->Terminal and type:

sudo aptget update; sudo apt-get upgrade
sudo apt-get install camorama build-essential gspca-source linux-headers-$(uname -r)
cd /usr/src
sudo tar -xjvf gspca-source.tar.bz2
cd /usr/src/modules/gspca/
sudo make
sudo make install
modprobe gspca
camorama

If your cam color are no good open the: /etc/modprobe.d/options file

sudo gedit /etc/modprobe.d/options

and add this row at the end of file:
options gspca force_rgb=1

add the module gspca at the end of /etc/modules file, type:

sudo gedit /etc/modules

add a row at the end of file and type:
gspca

Save and exit and reboot your pc reopen Camorama from menu: Applications->Graphics->...

Hope this help

---

