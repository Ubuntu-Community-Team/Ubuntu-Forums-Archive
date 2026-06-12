---
title: "nvidia/agpgart problems"
date: 2006-05-24
forum: Multimedia &amp; Video
---

### Post by chameleon_789 on 2006-05-24
No matter what I do, I can't enable agp support for my Geforce 6600gt. Neither Nvidia's agpgart or the default kernel module seem to have any effect. Can anyone help me out?

I always get this message : 
```
cat /proc/driver/nvidia/agp/status
Status:          Disabled

AGP initialization failed, please check the ouput
of the 'dmesg' command and/or your system log file
for additional information on this problem.
```

I've added "NvAGP" "3" to my xorg.conf, and I've tried both 'nvidia-agp' and 'agpgart' in /etc/modules, but dmesg gives no error messages using either. I've not done anything to modprobe.conf. Also, /dev/agpgart is mentioned in a few wiki's, but it's not in my /dev, wondering if that's a problem..? 

I'm using a recompiled breezy badger 2.6.12 amd64 kernel with IO_MMU disabled and agpgart as a kernel module, and the 8762 nvidia driver installed using nvidia's installer.

---

### Post by indulis on 2006-05-24
Have your checked that your BIOS has primary video card set to AGP?

I also had problems with instability at AGP 8x, had to reduce it to 4x to be stable on my older motherboard.  The instructions for this are buried in the readme (also on the nvidia website, on the download page, SOME of the readme file links work OK).

I am running a 6200A, with Linux drivers 1.0-8756, and kernel 2.6.12-10-k7

