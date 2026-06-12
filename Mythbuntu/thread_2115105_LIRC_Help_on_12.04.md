---
title: "LIRC Help on 12.04"
date: 2013-02-11
forum: Mythbuntu
---

### Post by AppleTech on 2013-02-11
Hi... I'm 99% done with my mythbuntu box.  I've gotten everything working (including my MCE remote) with the exception of IR Blasting to control my STB.  I've followed along with [this thread]("http://ubuntuforums.org/showthread.php?t=742672&highlight=lirc&page=2") (realizing that I don't have a Hauppage unit, but the procedures are still sound save for the configuration files).  I'm using the IRBlaster.info unit.  I've verified my Serial port is enabled in the BIOS and confirmed the IRQ and address.

Anyway, my issue is not with the ability of the system's recognition of the serial IR transmitter... I'm able to use irsend to send commands and get no errors back.  I've used a camera (that I can confirm sees IR signals with other remotes) and the IR blaster is not emitting any signal.  Is it possible for lirc to be configured improperly and irsend to not throw an error?  Any help appreciated!

/etc/lirc/lircd.conf:
```
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

#Configuration for the Windows Media Center Transceivers/Remotes (all) remote:
include "/usr/share/lirc/extras/transmitters/motorola/dctxxxx.conf"
include "/usr/share/lirc/remotes/mceusb/lircd.conf.mceusb"
```

/etc/lirc/hardware.conf
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
TRANSMITTER="DCT2000"
TRANSMITTER_MODULES="lirc_dev lirc_serial"
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE="/dev/lirc1"
TRANSMITTER_SOCKET="motorola/dctxxxx.conf"
TRANSMITTER_LIRCD_CONF=""
TRANSMITTER_LIRCD_ARGS=""

#Enable lircd
START_LIRCD="true"

#Don't start lircmd even if there seems to be a good config file
#START_LIRCMD="false"

#Try to load appropriate kernel modules
LOAD_MODULES="true"

# Default configuration files for your hardware if any
LIRCMD_CONF=""

```

/etc/modprobe.d/lirc-serial.conf
```
#COM1 equivalent, /dev/ttyS0
options lirc_serial irq=4 io=0x3f8
#COM2 equivalent, /dev/ttyS1
#options lirc_serial irq=3 io=0x2f8
```

---

### Post by AppleTech on 2013-02-11
SOLVED - did a complete uninstall and reinstall of lirc.  Went through the config util again and selected my MCE remote and Serial transmitter.  Played around with irsend and had to use -d to select lircd1 instead of lircd.  I guess irsend doesn't automatically determine which one sends.

Looking good!  Now just to get the channel change scripts up and running!

---

### Post by hansdown on 2013-02-12
> **AppleTech said:**
> SOLVED - did a complete uninstall and reinstall of lirc.  Went through the config util again and selected my MCE remote and Serial transmitter.  Played around with irsend and had to use -d to select lircd1 instead of lircd.  I guess irsend doesn't automatically determine which one sends.

Looking good!  Now just to get the channel change scripts up and running!

Glad you got it working, AppleTech.

Please post back, if you have other probs.

---

