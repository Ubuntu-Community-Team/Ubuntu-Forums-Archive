---
title: "Agpgart"
date: 2006-08-03
forum: Multimedia &amp; Video
---

### Post by Ephemeriis on 2006-08-03
I'm running a GeForce FX5600 on an nForce2 motherboard.  I've got an issue with graphical corruption periodically...  My system runs fine most of the time, but when I run 3D applications (including any GL screensavers) I've got about a 50% chance of crashing my machine.

The problem seems to be a known issue whith certain motherboard chipsets and the AGPGART drivers.  The suggested fix is to use NvAGP instead.  I've seen a couple suggestions on how to do this, but they don't seem to be working.

One recommended disabling the AGPGART module...  But it appears to be statically linked in Ubuntu.  Either that, or I'm following the directions incorrectly.

Another suggested passing "agp=off" through GRUB, but that didn't seem to work either.

I'm thinking, from what I've read, that I'm going to have to recompile the kernel.  Is this correct, or am I misinformed?  Is there a relatively easy way to get NvAGP running instead of AGPGART?

---

### Post by tseliot on 2006-08-04
Try putting this in the Section Device of your xorg.conf:
```
Option "NvAGP" "1"
```

Or, if that doesn't help:
```
Option "NvAGP" "0"
```

---

### Post by Ephemeriis on 2006-08-04
Right now I'm using the default setting of NvAGP=3, which attempts to use AGPGART and then fails over to NvAGP.  It didn't occur to me to try manually setting it to 1.  I'll give that a try when I get home.

NvAGP=0 sets it to off, correct?  If I want to actually use NvAGP, why would I want to turn it off?  Or am I misunderstanding something?

---

### Post by Ephemeriis on 2006-08-04
Bah!

Both those settings (NvAGP=1 and NvAGP=0) completely disable my AGP.  I'm not running AGPGART, but I'm not running NvAGP either.

Any other suggestions?

---

### Post by mlalkaka on 2006-08-08
**Appendix F of *NVIDIA Accelerated Linux Driver Set README and Installation Guide*:**
> 
NVIDIA AGP support *cannot* be used if AGPGART is loaded in the kernel. It is recommended that you compile AGPGART as a module and *make sure that it is not loaded when trying to use NVIDIA AGP*.
 
In the Dapper Drake kernel, AGPGART has been compiled as a module. This can be confirmed by the following:
```

$ grep -i agp /boot/config-2.6.15-26-686
[B]CONFIG_AGP=m
CONFIG_AGP_ALI=m
CONFIG_AGP_ATI=m
CONFIG_AGP_AMD=m
CONFIG_AGP_AMD64=m
CONFIG_AGP_INTEL=m
CONFIG_AGP_NVIDIA=m
CONFIG_AGP_SIS=m
CONFIG_AGP_SWORKS=m
CONFIG_AGP_VIA=m
CONFIG_AGP_EFFICEON=m[/B]

$ lsmod | grep agpgart
**agpgart**                36784  2 nvidia,sis_agp

``` 
So that means all we have to do is [LIST]
[*]ensure that the agpgart module is not loaded when Ubuntu boots up, and
[*]ensure that the nvidia module uses nvagp instead of agpgart.[/LIST]We know how to make the nvidia module use nvagp:
**/etc/xorg.conf:**
```

Option "NvAGP" "1"

``` 
All we need to do is remove the loading of agpgart from the boot up process; this is what I do not know how to do. I can't find agpgart mentioned anywhere in /etc/modprobe.d. Any ideas?

---

### Post by tseliot on 2006-08-08
what's the output of this command?
```
lsmod
```

---