I remember following the instructions to get the agpart module working, but also remember having to move some modules around (and I *think* I had to change /etc/ld.so.conf as shown below.. tho I've had problems with mythtv as well so some of this might have been mythtv related).

Cheers,

Indulis
My /etc/X11/xorg.conf
```


Section "Device"
    Identifier     "NVIDIA Corporation 6200A"
    Driver         "nvidia"
    Option "NvAGP" "1"
    Option "RenderAccel" "on"
    Option "NoLogo" "on"
    Option "XvmcUsesTextures" "true"
EndSection

```

```

mythtv@kato:~$ ls -l /dev/agpgart
crw-rw----  1 root video 10, 175 May 25 09:53 /dev/agpgart

indulis@kato:~$ cat /etc/ld.so.conf
/usr/X11R6/lib/
/usr/local/lib/


cat /proc/driver/nvidia/agp/status
Status:          Enabled
Driver:          AGPGART
AGP Rate:        4x
Fast Writes:     Disabled
SBA:             Enabled

indulis@kato:~$ locate agp
/dev/agpgart
/dev/.udevdb/class@misc@agpgart
/lib/modules/2.6.12-10-k7/kernel/drivers/char/agp
/lib/modules/2.6.12-10-k7/kernel/drivers/char/agp/efficeon-agp.ko
/lib/modules/2.6.12-10-k7/kernel/drivers/char/agp/sworks-agp.ko
/lib/modules/2.6.12-10-k7/kernel/drivers/char/agp/intel-agp.ko
/lib/modules/2.6.12-10-k7/kernel/drivers/char/agp/amd-k7-agp.ko
/lib/modules/2.6.12-10-k7/kernel/drivers/char/agp/ati-agp.ko
/lib/modules/2.6.12-10-k7/kernel/drivers/char/agp/via-agp.ko
/lib/modules/2.6.12-10-k7/kernel/drivers/char/agp/agpgart.ko
/lib/modules/2.6.12-10-k7/kernel/drivers/char/agp/sis-agp.ko
/lib/modules/2.6.12-10-k7/kernel/drivers/char/agp/ali-agp.ko
/lib/modules/2.6.12-10-k7/kernel/drivers/char/agp/amd64-agp.ko
/lib/modules/2.6.12-10-k7/kernel/drivers/char/agp/nvidia-agp.ko


indulis@kato:~$ lsmod
Module                  Size  Used by
rfcomm                 38748  0
l2cap                  25156  5 rfcomm
bluetooth              48580  4 rfcomm,l2cap
cpufreq_powersave       1792  0
cpufreq_stats           5316  0
cpufreq_userspace       4380  0
cpufreq_ondemand        6108  0
cpufreq_conservative     7012  0
freq_table              4484  1 cpufreq_stats
ipt_limit               2304  8
iptable_mangle          2816  0
ipt_LOG                 7040  8
ipt_MASQUERADE          3392  0
iptable_nat            23060  1 ipt_MASQUERADE
ipt_TOS                 2432  0
ipt_REJECT              5440  1
ip_conntrack_irc       71760  0
ip_conntrack_ftp       72784  0
ipt_state               1856  6
ip_conntrack           43128  5 ipt_MASQUERADE,iptable_nat,ip_conntrack_irc,ip_conntrack_ftp,ipt_state
iptable_filter          2880  1
ip_tables              19648  9 ipt_limit,iptable_mangle,ipt_LOG,ipt_MASQUERADE,iptable_nat,ipt_TOS,ipt_REJECT,ipt_state,iptable_filter
nvidia               4544948  12
tun                    11648  1
tc1100_wmi              6788  0
video                  15812  0
battery                 9412  0
container               4480  0
i2c_acpi_ec             5568  0
button                  6544  0
pcc_acpi               11200  0
sony_acpi               5388  0
ac                      4804  0
dev_acpi               11268  0
hotkey                  9380  0
ipv6                  252544  24
af_packet              22088  2
floppy                 59412  0
pcspkr                  3460  0
rtc                    12408  0
i2c_viapro              8016  0
via_ircc               30548  0
irda                  188412  1 via_ircc
crc_ccitt               2048  1 irda
ohci1394               34804  0
snd_cmipci             33696  1
gameport               14920  1 snd_cmipci
snd_pcm_oss            53152  0
snd_mixer_oss          19392  1 snd_pcm_oss
snd_pcm                89032  2 snd_cmipci,snd_pcm_oss
snd_page_alloc         10696  1 snd_pcm
snd_opl3_lib           10688  1 snd_cmipci
snd_hwdep               8992  1 snd_opl3_lib
snd_mpu401_uart         7360  1 snd_cmipci
cx88_blackbird         15428  0
cx88_dvb                7812  36
cx8802                 10052  2 cx88_blackbird,cx88_dvb
mt352                   6788  1 cx88_dvb
or51132                10116  1 cx88_dvb
firmware_class         10240  2 cx88_blackbird,or51132
video_buf_dvb           6340  1 cx88_dvb
dvb_core               82088  1 video_buf_dvb
cx22702                 6468  1 cx88_dvb
dvb_pll                 4612  3 cx88_dvb,or51132,cx22702
cx8800                 31692  0
cx88xx                 54176  4 cx88_blackbird,cx88_dvb,cx8802,cx8800
i2c_algo_bit            9480  1 cx88xx
video_buf              21316  6 cx88_blackbird,cx88_dvb,cx8802,video_buf_dvb,cx8800,cx88xx
ir_common               7620  1 cx88xx
tveeprom               13208  1 cx88xx
i2c_core               21328  9 nvidia,i2c_acpi_ec,i2c_viapro,mt352,or51132,cx22702,cx88xx,i2c_algo_bit,tveeprom
v4l1_compat            14788  1 cx8800
v4l2_common             5824  1 cx8800
btcx_risc               4936  3 cx8802,cx8800,cx88xx
videodev                9536  3 cx88_blackbird,cx8800,cx88xx
shpchp                 97252  0
pci_hotplug            27636  1 shpchp
via_agp                 9728  1
agpgart                34888  2 nvidia,via_agp
jfs                   190148  1
ext3                  137352  1
jbd                    55128  1 ext3
ext2                   67528  1
mbcache                 9348  2 ext3,ext2
tsdev                   7872  0
evdev                   9728  0
snd_seq_dummy           3716  0
snd_seq_oss            33664  0
snd_seq_midi            9184  0
snd_rawmidi            25056  2 snd_mpu401_uart,snd_seq_midi
snd_seq_midi_event      7040  2 snd_seq_oss,snd_seq_midi
snd_seq                51024  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24260  3 snd_pcm,snd_opl3_lib,snd_seq
snd_seq_device          8524  6 snd_opl3_lib,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    55172  14 snd_cmipci,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_opl3_lib,snd_hwdep,snd_mpu401_uart,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               9696  1 snd
sr_mod                 17252  0
sbp2                   23176  0
ieee1394              101752  2 ohci1394,sbp2
psmouse                30212  0
mousedev               11680  1
parport_pc             35460  1
lp                     12420  0
parport                36104  2 parport_pc,lp
md                     45648  0
reiserfs              264048  9
dm_mod                 58044  20
thermal                13064  0
processor              22908  1 thermal
fan                     4548  0
sd_mod                 19216  8
ehci_hcd               34312  0
uhci_hcd               31376  0
usbcore               118396  3 ehci_hcd,uhci_hcd
tg3                    97220  0
sata_promise           11204  19
libata                 54020  1 sata_promise
scsi_mod              135944  5 sr_mod,sbp2,sd_mod,sata_promise,libata
8139cp                 19776  0
8139too                25728  0
mii                     5760  2 8139cp,8139too
ide_cd                 41732  0
cdrom                  39904  2 sr_mod,ide_cd
ide_disk               18560  7
ide_generic             1472  0
via82cxxx              13532  1
ide_core              139028  4 ide_cd,ide_disk,ide_generic,via82cxxx
unix                   27248  906
vesafb                  8088  0
capability              4808  0
commoncap               6912  1 capability
vga16fb                12680  1
vgastate                9792  1 vga16fb
softcursor              2496  2 vesafb,vga16fb
cfbimgblt               3008  2 vesafb,vga16fb
cfbfillrect             3968  2 vesafb,vga16fb
cfbcopyarea             4672  2 vesafb,vga16fb
fbcon                  39104  72
tileblit                2432  1 fbcon
font                    8320  1 fbcon
bitblit                 5696  1 fbcon


```

---

### Post by chameleon_789 on 2006-05-24
Ok, thanks to your tip I think I worked out why it wasn't working.. I typed 'locate agp', and all I have in lib/modules/2.6.12-10/kernel/drivers/char/agp is agpgart.ko. I tried to recompile the kernel with make xconfig and lo-and-behold, sis-agp and most of the other *-agp.ko depend on x86_32, so afaik they don't compile with a 64 bit kernel.

I searched around a bit though and found a patch for 2.6.16 (2.6.12-mm2) which enables sis-agp and via-agp on x86_64 kernels, so that's compiling now..

---

### Post by indulis on 2006-05-25
Glad that my stumbling around has been useful to you... shared pain is shared gain or something like that ;-)

---

