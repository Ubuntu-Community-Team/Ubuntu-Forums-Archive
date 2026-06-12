---
title: "Please Help Me With Canon SD600 &amp; Ubuntu Edgy"
date: 2007-03-15
forum: Multimedia &amp; Video
---

### Post by goonies on 2007-03-15
dmesg

```
[17179763.588000] usb 5-6.3: new high speed USB device using ehci_hcd and address 4
[17179763.716000] usb 5-6.3: configuration #1 chosen from 1 choice
```

[[IMG]http://64.72.123.97/thumb/1285170/thumb.png[/IMG]](http://www.zshare.net/image/screenshot-png-qw0.html)[[IMG]http://64.72.123.97/thumb/1285172/thumb.png[/IMG]](http://www.zshare.net/image/screenshot-1-png-7rz.html)


```
*****@oblivion:~$ lsmod
Module                  Size  Used by
isofs                  38076  0 
udf                    89348  0 
binfmt_misc            13448  1 
af_packet              24584  2 
fuse                   43912  4 
lp                     12964  0 
snd_intel8x0           34844  1 
snd_ac97_codec         97696  1 snd_intel8x0
snd_ac97_bus            3456  1 snd_ac97_codec
nvidia               4554836  12 
snd_pcm_oss            47360  0 
tsdev                   9152  0 
e100                   38020  0 
mii                     6912  1 e100
snd_mixer_oss          19584  1 snd_pcm_oss
sg                     37404  0 
i2c_core               23424  1 nvidia
snd_pcm                84612  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              25348  1 snd_pcm
usb_storage            75072  0 
libusual               17040  1 usb_storage
snd                    58372  8 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
serio_raw               8452  0 
parport_pc             37796  1 
parport                39496  2 lp,parport_pc
soundcore              11232  1 snd
hw_random               7320  0 
intel_agp              26012  1 
snd_page_alloc         11400  2 snd_intel8x0,snd_pcm
agpgart                34888  2 nvidia,intel_agp
pcspkr                  4352  0 
shpchp                 42144  0 
pci_hotplug            32828  1 shpchp
floppy                 63044  0 
evdev                  11392  1 
psmouse                41352  0 
ext3                  142856  1 
jbd                    62228  1 ext3
ehci_hcd               34696  0 
uhci_hcd               24968  0 
usbcore               134912  5 usb_storage,libusual,ehci_hcd,uhci_hcd
ide_generic             2432  0 
sata_via               10500  0 
sd_mod                 22656  6 
ata_piix               11780  4 
libata                 74892  2 sata_via,ata_piix
scsi_mod              144648  4 sg,usb_storage,sd_mod,libata
ide_cd                 33696  0 
cdrom                  38944  1 ide_cd
piix                   11780  1 
generic                 6276  0 
thermal                15624  0 
processor              31560  1 thermal
fan                     6020  0 
fbcon                  41504  0 
tileblit                3840  1 fbcon
font                    9344  1 fbcon
bitblit                 7168  1 fbcon
softcursor              3328  1 bitblit
vesafb                  9244  0 
capability              5896  0 
commoncap               8704  1 capabilit
```

```
*****@oblivion:~$ gphoto2 -auto-detect
Abilities for camera             : Canon Digital IXUS 60 (PTP mode)            
Serial port support              : no
USB support                      : yes
Capture choices                  :
                                 : Capture not supported by the driver
Configuration support            : no
Delete selected files on camera  : yes
Delete all files on camera       : no
File preview (thumbnail) support : yes
File upload support              : yes
*** Error (-1: 'Unspecified error') ***       

For debugging messages, please use the --debug option.
Debugging messages may help finding a solution to your problem.
If you intend to send any error or debug messages to the gphoto
developer mailing list <gphoto-devel@lists.sourceforge.net>, please run
gphoto2 as follows:

    env LANG=C gphoto2 --debug -auto-detect

Please make sure there is sufficient quoting around the arguments.
```


can someone help me with this problem =\ I am trying to use my new canon sd600 camera =(

---

### Post by goonies on 2007-03-18
well i fixed my problem by downgrading to the previous versions of libgphoto2-2 and libgphoto2-port0, versions 2.2.1-2ubuntu4

seems like 2.3.0 has some issues

---