### Post by mlalkaka on 2006-08-08
**The output of lsmod:**
```

[FONT=Courier New][SIZE=4]Module                  Size  Used by
binfmt_misc            13064  1
rfcomm                 43604  0
l2cap                  28192  5 rfcomm
bluetooth              54084  4 rfcomm,l2cap
ipv6                  286976  22
ppdev                   9668  0
speedstep_lib           4580  0
cpufreq_userspace       6496  0
cpufreq_stats           6688  0
freq_table              4928  1 cpufreq_stats
cpufreq_powersave       1920  0
cpufreq_ondemand        7752  0
cpufreq_conservative     9000  0
video                  16324  0
tc1100_wmi              6884  0
sony_acpi               5580  0
pcc_acpi               12416  0
hotkey                 11492  0
dev_acpi               11236  0
container               4608  0
button                  6704  0
acpi_sbs               20172  0
battery                 9988  1 acpi_sbs
ac                      5220  1 acpi_sbs
i2c_acpi_ec             5120  1 acpi_sbs
nls_iso8859_1           4224  1
nls_cp437               5888  1
vfat                   14496  1
fat                    55548  1 vfat
dm_mod                 63256  1
md_mod                 76052  0
af_packet              24520  2
snd_seq_dummy           3908  0
snd_seq_oss            37216  0
snd_seq_midi            9600  0
snd_seq_midi_event      7520  2 snd_seq_oss,snd_seq_midi
snd_seq                58160  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
lp                     12356  0
snd_mpu401              6792  0
snd_mpu401_uart         8640  1 snd_mpu401
parport_pc             37988  1
analog                 12800  0
snd_intel8x0           35772  1
snd_ac97_codec        100224  1 snd_intel8x0
snd_ac97_bus            2400  1 snd_ac97_codec
parport                39400  3 ppdev,lp,parport_pc
gameport               16776  1 analog
snd_pcm_oss            56448  0
snd_mixer_oss          20544  1 snd_pcm_oss
snd_rawmidi            26848  2 snd_seq_midi,snd_mpu401_uart
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq,snd_rawmidi
snd_pcm                96708  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              26884  2 snd_seq,snd_pcm
pcspkr                  2244  0
snd                    60004  14 snd_seq_oss,snd_seq,snd_mpu401,snd_mpu401_uart,snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_rawmidi,snd_seq_device,snd_pcm,snd_timer
soundcore              10784  1 snd
snd_page_alloc         11304  2 snd_intel8x0,snd_pcm
floppy                 64676  0
8139too                29056  0
nvidia               4552660  12
psmouse                40004  0
serio_raw               7748  0
sis900                 25152  0
mii                     6176  2 8139too,sis900
i2c_sis96x              5860  0
i2c_core               22848  3 i2c_acpi_ec,nvidia,i2c_sis96x
shpchp                 49504  0
pci_hotplug            30788  1 shpchp
sis_agp                 9028  1
agpgart                36784  2 nvidia,sis_agp
tsdev                   8032  0
evdev                  10176  1
joydev                 10432  0
usbhid                 42752  0
ext3                  148104  2
jbd                    65876  1 ext3
ide_generic             1504  0
ohci_hcd               22724  0
usbcore               139076  3 usbhid,ohci_hcd
ide_cd                 35780  0
cdrom                  41408  1 ide_cd
ide_disk               19136  6
sis5513                17320  1
generic                 5124  0
thermal                13768  0
processor              26888  1 thermal
fan                     4836  0
capability              4968  0
commoncap               7328  1 capability
vga16fb                13992  1
vgastate               10208  1 vga16fb
fbcon                  43904  72
tileblit                2784  1 fbcon
font                    8320  1 fbcon
bitblit                 6464  1 fbcon
softcursor              2304  1 bitblit[/SIZE][/FONT]

```

---

