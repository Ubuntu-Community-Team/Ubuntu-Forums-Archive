---
title: "newest challenge for me and Linux: TV tuner via USB"
date: 2006-08-04
forum: Multimedia &amp; Video
---

### Post by louis_nichols on 2006-08-04
hi!

A couple of weeks ago I bought a tv tuner for my girlfriend, a Pixelview PlayTV 400 USB. Through a chain of circumstances, it is still in my possesion and I'd actually like to be able to use it under Linux.

I googled a bit and got a hint that the driver [usbvision]("http://usbvision.sourceforge.net/") should do the trick. I downloaded it, but don't seem able to install it. Here's what I get:```
myself@home:~/downloads/^src/tvtuner stuff/usbvision/src$ make
make -C /lib/modules/2.6.15-26-k7/build SUBDIRS=/home/myself/downloads/^src/tvtuner stuff/usbvision/src modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.15-26-k7'
make[1]: *** No rule to make target `stuff/usbvision/src'.  Stop.
make[1]: Leaving directory `/usr/src/linux-headers-2.6.15-26-k7'
make: *** [default] Error 2
```

I have linux-source and linux-headers installed. Any ideas?

---

### Post by patrick295767 on 2006-08-04
first, does it show up when you unplug / plug it in : 
```
sudo lsusb 
```?
& ```
sudo dmesg
```

---

### Post by louis_nichols on 2006-08-05
lsusb shows it as

```
Bus 001 Device 004: ID 1554:4933 Prolink Microsystems Corp.
```

dmesg shows:

```
[17180479.380000] usb 1-6: new high speed USB device using ehci_hcd and address 4
[17180480.000000] usbcore: registered new driver snd-usb-audio
```

In the meantime, I managed to compile the usbvision module, also. Now, lsmod says:

