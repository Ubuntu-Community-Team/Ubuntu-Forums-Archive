---
title: "IRSEND  hardware does not support sending"
date: 2011-04-13
forum: Mythbuntu
---

### Post by Chewiesw on 2011-04-13
Hello
I am trying with no luck to get my blaster to work, I keep getting this error message  "hardware does not support sending"

Mythbuntu 10.10 - 0.24 and PVR150 (SMK Manufacturing, Inc. eHome Infrared Receiver)

The remote works fine, I get data back from IRW.

```
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Windows Media Center Transceivers/Remotes (all)"
REMOTE_MODULES="lirc_dev mceusb"
REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/lirc0"
REMOTE_SOCKET=""
REMOTE_LIRCD_CONF="mceusb/lircd.conf.mceusb"
REMOTE_LIRCD_ARGS=""

#Chosen IR Transmitter
TRANSMITTER="Microsoft Windows Media Center V2 (usb) : Direct TV Receiver"
TRANSMITTER_MODULES="lirc_dev mceusb"
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE=""
TRANSMITTER_SOCKET=""
TRANSMITTER_LIRCD_CONF="directtv/general.conf"
TRANSMITTER_LIRCD_ARGS=""

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

I have tried commenting out the transmitter section, I have also removed everything in it.

I know this is some sort of driver issue but I don't know how to solve it.

```
andrew@DVRBOX:~$ ls /dev/lirc*
/dev/lircd
andrew@DVRBOX:~
```$

This is the last bit that I need to get my rig working

---

### Post by rileyp on 2011-07-24
Did you find a solution?
Just trying to sort out ir send with a mceusb transmitter/receiver
cheers rileyp

---