### Post by Ephemeriis on 2006-08-08
Output of lsmod:
```
Module                  Size  Used by
vmvirtualnic            2308  0
vm_bridge               9364  1
vm_main                34224  0
hypervisor             66932  1 vm_main
binfmt_misc            12296  1
rfcomm                 40216  0
l2cap                  26244  5 rfcomm
bluetooth              49892  4 rfcomm,l2cap
ppdev                   9220  0
cpufreq_userspace       4696  0
cpufreq_stats           5636  0
freq_table              4740  1 cpufreq_stats
cpufreq_powersave       1920  0
cpufreq_ondemand        6428  0
cpufreq_conservative     7332  0
video                  16260  0
tc1100_wmi              6916  0
sony_acpi               5644  0
pcc_acpi               12416  0
hotkey                 11556  0
dev_acpi               11140  0
container               4608  0
button                  6672  0
acpi_sbs               19980  0
battery                 9988  1 acpi_sbs
ac                      5252  1 acpi_sbs
i2c_acpi_ec             5120  1 acpi_sbs
dm_mod                 58936  1
ipv6                  265728  6
af_packet              22920  2
md_mod                 72532  0
parport_pc             35780  0
lp                     11844  0
parport                36296  3 ppdev,parport_pc,lp
snd_intel8x0           33692  2
snd_ac97_codec         93088  1 snd_intel8x0
snd_ac97_bus            2304  1 snd_ac97_codec
tsdev                   8000  0
nvidia               4550772  12
pcspkr                  2180  0
snd_pcm_oss            53664  0
snd_mixer_oss          18688  2 snd_pcm_oss
usbhid                 39904  0
snd_pcm                89864  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              25220  1 snd_pcm
shpchp                 45632  0
pci_hotplug            29236  1 shpchp
snd                    55268  8 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              10208  2 snd
snd_page_alloc         10632  2 snd_intel8x0,snd_pcm
rtc                    13492  0
psmouse                36100  0
serio_raw               7300  0
i2c_nforce2             6912  0
forcedeth              30732  0
i2c_core               21904  3 i2c_acpi_ec,nvidia,i2c_nforce2
nvidia_agp              8348  1
agpgart                34888  2 nvidia,nvidia_agp
evdev                   9856  1
ext3                  135688  1
jbd                    58772  1 ext3
ide_generic             1536  0
ehci_hcd               34184  0
ohci_hcd               21892  0
usbcore               130692  4 usbhid,ehci_hcd,ohci_hcd
ide_cd                 33028  0
cdrom                  38560  1 ide_cd
ide_disk               17664  4
generic                 5124  0
amd74xx                15260  0 [permanent]
sata_nv                 9732  0
libata                 78992  1 sata_nv
scsi_mod              139496  1 libata
thermal                13576  0
processor              23360  1 thermal
fan                     4868  0
capability              5000  0
commoncap               7296  1 capability
vga16fb                13704  1
vgastate               10368  1 vga16fb
fbcon                  42784  72
tileblit                2816  1 fbcon
font                    8320  1 fbcon
bitblit                 6272  1 fbcon
softcursor              2304  1 bitblit

```
Yup, AGPGART is in there...
```

agpgart                34888  2 nvidia,nvidia_agp

```
...so, anyone know how to prevent a module from loading?

---

### Post by tseliot on 2006-08-08
> **mlalkaka said:**
> **The output of lsmod:**
```

[FONT=Courier New][SIZE=4]Module                  Size  Used by
binfmt_misc            13064  1
rfcomm                 43604  0
l2cap                  28192  5 rfcomm
bluetooth              54084  4 rfcomm,l2cap
ipv6                  286976  22
ppdev                   9668  0
speedstep_lib           4580  0
cpufreq_userspace       6496  0
cpufreq_stats           6688  0
freq_table              4928  1 cpufreq_stats
cpufreq_powersave       1920  0
cpufreq_ondemand        7752  0
cpufreq_conservative     9000  0
video                  16324  0
tc1100_wmi              6884  0
sony_acpi               5580  0
pcc_acpi               12416  0
hotkey                 11492  0
dev_acpi               11236  0
container               4608  0
button                  6704  0
acpi_sbs               20172  0
battery                 9988  1 acpi_sbs
ac                      5220  1 acpi_sbs
i2c_acpi_ec             5120  1 acpi_sbs
nls_iso8859_1           4224  1
nls_cp437               5888  1
vfat                   14496  1
fat                    55548  1 vfat
dm_mod                 63256  1
md_mod                 76052  0
af_packet              24520  2
snd_seq_dummy           3908  0
snd_seq_oss            37216  0
snd_seq_midi            9600  0
snd_seq_midi_event      7520  2 snd_seq_oss,snd_seq_midi
snd_seq                58160  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
lp                     12356  0
snd_mpu401              6792  0
snd_mpu401_uart         8640  1 snd_mpu401
parport_pc             37988  1
analog                 12800  0
snd_intel8x0           35772  1
snd_ac97_codec        100224  1 snd_intel8x0
snd_ac97_bus            2400  1 snd_ac97_codec
parport                39400  3 ppdev,lp,parport_pc
gameport               16776  1 analog
snd_pcm_oss            56448  0
snd_mixer_oss          20544  1 snd_pcm_oss
snd_rawmidi            26848  2 snd_seq_midi,snd_mpu401_uart
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq,snd_rawmidi
snd_pcm                96708  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              26884  2 snd_seq,snd_pcm
pcspkr                  2244  0
snd                    60004  14 snd_seq_oss,snd_seq,snd_mpu401,snd_mpu401_uart,snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_rawmidi,snd_seq_device,snd_pcm,snd_timer
soundcore              10784  1 snd
snd_page_alloc         11304  2 snd_intel8x0,snd_pcm
floppy                 64676  0
8139too                29056  0
nvidia               4552660  12
psmouse                40004  0
serio_raw               7748  0
sis900                 25152  0
mii                     6176  2 8139too,sis900
i2c_sis96x              5860  0
i2c_core               22848  3 i2c_acpi_ec,nvidia,i2c_sis96x
shpchp                 49504  0
pci_hotplug            30788  1 shpchp
sis_agp                 9028  1
agpgart                36784  2 nvidia,sis_agp
tsdev                   8032  0
evdev                  10176  1
joydev                 10432  0
usbhid                 42752  0
ext3                  148104  2
jbd                    65876  1 ext3
ide_generic             1504  0
ohci_hcd               22724  0
usbcore               139076  3 usbhid,ohci_hcd
ide_cd                 35780  0
cdrom                  41408  1 ide_cd
ide_disk               19136  6
sis5513                17320  1
generic                 5124  0
thermal                13768  0
processor              26888  1 thermal
fan                     4836  0
capability              4968  0
commoncap               7328  1 capability
vga16fb                13992  1
vgastate               10208  1 vga16fb
fbcon                  43904  72
tileblit                2784  1 fbcon
font                    8320  1 fbcon
bitblit                 6464  1 fbcon
softcursor              2304  1 bitblit[/SIZE][/FONT]

```

