---
title: "Is there an Edgy update to &quot;Nvidia Intel Integrated?&quot;"
date: 2006-11-07
forum: Multimedia &amp; Video
---

### Post by theyost on 2006-11-07
I followed the directions, but now it appears I don't have any AGP driver running (I want the "NvAGP" "1" option in xorg.conf to work).

cat /proc/driver/nvidia/agp/status output:

[OUTPUT]Status: Disabled

AGP initializatoin failed, please check the output of the 'dmesg' command...[/OUTPUT]

line 366 of dmesg
> [ 48.439580] NVRM: not using NVAGP, an AGPGART backend is loaded!

EARLIER on line 143 of dmesg
> [ 22801797] Linux agpgart interface v0.101 (c) Dave Jones

Does this mean agpgart is still being loaded?.... heh?

The good news is your current directions have eliminated system crashes... but performace lags. My fallback would be to replace the mobo with one w/out integrated graphics, but for now I am trying to fiddle & fix.

Any help would be greatly appreciated.

lsmod output:

> mythtv@ubuntu-mythtv:~$ lsmod
Module                  Size  Used by
binfmt_misc            16012  1 
speedstep_centrino      8560  1 
cpufreq_userspace       6560  0 
cpufreq_stats           9312  0 
freq_table              7104  2 speedstep_centrino,cpufreq_stats
cpufreq_powersave       3456  0 
cpufreq_ondemand       10928  2 
cpufreq_conservative    11272  0 
video                  22920  0 
tc1100_wmi             10632  0 
sony_acpi               7704  0 
sbs                    20928  0 
pcc_acpi               19968  0 
i2c_ec                  7808  1 sbs
hotkey                 14536  0 
dev_acpi               17540  0 
container               6656  0 
button                  9888  0 
battery                14088  0 
asus_acpi              21924  0 
ac                      8328  0 
ipv6                  334432  21 
smbfs                  87816  2 
xfs                   648904  1 
lp                     16584  0 
snd_seq_dummy           6020  0 
snd_seq_oss            45824  0 
snd_seq_midi           12160  0 
snd_seq_midi_event     11520  2 snd_seq_oss,snd_seq_midi
snd_seq                77344  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
cx88_blackbird         25520  0 
joydev                 14208  0 
af_packet              29452  2 
tsdev                  11136  0 
nvidia               5444468  12 
tda9887                21648  0 
cx88_dvb               18820  2 
cx8802                 17028  2 cx88_blackbird,cx88_dvb
tuner                  63148  0 
snd_via82xx            36520  1 
lirc_mceusb2           14340  0 
usbhid                 51360  0 
sg                     44584  0 
cx88_vp3054_i2c         7680  1 cx88_dvb
lirc_dev               19496  1 lirc_mceusb2
cx88_alsa              18952  0 
gameport               21008  1 snd_via82xx
cx8800                 42764  1 cx88_blackbird
parport_pc             43560  1 
parport                49932  2 lp,parport_pc
i2c_viapro             11928  0 
mt352                  10372  1 cx88_dvb
or51132                13060  1 cx88_dvb
video_buf_dvb           9348  1 cx88_dvb
nxt200x                17796  1 cx88_dvb
zl10353                 8708  1 cx88_dvb
cx24123                18056  1 cx88_dvb
lgdt330x               12444  1 cx88_dvb
cx88xx                 74660  5 cx88_blackbird,cx88_dvb,cx8802,cx88_alsa,cx8800
snd_pcm_oss            57344  0 
snd_mixer_oss          22784  1 snd_pcm_oss
snd_ac97_codec        127064  1 snd_via82xx
snd_ac97_bus            4352  1 snd_ac97_codec
snd_mpu401_uart        12928  1 snd_via82xx
snd_rawmidi            34432  2 snd_seq_midi,snd_mpu401_uart
snd_seq_device         12180  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq,snd_rawmidi
via_rhine              30852  0 
ir_common              32260  1 cx88xx
dvb_core              105008  3 or51132,video_buf_dvb,lgdt330x
cx22702                 9988  1 cx88_dvb
i2c_algo_bit           11784  2 cx88_vp3054_i2c,cx88xx
snd_pcm               108168  4 snd_via82xx,cx88_alsa,snd_pcm_oss,snd_ac97_codec
snd_timer              31112  2 snd_seq,snd_pcm
snd_page_alloc         13200  2 snd_via82xx,snd_pcm
psmouse                51088  0 
serio_raw              10244  0 
snd                    79016  14 snd_seq_oss,snd_seq,snd_via82xx,cx88_alsa,snd_pcm_oss,snd_mixer_oss,snd_ac97_codec,snd_mpu401_uart,snd_rawmidi,snd_seq_device,snd_pcm,snd_timer
soundcore              14112  1 snd
mii                     8192  1 via_rhine
tveeprom               20496  1 cx88xx
compat_ioctl32         11648  1 cx8800
v4l2_common            20736  4 cx88_blackbird,tuner,cx8800,compat_ioctl32
v4l1_compat            15492  1 cx8800
videodev               14592  3 cx88_blackbird,cx8800,cx88xx
i2c_core               29312  16 i2c_ec,nvidia,tda9887,cx88_dvb,tuner,i2c_viapro,mt352,or51132,nxt200x,zl10353,cx24123,lgdt330x,cx88xx,cx22702,i2c_algo_bit,tveeprom
dvb_pll                16132  4 cx88_dvb,or51132,nxt200x,cx22702
shpchp                 49068  0 
pci_hotplug            38912  1 shpchp
video_buf              33540  7 cx88_blackbird,cx88_dvb,cx8802,cx88_alsa,cx8800,video_buf_dvb,cx88xx
btcx_risc               7688  4 cx8802,cx88_alsa,cx8800,cx88xx
evdev                  14592  2 
pcspkr                  5248  0 
floppy                 76648  0 
ext3                  164624  1 
jbd                    74024  1 ext3
ehci_hcd               40456  0 
uhci_hcd               30096  0 
usbcore               167840  5 lirc_mceusb2,usbhid,ehci_hcd,uhci_hcd
ide_generic             2944  0 
ide_cd                 39584  0 
cdrom                  43816  1 ide_cd
via82cxxx              11780  0 [permanent]
sd_mod                 25728  4 
generic                 7428  0 
sata_via               12548  3 
libata                 88984  1 sata_via
scsi_mod              181424  3 sg,sd_mod,libata
thermal                19472  0 
processor              38280  2 speedstep_centrino,thermal
fan                     7432  0 
vesafb                 11048  0 
capability              7304  0 
commoncap              10752  1 capability
vga16fb                16656  1 
cfbcopyarea             5376  2 vesafb,vga16fb
vgastate               10368  1 vga16fb
cfbimgblt               4352  2 vesafb,vga16fb
cfbfillrect             6272  2 vesafb,vga16fb
fbcon                  45824  72 
tileblit                4736  1 fbcon
font                   10240  1 fbcon
bitblit                 8064  1 fbcon
softcursor              3968  1 bitblit
mythtv@ubuntu-mythtv:~$

