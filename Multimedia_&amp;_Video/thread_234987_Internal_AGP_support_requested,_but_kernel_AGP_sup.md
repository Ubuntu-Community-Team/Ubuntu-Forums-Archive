---
title: "Internal AGP support requested, but kernel AGP support active."
date: 2006-08-12
forum: Multimedia &amp; Video
---

### Post by chadk on 2006-08-12
Can someone tell me what this means (from dmesg)

```
[17179607.036000] [fglrx] Internal AGP support requested, but kernel AGP support active.
[17179607.036000] [fglrx] Have to use kernel AGP support to avoid conflicts.

```

---

### Post by tseliot on 2006-08-12
It's not a problem. You're using the kernel support for ATI cards instead of the one provided by the ATI driver.

---

### Post by chadk on 2006-08-13
Would I benefit from switching to the ati driver from the kernel agp?

---

### Post by tseliot on 2006-08-13
> **chadk said:**
> Would I benefit from switching to the ati driver from the kernel agp?

I wouldn't know. With Nvidia cards sometimes there is a performance boost.

If you want to try it I can assist you.

if so post the output of:
```
lsmod
```

---

### Post by chadk on 2006-08-13
Hmm that would be great!  Here's my lsmod output.
```
Module                  Size  Used by
video                  16644  0 
tc1100_wmi              7172  0 
sony_acpi               5900  0 
pcc_acpi               12736  0 
hotkey                 11812  0 
dev_acpi               11652  0 
container               4928  0 
button                  6992  0 
acpi_sbs               20556  0 
battery                10308  1 acpi_sbs
ac                      5508  1 acpi_sbs
i2c_acpi_ec             5440  1 acpi_sbs
nfsd                  243012  13 
exportfs                7040  1 nfsd
lockd                  68616  2 nfsd
sunrpc                160060  8 nfsd,lockd
fglrx                 391980  8 
ppdev                  10052  0 
powernow_k8            14560  0 
cpufreq_userspace       6816  1 
cpufreq_stats           6912  0 
freq_table              5152  2 powernow_k8,cpufreq_stats
cpufreq_powersave       2240  0 
cpufreq_ondemand        8104  0 
cpufreq_conservative     9256  0 
dm_mod                 63640  1 
md_mod                 76244  0 
sg                     40352  0 
sd_mod                 20864  0 
parport_pc             38340  0 
lp                     12612  0 
parport                39560  3 ppdev,parport_pc,lp
rsrc_nonstatic         14784  0 
pcmcia_core            45528  1 rsrc_nonstatic
snd_seq_dummy           4164  0 
snd_seq_oss            37632  0 
snd_seq_midi            9888  0 
snd_seq_midi_event      8064  2 snd_seq_oss,snd_seq_midi
snd_seq                58832  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
tda9887                16528  0 
wm8775                  6604  0 
ipv6                  287456  29 
tsdev                   8320  0 
usb_storage            80064  0 
cx25840                27536  0 
tuner                  25184  0 
snd_via82xx            31256  2 
gameport               17032  1 snd_via82xx
tveeprom               14700  0 
ivtv                  227220  0 
snd_ac97_codec         99296  1 snd_via82xx
snd_ac97_bus            2688  1 snd_ac97_codec
i2c_viapro              9364  0 
snd_pcm_oss            56352  0 
snd_mixer_oss          20800  1 snd_pcm_oss
i2c_algo_bit           10120  1 ivtv
snd_pcm                96772  3 snd_via82xx,snd_ac97_codec,snd_pcm_oss
snd_timer              27204  2 snd_seq,snd_pcm
snd_page_alloc         11592  2 snd_via82xx,snd_pcm
snd_mpu401_uart         8896  1 snd_via82xx
snd_rawmidi            27552  2 snd_seq_midi,snd_mpu401_uart
snd_seq_device          9548  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq,snd_rawmidi
shpchp                 49312  0 
pci_hotplug            30916  1 shpchp
snd                    60068  15 snd_seq_oss,snd_seq,snd_via82xx,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_mpu401_uart,snd_rawmidi,snd_seq_device
i2c_core               23168  9 i2c_acpi_ec,tda9887,wm8775,cx25840,tuner,tveeprom,ivtv,i2c_viapro,i2c_algo_bit
videodev               10368  1 ivtv
serio_raw               8132  0 
soundcore              11040  1 snd
tulip                  53792  0 
psmouse                40132  0 
pcspkr                  2564  0 
amd64_agp              13252  1 
agpgart                37072  2 fglrx,amd64_agp
evdev                  10432  1 
ext3                  148296  1 
jbd                    65684  1 ext3
ide_generic             1792  0 
ehci_hcd               36104  0 
uhci_hcd               35472  0 
usbcore               138948  4 usb_storage,ehci_hcd,uhci_hcd
ide_cd                 36228  0 
cdrom                  41504  1 ide_cd
ide_disk               19520  4 
via82cxxx               9988  0 [permanent]
generic                 5444  0 
sata_via               10628  0 
libata                 84176  1 sata_via
scsi_mod              145736  4 sg,sd_mod,usb_storage,libata
thermal                14088  0 
processor              27208  2 powernow_k8,thermal
fan                     5124  0 
capability              5256  0 
commoncap               7616  1 capability
vga16fb                14344  1 
vgastate               10304  1 vga16fb
fbcon                  44640  72 
tileblit                3072  1 fbcon
font                    8640  1 fbcon
bitblit                 6592  1 fbcon
softcursor              2752  1 bitblit

```