> **Ephemeriis said:**
> Output of lsmod:
```
Module                  Size  Used by
vmvirtualnic            2308  0
vm_bridge               9364  1
vm_main                34224  0
hypervisor             66932  1 vm_main
binfmt_misc            12296  1
rfcomm                 40216  0
l2cap                  26244  5 rfcomm
bluetooth              49892  4 rfcomm,l2cap
ppdev                   9220  0
cpufreq_userspace       4696  0
cpufreq_stats           5636  0
freq_table              4740  1 cpufreq_stats
cpufreq_powersave       1920  0
cpufreq_ondemand        6428  0
cpufreq_conservative     7332  0
video                  16260  0
tc1100_wmi              6916  0
sony_acpi               5644  0
pcc_acpi               12416  0
hotkey                 11556  0
dev_acpi               11140  0
container               4608  0
button                  6672  0
acpi_sbs               19980  0
battery                 9988  1 acpi_sbs
ac                      5252  1 acpi_sbs
i2c_acpi_ec             5120  1 acpi_sbs
dm_mod                 58936  1
ipv6                  265728  6
af_packet              22920  2
md_mod                 72532  0
parport_pc             35780  0
lp                     11844  0
parport                36296  3 ppdev,parport_pc,lp
snd_intel8x0           33692  2
snd_ac97_codec         93088  1 snd_intel8x0
snd_ac97_bus            2304  1 snd_ac97_codec
tsdev                   8000  0
nvidia               4550772  12
pcspkr                  2180  0
snd_pcm_oss            53664  0
snd_mixer_oss          18688  2 snd_pcm_oss
usbhid                 39904  0
snd_pcm                89864  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              25220  1 snd_pcm
shpchp                 45632  0
pci_hotplug            29236  1 shpchp
snd                    55268  8 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              10208  2 snd
snd_page_alloc         10632  2 snd_intel8x0,snd_pcm
rtc                    13492  0
psmouse                36100  0
serio_raw               7300  0
i2c_nforce2             6912  0
forcedeth              30732  0
i2c_core               21904  3 i2c_acpi_ec,nvidia,i2c_nforce2
nvidia_agp              8348  1
agpgart                34888  2 nvidia,nvidia_agp
evdev                   9856  1
ext3                  135688  1
jbd                    58772  1 ext3
ide_generic             1536  0
ehci_hcd               34184  0
ohci_hcd               21892  0
usbcore               130692  4 usbhid,ehci_hcd,ohci_hcd
ide_cd                 33028  0
cdrom                  38560  1 ide_cd
ide_disk               17664  4
generic                 5124  0
amd74xx                15260  0 [permanent]
sata_nv                 9732  0
libata                 78992  1 sata_nv
scsi_mod              139496  1 libata
thermal                13576  0
processor              23360  1 thermal
fan                     4868  0
capability              5000  0
commoncap               7296  1 capability
vga16fb                13704  1
vgastate               10368  1 vga16fb
fbcon                  42784  72
tileblit                2816  1 fbcon
font                    8320  1 fbcon
bitblit                 6272  1 fbcon
softcursor              2304  1 bitblit

```
Yup, AGPGART is in there...
```

agpgart                34888  2 nvidia,nvidia_agp

```
...so, anyone know how to prevent a module from loading?

