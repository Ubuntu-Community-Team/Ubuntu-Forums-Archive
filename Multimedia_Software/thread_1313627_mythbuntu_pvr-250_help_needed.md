---
title: "mythbuntu pvr-250 help needed"
date: 2009-11-03
forum: Multimedia Software
---

### Post by vbsaltydog on 2009-11-03
I loaded the current version of mythbuntu today and overall it is very nice but I am having real problems getting the channel to change. The parameters are:

2Gb Duo CPU
512Mb RAM
80Gb HD
Mythbuntu 9.10
Hauppage PVR-250 capturer card w/remote and ir blaster
DirecTV Set Top Box

I understand that channel changes must be initiated by myth and I setup the ir profile for the Hauppage TV Card option but I cant get the any response from myth from the remote.

This can't really be that hard, can it? The pvr-250 is well supported but there is NO configuration document anywhere.

Any help is appreciated.

---

### Post by vbsaltydog on 2009-11-04
I got the pvr-250 remote working to control the myth menus but now I need to get the ir blaster working for my directv receiver.

```

dmesg | grep eeprom
[    8.688506] tveeprom 0-0050: Hauppauge model 26032, rev C199, serial# 8327984
[    8.688513] tveeprom 0-0050: tuner model is TCL 2002N 5H (idx 99, type 50)
[    8.688518] tveeprom 0-0050: TV standards NTSC(M) (eeprom 0x08)
[    8.688523] tveeprom 0-0050: audio processor is CX25841 (idx 35)
[    8.688529] tveeprom 0-0050: decoder processor is CX25841 (idx 28)
[    8.688533] tveeprom 0-0050: has no radio, has IR receiver, has IR transmitter

```

```

dmesg | grep ivtv
[    8.631813] ivtv: Start initialization, version 1.4.1
[    8.632036] ivtv0: Initializing card 0
[    8.632042] ivtv0: Autodetected Hauppauge card (cx23416 based)
[    8.632150] ivtv 0000:05:04.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    8.688539] ivtv0: Autodetected Hauppauge WinTV PVR-150
[    8.688543] ivtv0: Reopen i2c bus for IR-blaster support
[    9.076127] cx25840 0-0044: cx25841-23 found @ 0x88 (ivtv i2c driver #0)
[    9.156775] tuner 0-0061: chip found @ 0xc2 (ivtv i2c driver #0)
[    9.288297] wm8775 0-001b: chip found @ 0x36 (ivtv i2c driver #0)
[    9.349437] IRQ 16/ivtv0: IRQF_DISABLED is not guaranteed on shared IRQs
[    9.349860] ivtv0: Registered device video0 for encoder MPG (4096 kB)
[    9.349894] ivtv0: Registered device video32 for encoder YUV (2048 kB)
[    9.349928] ivtv0: Registered device vbi0 for encoder VBI (1024 kB)
[    9.349971] ivtv0: Registered device video24 for encoder PCM (320 kB)
[    9.349975] ivtv0: Initialized card: Hauppauge WinTV PVR-150
[    9.350010] ivtv: End initialization
[   10.016022] ivtv 0000:05:04.0: firmware: requesting v4l-cx2341x-enc.fw
[   10.389266] ivtv0: Loaded v4l-cx2341x-enc.fw firmware (376836 bytes)
[   10.592705] ivtv0: Encoder revision: 0x02060039

```

```

vi /etc/lirc/lircd.conf

#This configuration has been automatically generated via
#the Ubuntu LIRC package maintainer scripts.
#
#It includes the default configuration for the remote and/or
#transmitter that you have selected during package installation.
#
#Feel free to add any custom remotes to the configuration
#via additional include directives or below the existing
#Ubuntu include directives from your selected remote and/or
#transmitter.

#Configuration for the Hauppauge TV card remote:
include "/usr/share/lirc/extras/more_remotes/hauppauge/lircd.conf.hauppauge"

```

The /usr/share/lirc/extras/more_remotes/hauppauge/lircd.conf.hauppauge file holds configs for several remotes and is too long to post here.

```

# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Hauppauge TV card"
REMOTE_MODULES="lirc_dev lirc_i2c"
REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/lirc0"
REMOTE_SOCKET=""
REMOTE_LIRCD_CONF="hauppauge/lircd.conf.hauppauge"
REMOTE_LIRCD_ARGS=""

#Enable lircd
START_LIRCD="true"

#Don't start lircmd even if there seems to be a good config file
#START_LIRCMD="false"

#Try to load appropriate kernel modules
LOAD_MODULES="true"

# Default configuration files for your hardware if any
LIRCMD_CONF=""

#Forcing noninteractive reconfiguration
#If lirc is to be reconfigured by an external application
#that doesn't have a debconf frontend available, the noninteractive
#frontend can be invoked and set to parse REMOTE and TRANSMITTER
#It will then populate all other variables without any user input
#If you would like to configure lirc via standard methods, be sure
#to leave this set to "false"
FORCE_NONINTERACTIVE_RECONFIGURATION="false"
START_LIRCMD=""

```

Please help as mythtv isnt worth much if you cant change the channel.

---