---

### Post by tseliot on 2006-08-14
Blackist the amd64_agp & agpgart modules by adding this to your /etc/modprobe.d/blacklist (don't worry if the file is blank or doesn't exist):

```
sudo nano -w /etc/modprobe.d/blacklist
```

Copy and paste the following lines:
```
blacklist agpgart
blacklist amd64_agp
```

CTRL+X to exit (save)

```
sudo nano -w /etc/X11/xorg.conf
```

Put this option in the Section Device of your /etc/X11/xorg.conf:
```
    Option "UseInternalAGPGART" "no"
```

Reboot

---

### Post by whatever on 2006-08-14
> **tseliot said:**
> Blackist the amd64_agp & agpgart modules by adding this to your /etc/modprobe.d/blacklist 

[...]

Put this option in the Section Device of your /etc/X11/xorg.conf:
```
    Option "UseInternalAGPGART" "no"
```

how is agp supposed to work if he disables the kernel agp-support AND the internal agpgart of fglrx? :rolleyes:

---

### Post by tseliot on 2006-08-14
> **whatever said:**
> how is agp supposed to work if he disables the kernel agp-support AND the internal agpgart of fglrx? :rolleyes:

I'm not an expert of ATI cards but for nvidia cards you have to blacklist agpgart and tell your xorg.conf that you won't use agpgart but the module which was compiled together with the kernel.

Isn't it the same for ATI cards?

EDIT: I see... you mean that "UseInternalAGPGART" should be set to "yes", don't you?

---

### Post by whatever on 2006-08-14
> **tseliot said:**
> EDIT: I see... you mean that "UseInternalAGPGART" should be set to "yes", don't you?
yes, that's what i meant :)
however, the internal agpgart only supported very few chipsets. with certain mainboards (e.g. those based on nforce series) you always had to use the kernel agpgart.

i did some quick research and found out that since version 8.25.18 (which is the version included in dapper) the internal agpgart is no longer included in fglrx. thus this whole thread is kind of pointless...

---

### Post by tseliot on 2006-08-14
> **whatever said:**
> yes, that's what i meant :)
however, the internal agpgart only supported very few chipsets. with certain mainboards (e.g. those based on nforce series) you always had to use the kernel agpgart.

i did some quick research and found out that since version 8.25.18 (which is the version included in dapper) the internal agpgart is no longer included in fglrx. thus this whole thread is kind of pointless...

Ok, thanks for reporting.

In other words **chadk**, please remove the lines I told you to add.

---

### Post by chadk on 2006-08-14
lol
that's it then, I'm getting an nvidia card.

---

### Post by whatever on 2006-08-14
what's your problem with the kernel agpgart?

---

### Post by chadk on 2006-08-15
I don't really have one but it seems that a few weeks ago before I reinstalled ubuntu I was getting full screen from mythtv without any problems, but today I can barely get 640x480 out of it without tearing.

---