Type:
```
sudo nano -w /etc/modprobe.d/blacklist
```

Add the following lines to the end of the file:

**Ephemeriis**, you need to add this:
```
blacklist agpgart
blacklist nvidia_agp
```

**mlalkaka**, you need to add this:
```
blacklist agpgart
blacklist sis_agp
```


Then (both of you):

Press CTRL+X to exit (save the file)

Type:

```
sudo nano -w /etc/X11/xorg.conf
```


get to the Section Device of the file add Option "NvAGP" "1" (like in the example below):

```
Section "Device"
Identifier "NVIDIA Corporation NV34 [GeForce FX 5500]"
Driver "nvidia"
BusID "PCI:1:9:0"
[COLOR="Red"]Option "NvAGP" "1"[/COLOR]
```

Set the driver to Nvidia

Press CTRL+X to exit (save the file)


Then log out and restart the Xserver

**NOTE: restarting your computer might be a good idea**

---

### Post by mlalkaka on 2006-08-08
I tried what you suggested, tseliot, but the agpgart module still loaded. Here is the output of lsmod after making the suggested changes and then restarting the computer:
```

[FONT=Courier New][SIZE=3]Module                  Size  Used by
binfmt_misc            13064  1
rfcomm                 43604  0
l2cap                  28192  5 rfcomm
bluetooth              54084  4 rfcomm,l2cap
ppdev                   9668  0
speedstep_lib           4580  0
cpufreq_userspace       6496  0
cpufreq_stats           6688  0
freq_table              4928  1 cpufreq_stats
cpufreq_powersave       1920  0
cpufreq_ondemand        7752  0
cpufreq_conservative     9000  0
video                  16324  0
tc1100_wmi              6884  0
sony_acpi               5580  0
pcc_acpi               12416  0
hotkey                 11492  0
dev_acpi               11236  0
container               4608  0
button                  6704  0
acpi_sbs               20172  0
battery                 9988  1 acpi_sbs
ac                      5220  1 acpi_sbs
i2c_acpi_ec             5120  1 acpi_sbs
nls_iso8859_1           4224  1
nls_cp437               5888  1
vfat                   14496  1
fat                    55548  1 vfat
ipv6                  286976  22
dm_mod                 63256  1
md_mod                 76052  0
af_packet              24520  2
snd_seq_dummy           3908  0
snd_seq_oss            37216  0
snd_seq_midi            9600  0
snd_seq_midi_event      7520  2 snd_seq_oss,snd_seq_midi
snd_seq                58160  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
lp                     12356  0
analog                 12800  0
snd_mpu401              6792  0
snd_mpu401_uart         8640  1 snd_mpu401
gameport               16776  1 analog
snd_rawmidi            26848  2 snd_seq_midi,snd_mpu401_uart
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq,snd_rawmidi
floppy                 64676  0
tsdev                   8032  0
joydev                 10432  0
parport_pc             37988  1
parport                39400  3 ppdev,lp,parport_pc
pcspkr                  2244  0
usbhid                 42752  0
snd_intel8x0           35772  3
snd_ac97_codec        100224  1 snd_intel8x0
snd_ac97_bus            2400  1 snd_ac97_codec
8139too                29056  0
psmouse                40004  0
snd_pcm_oss            56448  0
snd_mixer_oss          20544  1 snd_pcm_oss
serio_raw               7748  0
snd_pcm                96708  4 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              26884  3 snd_seq,snd_pcm
snd                    60004  16 snd_seq_oss,snd_seq,snd_mpu401,snd_mpu401_uart,snd_rawmidi,snd_seq_device,snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              10784  1 snd
nvidia               4552660  12
**[COLOR=Lime]agpgart                36784  1 nvidia[/COLOR]**
sis900                 25152  0
snd_page_alloc         11304  2 snd_intel8x0,snd_pcm
mii                     6176  2 8139too,sis900
i2c_sis96x              5860  0
shpchp                 49504  0
pci_hotplug            30788  1 shpchp
i2c_core               22848  3 i2c_acpi_ec,nvidia,i2c_sis96x
evdev                  10176  1
ext3                  148104  2
jbd                    65876  1 ext3
ide_generic             1504  0
ohci_hcd               22724  0
usbcore               139076  3 usbhid,ohci_hcd
ide_cd                 35780  0
cdrom                  41408  1 ide_cd
ide_disk               19136  6
sis5513                17320  1
generic                 5124  0
thermal                13768  0
processor              26888  1 thermal
fan                     4836  0
capability              4968  0
commoncap               7328  1 capability
vga16fb                13992  1
vgastate               10208  1 vga16fb
fbcon                  43904  72
tileblit                2784  1 fbcon
font                    8320  1 fbcon
bitblit                 6464  1 fbcon
softcursor              2304  1 bitblit[/SIZE][/FONT]

``` 
Any more ideas?