```
myself@home:~$ lsmod
Module                  Size  Used by
snd_usb_audio          84032  0
snd_usb_lib            18432  1 snd_usb_audio
snd_hwdep              10272  1 snd_usb_audio
ppdev                  10052  0
cpufreq_powersave       2240  0
cpufreq_stats           6912  0
cpufreq_userspace       6816  0
cpufreq_ondemand        8104  0
cpufreq_conservative     9256  0
freq_table              5152  1 cpufreq_stats
tc1100_wmi              7172  0
video                  16644  0
acpi_sbs               20556  0
battery                10308  1 acpi_sbs
i2c_acpi_ec             5440  1 acpi_sbs
container               4928  0
button                  6992  0
pcc_acpi               12736  0
sony_acpi               5900  0
ac                      5508  1 acpi_sbs
dev_acpi               11652  0
hotkey                 11812  0
usbvision              83556  0
i2c_algo_usb            5316  1 usbvision
nls_cp437               6208  2
ntfs                  114288  2
ext3                  148296  1
jbd                    65684  1 ext3
ipv6                  287456  22
md_mod                 76244  0
af_packet              25224  2
lp                     12612  0
snd_mpu401              7112  0
snd_mpu401_uart         8896  1 snd_mpu401
analog                 12960  0
gameport               17032  1 analog
snd_rawmidi            27552  2 snd_usb_lib,snd_mpu401_uart
snd_seq_device          9548  1 snd_rawmidi
parport_pc             38340  1
parport                39560  3 ppdev,lp,parport_pc
nvidia               4553748  12
spca5xx               653072  0
videodev               10368  2 usbvision,spca5xx
floppy                 65924  0
snd_intel8x0           35804  5
snd_ac97_codec         99296  1 snd_intel8x0
snd_ac97_bus            2688  1 snd_ac97_codec
snd_pcm_oss            56352  0
snd_mixer_oss          20800  3 snd_pcm_oss
snd_pcm                96772  5 snd_usb_audio,snd_intel8x0,snd_ac97_codec,snd_pcm_oss
psmouse                40132  0
serio_raw               8132  0
snd_timer              27204  2 snd_pcm
3c59x                  48040  0
snd                    60068  16 snd_usb_audio,snd_hwdep,snd_mpu401,snd_mpu401_uart,snd_rawmidi,snd_seq_device,snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
pcspkr                  2564  0
mii                     6528  1 3c59x
i2c_nforce2             7360  0
soundcore              11040  3 snd
snd_page_alloc         11592  2 snd_intel8x0,snd_pcm
i2c_core               23168  4 i2c_acpi_ec,i2c_algo_usb,nvidia,i2c_nforce2
forcedeth              33164  0
shpchp                 49312  0
pci_hotplug            30916  1 shpchp
nvidia_agp              9116  1
agpgart                37072  2 nvidia,nvidia_agp
tsdev                   8320  0
evdev                  10432  1
usbhid                 42912  0
reiserfs              284400  2
dm_mod                 63640  5
ide_generic             1792  0
ehci_hcd               36104  0
ohci_hcd               22788  0
usbcore               138948  8 snd_usb_audio,snd_usb_lib,usbvision,spca5xx,usbhid,ehci_hcd,ohci_hcd
ide_cd                 36228  0
cdrom                  41504  1 ide_cd
ide_disk               19520  5
sata_nv                10372  0
libata                 84176  1 sata_nv
scsi_mod              145736  1 libata
generic                 5444  0
amd74xx                15324  0 [permanent]
thermal                14088  0
processor              27208  1 thermal
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

Still doesn't work. I googled around a bit more and I actually think it  might not work at all, from what I read. Unfortunatelly, I'm not a programmer, or I would start programming the thing myself

---

### Post by patrick295767 on 2006-08-07
> **louis_nichols said:**
> lsusb shows it as

```
Bus 001 Device 004: ID 1554:4933 Prolink Microsystems Corp.
```

dmesg shows:

```
[17180479.380000] usb 1-6: new high speed USB device using ehci_hcd and address 4
[17180480.000000] usbcore: registered new driver snd-usb-audio
```

In the meantime, I managed to compile the usbvision module, also. Now, lsmod says:

```
myself@home:~$ lsmod
Module                  Size  Used by
snd_usb_audio          84032  0
snd_usb_lib            18432  1 snd_usb_audio
snd_hwdep              10272  1 snd_usb_audio
ppdev                  10052  0
cpufreq_powersave       2240  0
cpufreq_stats           6912  0
cpufreq_userspace       6816  0
cpufreq_ondemand        8104  0
cpufreq_conservative     9256  0
freq_table              5152  1 cpufreq_stats
tc1100_wmi              7172  0
video                  16644  0
acpi_sbs               20556  0
battery                10308  1 acpi_sbs
i2c_acpi_ec             5440  1 acpi_sbs
container               4928  0
button                  6992  0
pcc_acpi               12736  0
sony_acpi               5900  0
ac                      5508  1 acpi_sbs
dev_acpi               11652  0
hotkey                 11812  0
usbvision              83556  0
i2c_algo_usb            5316  1 usbvision
nls_cp437               6208  2
ntfs                  114288  2
ext3                  148296  1
jbd                    65684  1 ext3
ipv6                  287456  22
md_mod                 76244  0
af_packet              25224  2
lp                     12612  0
snd_mpu401              7112  0
snd_mpu401_uart         8896  1 snd_mpu401
analog                 12960  0
gameport               17032  1 analog
snd_rawmidi            27552  2 snd_usb_lib,snd_mpu401_uart
snd_seq_device          9548  1 snd_rawmidi
parport_pc             38340  1
parport                39560  3 ppdev,lp,parport_pc
nvidia               4553748  12
spca5xx               653072  0
videodev               10368  2 usbvision,spca5xx
floppy                 65924  0
snd_intel8x0           35804  5
snd_ac97_codec         99296  1 snd_intel8x0
snd_ac97_bus            2688  1 snd_ac97_codec
snd_pcm_oss            56352  0
snd_mixer_oss          20800  3 snd_pcm_oss
snd_pcm                96772  5 snd_usb_audio,snd_intel8x0,snd_ac97_codec,snd_pcm_oss
psmouse                40132  0
serio_raw               8132  0
snd_timer              27204  2 snd_pcm
3c59x                  48040  0
snd                    60068  16 snd_usb_audio,snd_hwdep,snd_mpu401,snd_mpu401_uart,snd_rawmidi,snd_seq_device,snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
pcspkr                  2564  0
mii                     6528  1 3c59x
i2c_nforce2             7360  0
soundcore              11040  3 snd
snd_page_alloc         11592  2 snd_intel8x0,snd_pcm
i2c_core               23168  4 i2c_acpi_ec,i2c_algo_usb,nvidia,i2c_nforce2
forcedeth              33164  0
shpchp                 49312  0
pci_hotplug            30916  1 shpchp
nvidia_agp              9116  1
agpgart                37072  2 nvidia,nvidia_agp
tsdev                   8320  0
evdev                  10432  1
usbhid                 42912  0
reiserfs              284400  2
dm_mod                 63640  5
ide_generic             1792  0
ehci_hcd               36104  0
ohci_hcd               22788  0
usbcore               138948  8 snd_usb_audio,snd_usb_lib,usbvision,spca5xx,usbhid,ehci_hcd,ohci_hcd
ide_cd                 36228  0
cdrom                  41504  1 ide_cd
ide_disk               19520  5
sata_nv                10372  0
libata                 84176  1 sata_nv
scsi_mod              145736  1 libata
generic                 5444  0
amd74xx                15324  0 [permanent]
thermal                14088  0
processor              27208  1 thermal
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

Still doesn't work. I googled around a bit more and I actually think it  might not work at all, from what I read. Unfortunatelly, I'm not a programmer, or I would start programming the thing myself

It's then on very good way. I have also to install my USB tuner. I will work on it very soon. I subscribed to this thread. I will give a try next week. What's the programs that you might use to make use of your TV tuner hardware, that you might propose ?
  
Looks like you have it almost workign, permissions should be okay too before trying...
Do know much, I didnt yet installed my usb tv tuner... 
 
Let me know about your progresses !

Greetings

---

### Post by louis_nichols on 2006-08-07
> **patrick295767 said:**
> It's then on very good way. I have also to install my USB tuner. I will work on it very soon. I subscribed to this thread. I will give a try next week. What's the programs that you might use to make use of your TV tuner hardware, that you might propose ?
  
Looks like you have it almost workign, permissions should be okay too before trying...
Do know much, I didnt yet installed my usb tv tuner... 
 
Let me know about your progresses !

Greetings


I'm afraid I've given up.

compiling the driver worked in the end, and loading the module is easy (I loaded it with modprobe, not automatically), but it has to be the right driver, and this one isn't. ](*,)  at least, not for my tuner. there isn't a driver around for it, I'm quite certain now, after quite some googling :( . And I wouldn't know where to start coding one.

hope you have better luck with yours.

---