### Post by mitticus on 2006-08-16
> **tseliot said:**
> I'm not an expert of ATI cards but for nvidia cards you have to blacklist agpgart and tell your xorg.conf that you won't use agpgart but the module which was compiled together with the kernel.

Isn't it the same for ATI cards?

EDIT: I see... you mean that "UseInternalAGPGART" should be set to "yes", don't you?
I'm confused.

What does "usinternalagpgart" mean here? Compiled into the kernel? Why would you have "useinternalagp" as yes if the driver release notes say that internal agp is not supported anymore?

aarrgh. What a mess.

---

### Post by missingxtension on 2006-12-01
i have the same problem but it has to do with a kernel i compiled 
i actually could not find a good source for compiling a kernel with p4 no ht, ati radeon and audigy2 so it could be something i did and it might not even be the right place for this problem but the simtoms are the same 
my lsmod output look like this 
```
Module                  Size  Used by
isofs                  37436  0 
udf                    88708  0 
nls_utf8                2560  1 
vfat                   14080  1 
fat                    55580  1 vfat
binfmt_misc            12680  1 
sr_mod                 17444  0 
fglrx                 412236  9 
video                  17028  0 
fuse                   48276  4 
sbp2                   23944  0 
ipv6                  273056  8 
psmouse                41224  0 
sg                     36892  0 
usb_storage            74944  1 
libusual               16912  1 usb_storage
ati_remote             12424  0 
usbhid                 45024  0 
serio_raw               7812  0 
snd_emu10k1_synth       8320  0 
snd_emux_synth         38784  1 snd_emu10k1_synth
snd_seq_virmidi         7936  1 snd_emux_synth
snd_seq_midi_emul       7552  1 snd_emux_synth
snd_emu10k1           127264  2 snd_emu10k1_synth
snd_ac97_codec         96544  1 snd_emu10k1
snd_ac97_bus            2816  1 snd_ac97_codec
snd_util_mem            5504  2 snd_emux_synth,snd_emu10k1
snd_hwdep              10244  2 snd_emux_synth,snd_emu10k1
snd_pcm_oss            46592  0 
snd_pcm                83332  3 snd_emu10k1,snd_ac97_codec,snd_pcm_oss
snd_page_alloc         10888  2 snd_emu10k1,snd_pcm
snd_mixer_oss          17920  1 snd_pcm_oss
snd_seq_dummy           4356  0 
snd_seq_oss            35840  0 
snd_seq_midi            9344  0 
snd_rawmidi            26496  3 snd_seq_virmidi,snd_emu10k1,snd_seq_midi
snd_seq_midi_event      8448  3 snd_seq_virmidi,snd_seq_oss,snd_seq_midi
e100                   38152  0 
floppy                 60900  0 
mii                     6272  1 e100
snd_seq                57840  9 snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24964  3 snd_emu10k1,snd_pcm,snd_seq
snd_seq_device          9228  8 snd_emu10k1_synth,snd_emux_synth,snd_emu10k1,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
evdev                  10624  3 
shpchp                 39712  0 
pci_hotplug            34112  1 shpchp
intel_agp              24220  1 
agpgart                34248  2 fglrx,intel_agp
snd                    56324  15 snd_emux_synth,snd_seq_virmidi,snd_emu10k1,snd_ac97_codec,snd_hwdep,snd_pcm_oss,snd_pcm,snd_mixer_oss,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
pcspkr                  3712  0 
ehci_hcd               34056  0 
ohci1394               36528  0 
ieee1394              304952  2 sbp2,ohci1394
uhci_hcd               25480  0 
usbcore               135044  7 usb_storage,libusual,ati_remote,usbhid,ehci_hcd,uhci_hcd
ide_generic             1664  0 [permanent]
sd_mod                 22272  7 
ata_piix               14728  4 
libata                106516  1 ata_piix
scsi_mod              141448  6 sr_mod,sbp2,sg,usb_storage,sd_mod,libata
ide_cd                 41632  0 
cdrom                  38432  2 sr_mod,ide_cd
piix                   10884  0 [permanent]
generic                 5508  0 [permanent]

```
i tried to compile as small as possible 
but the linux kernel compilation is confusing and undocumented compared to BSD witch is a snap

---