Any help is appreciated.

-Dave

---

### Post by theyost on 2006-11-08
I found some other's with the same problem here (very bottom of page... by "terrax"):
[http://ubuntuforums.org/showthread.php?t=25080]("http://ubuntuforums.org/showthread.php?t=25080")

Apparently the agpgart module is built into the 64bit kernel.  It is used for IOMMU & addressing memory capacaties > 4GB.

I guess the only fix is to recompile a new kernel... wish me luck :-? 

If anyone else has a better idea, let me know....

-Dave

---

### Post by theyost on 2006-11-10
OK... I am really having fun now. :evil: 

Apparently there is now way to disable agpgart in the new 2.6.18 kernel.  I can see the option in menuconfig... it just won't let me turn it off.  I tried to find the dependencies, but no luck ](*,)

---

### Post by theyost on 2006-11-12
Just an update...

After spending too many hours trying to get over the agpgart-nvidia conflicts in ubuntu-64bit I finally decided to just do a fresh ubuntu-32bit install.

So far (48hours) everything is running smoothly.  Agpgart is running the agp port, but it is not having the original conflicts with the integrated video card like in ubuntu-64.

Just a recap: Ubuntu-64's implementation of agpgart caused conflicts between the integrated video card and my nVidia agp graphics card.  I tried to "blacklist" agpgart and this did stop the system freezes :), but nvagp would still refuse to load because agpgart is *embedded* inside the 64bit kernel :(.  Not having any agp driver slowed graphics performance considerably (especially because I am building a Myth HDTV box).

Why not just recompile a new kernel???  Well, I tried.  Compilation errors were preventing a successful 2.6.17 build, and kernel 2.6.18 will not even give you an option to disable agpgart :???: (I found the agpgart option in menuconfig, but I could find no way to disable it).

Enough for now... hope this helped.

-Dave

---