---

### Post by mlalkaka on 2006-08-08
tseliot, it seems that I was wrong. Although the agpgart module is loaded, the nvidia module does, in fact, use its built-in AGP support.

The output of "[FONT=Courier New][SIZE=3]modinfo nvidia[/SIZE][/FONT]" shows that agpgart must be loaded, regardless of whether it gets used:
```

[FONT=Courier New][SIZE=3]filename:       /lib/modules/2.6.15-26-686/volatile/nvidia.ko
license:        NVIDIA
alias:          char-major-195-*
vermagic:       2.6.15-26-686 SMP preempt 686 gcc-4.0
depends:        [COLOR=Lime]**agpgart**[/COLOR],i2c-core
alias:          pci:v000010DEd*sv*sd*bc03sc00i00*
alias:          pci:v000010DEd*sv*sd*bc03sc02i00*
parm:           NVreg_PanelBrightnessLimits:int[/SIZE][/FONT][SIZE=3]
[/SIZE]
``` 
To confirm that the nvidia module is using its built-in AGP support, look at the output of the command "[FONT=Courier New][SIZE=3]cat /proc/driver/nvidia/agp/status[/SIZE][/FONT]":
[B]Before
[/B]```

[FONT=Courier New][SIZE=3]Status:          Enabled
Driver:          [COLOR=Lime]**AGPGART**[/COLOR]
AGP Rate:        4x
Fast Writes:     Disabled
SBA:             Disabled[/SIZE][/FONT]

``` **After**
```

[FONT=Courier New][SIZE=3]Status:          Enabled
Driver:          **[COLOR=Lime]NVIDIA[/COLOR]**
AGP Rate:        4x
Fast Writes:     Disabled
SBA:             Disabled[/SIZE][/FONT]

``` 
So it seems that your instructions worked. Thanks :D.

---

### Post by Ephemeriis on 2006-08-08
Thank you!

AGPGART did not load, NvAGP loaded instead, and I've been playing with 3D applications/games/screensavers for the last half hour with no trouble.

---

### Post by jaybombalous on 2007-10-01
I have this article and the other article u wrote on enabling NvAGP in edgy.

I have checked, double checked and triple checked to make sure I am doing this exactly as stated. Every time I restart a AGPGART backend is being loaded into the kernel, as stated by dmesg.

lsmod tells me what it told Ephemeriis that

```
 agpgart                    2 nvidia, nvidia_agp 
```

agpgart is loaded and nothing I put in the /etc/modprob.d/blacklist is taking effect. 

:( frustrating as hell.

---

### Post by jaybombalous on 2007-10-01
I figured it out :)

I was being stupid, but this was a good learning experience.

I followed another guide that told me I should add this line to /etc/modules

```
nvidia-agp
```

so I did, but what I was unaware of at the time is how the guide was made for a previous version of ubuntu, breezy. 

In other words I think I was trying to load a module and blacklist it all at the same time. If thats even possible then manually loading it takes priority.

---

