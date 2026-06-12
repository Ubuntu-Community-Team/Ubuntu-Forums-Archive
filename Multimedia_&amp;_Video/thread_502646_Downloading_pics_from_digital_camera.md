---
title: "Downloading pics from digital camera"
date: 2007-07-16
forum: Multimedia &amp; Video
---

### Post by jdkchem on 2007-07-16
I have a Canon PowerShot A85.  When I connect it to the usb port the camera is recognized and I am given the option to import photos.  I am then given the following error message;

```
An error occurred in the io-library ('Could not claim the USB device'): 
Could not claim interface 0 (Operation not permitted). Make sure no other program 
or kernel module (such as sdc2xx, stv680, spca50x) is using the device and you 
have read/write access to the device.
```

I've blacklisted modules sdc2xx and stv680.  I've also removed the spca5xx module using 
```
sudo modprobe -r spca5xx
```
as I have a creative webcam.  I have unplugged the webcam and rebooted the computer. 

The output of lsmod after doing all of this is;

```
desktop:~$ lsmod
Module                  Size  Used by
binfmt_misc            13448  1 
rfcomm                 42260  0 
l2cap                  27136  5 rfcomm
bluetooth              53476  4 rfcomm,l2cap
ipv6                  272288  10 
cpufreq_userspace       5408  0 
cpufreq_stats           7744  0 
freq_table              6048  1 cpufreq_stats
cpufreq_powersave       2944  0 
cpufreq_ondemand        8876  0 
cpufreq_conservative     8712  0 
video                  17540  0 
tc1100_wmi              8324  0 
sbs                    16804  0 
sony_acpi               6412  0 
pcc_acpi               14080  0 
i2c_ec                  6272  1 sbs
hotkey                 11556  0 
dev_acpi               12292  0 
button                  7952  0 
battery                11652  0 
container               5632  0 
ac                      6788  0 
asus_acpi              17688  0 
af_packet              24584  2 
sbp2                   24584  0 
parport_pc             37796  0 
lp                     12964  0 
parport                39496  2 parport_pc,lp
snd_via82xx            30360  1 
gameport               17160  1 snd_via82xx
snd_ac97_codec         97696  1 snd_via82xx
snd_ac97_bus            3456  1 snd_ac97_codec
snd_mpu401_uart        10240  1 snd_via82xx
snd_pcm_oss            47360  0 
snd_pcm                84612  3 snd_via82xx,snd_ac97_codec,snd_pcm_oss
snd_page_alloc         11400  2 snd_via82xx,snd_pcm
snd_mixer_oss          19584  1 snd_pcm_oss
snd_seq_dummy           4996  0 
snd_seq_oss            36480  0 
sg                     37404  0 
snd_seq_midi            9984  0 
snd_rawmidi            27264  2 snd_mpu401_uart,snd_seq_midi
snd_seq_midi_event      8960  2 snd_seq_oss,snd_seq_midi
snd_seq                59120  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              25348  2 snd_pcm,snd_seq
snd_seq_device          9868  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
tsdev                   9152  0 
snd                    58372  13 snd_via82xx,snd_ac97_codec,snd_mpu401_uart,snd_pcm_oss,snd_pcm,snd_mixer_oss,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              11232  1 snd
usbhid                 45152  0 
via_agp                11264  1 
nvidia               4554836  12 
i2c_viapro              9876  0 
evdev                  11392  1 
pcspkr                  4352  0 
serio_raw               8452  0 
agpgart                34888  2 via_agp,nvidia
rt61                  254596  1 
i2c_core               23424  3 i2c_ec,nvidia,i2c_viapro
psmouse                41352  0 
shpchp                 42144  0 
pci_hotplug            32828  1 shpchp
ext3                  142856  1 
jbd                    62228  1 ext3
ohci1394               37040  0 
ieee1394              306104  2 sbp2,ohci1394
ehci_hcd               34696  0 
uhci_hcd               24968  0 
usbcore               134912  4 usbhid,ehci_hcd,uhci_hcd
ide_generic             2432  0 
ide_cd                 33696  0 
cdrom                  38944  1 ide_cd
via82cxxx              10500  0 [permanent]
generic                 6276  0 
sd_mod                 22656  3 
sata_via               10500  2 
libata                 74892  1 sata_via
scsi_mod              144648  4 sbp2,sg,sd_mod,libata
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
commoncap               8704  1 capability
```

The error still comes up.

Help!!!!  My best guess is that I do not have read/write access to the device.  But I am at a loss as to how to configure the camera.

---

### Post by kahotep on 2007-07-18
I have a different camera than you and I just mounted mine to my Ubuntu system for the first time today.  Although my camera is a Nikon Coolpix 5600, the method is probably the same if your  Canon PowerShot A85 is capable of acting as a USB mass storage device.

**Here is the tail end of my dmesg command:**

```
kahotep@engin05:~$ dmesg
........snip.......
[669790.042080] scsi 5:0:0:0: Direct-Access     NIKON    NIKON DSC E5600  1.00 P
Q: 0 ANSI: 2
[669790.048041] SCSI device sdb: 246016 512-byte hdwr sectors (126 MB)
[669790.051058] sdb: Write Protect is off
[669790.051065] sdb: Mode Sense: 18 00 00 08
[669790.051069] sdb: assuming drive cache: write through
[669790.060034] SCSI device sdb: 246016 512-byte hdwr sectors (126 MB)
[669790.063033] sdb: Write Protect is off
[669790.063038] sdb: Mode Sense: 18 00 00 08
[669790.063042] sdb: assuming drive cache: write through
[669790.063047]  sdb: sdb1
[669790.073076] sd 5:0:0:0: Attached scsi removable disk sdb
[669790.073149] sd 5:0:0:0: Attached scsi generic sg2 type 0
```

So it looks like the device resides at sdb1.  Now I am going to make a directory to mount it to:

```
kahotep@engin05:~$ sudo mkdir /mnt/camera/
Password:
```

Now I am going to mount the directory, as a VFAT file system, to the /mnt/camera directory and then see what's in the directory:

```
kahotep@engin05:~$ sudo mount -t vfat /dev/sdb1 /mnt/camera/
Password:
kahotep@engin05:/mnt/camera$ cd /mnt/camera/
kahotep@engin05:/mnt/camera$ ls
dcim  misc  nikon001.dsc
```

Thats all there is to it.  The same should be true for any other camera that can act as a mass storage device.

Be sure to unmount the camera when you are done:

```
kahotep@engin05:~$ sudo umount  /mnt/camera/
```

---

