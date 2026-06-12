---
title: "Can´t get HVR-1950 remote running on Karmic"
date: 2009-11-01
forum: Mythbuntu
---

### Post by deadland on 2009-11-01
Dear all,

I can´t get my Hauppauge HVR-1950 work with lirc! 

I ran  "sudo dpkg-reconfigure lirc" and chose the hvr-1300 as remote configuration, which produced the following hardware.conf:

```
 # /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Hauppauge HVR-1300"
REMOTE_MODULES="lirc_dev lirc_i2c"
REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/lirc0"
REMOTE_SOCKET=""
REMOTE_LIRCD_CONF="hauppauge/lircd.conf.hauppauge"
REMOTE_LIRCD_ARGS=""

```

but if I run "irw" or "mode2 -d /dev/lircd" nothing happens. If I open the battery case I get this model-id: "A415 OH/S 1-3".

Additional infos:

```
lsmod | grep lirc
lirc_i2c                7136  0 
lirc_dev               10804  1 lirc_i2c

```

```
mesg | grep lirc
[   16.280348] lirc_dev: IR Remote Control driver registered, major 61 
[12447.886947] lirc_dev: IR Remote Control driver registered, major 61 
[14764.173728] lirc_dev: IR Remote Control driver registered, major 61 
[14986.500859] lirc_dev: IR Remote Control driver registered, major 61 
```

```
mesg | grep pvrusb2
[    9.041222] usbcore: registered new interface driver pvrusb2
[    9.041237] pvrusb2: V4L in-tree version:Hauppauge WinTV-PVR-USB2 MPEG2 Encoder/Tuner
[    9.041246] pvrusb2: Debug mask is 31 (0x1f)
[    9.433638] cx25840 2-0044: cx25843-24 found @ 0x88 (pvrusb2_a)
[    9.434739] pvrusb2: Attached sub-driver cx25840
[   10.000549] tuner 2-0042: chip found @ 0x84 (pvrusb2_a)
[   10.000576] pvrusb2: Attached sub-driver tuner
[   13.414902] pvrusb2: Supported video standard(s) reported available in hardware: PAL-M/N/Nc;NTSC-M/Mj/Mk;ATSC-8VSB/16VSB
[   13.414920] pvrusb2: Mapping standards mask=0x300b700 (PAL-M/N/Nc;NTSC-M/Mj/Mk;ATSC-8VSB/16VSB)
[   13.414930] pvrusb2: Setting up 6 unique standard(s)
[   13.414941] pvrusb2: Set up standard idx=0 name=PAL-M
[   13.414949] pvrusb2: Set up standard idx=1 name=PAL-N
[   13.414957] pvrusb2: Set up standard idx=2 name=PAL-Nc
[   13.414966] pvrusb2: Set up standard idx=3 name=NTSC-M
[   13.414974] pvrusb2: Set up standard idx=4 name=NTSC-Mj
[   13.414982] pvrusb2: Set up standard idx=5 name=NTSC-Mk
[   13.414992] pvrusb2: Initial video standard (determined by device type): NTSC-M
[   13.415028] pvrusb2: Device initialization completed successfully.
[   13.415218] pvrusb2: registered device video1 [mpeg]
[   13.415230] DVB: registering new adapter (pvrusb2-dvb)

```

It would be great if someone could provide me his working hardware.conf or any other advice.

Thanks in advanced

---

