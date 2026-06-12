---
title: "lirc sending failed after reboot"
date: 2013-04-21
forum: Mythbuntu
---

### Post by AppleTech on 2013-04-21
Had to reboot my box today for the first time in many moons... after reboot, my IR blaster (serial) is no longer working in mythtv... the IR receiver seems to be fully functional.  When I ran the command manually from my channelchange.sh, here's the output:

```
root@mythbuntu:/etc/lirc# irsend -d /var/run/lirc/lircd1 SEND_ONCE DCT2000 1irsend: command failed: SEND_ONCE DCT2000 1
irsend: hardware does not support sending
```

I've tried removing and re-installing LIRC, as well as reconfiguring, still getting the same errors.

Here's my /etc/lirc/lircd.conf:
```
#This configuration has been automatically generated via#the Ubuntu LIRC package maintainer scripts.
#
#It includes the default configuration for the remote and/or
#transmitter that you have selected during package installation.
#
#Feel free to add any custom remotes to the configuration
#via additional include directives or below the existing
#Ubuntu include directives from your selected remote and/or
#transmitter.


#Configuration for the Serial Port (UART) : Motorola Cable box transmitter:
include "/usr/share/lirc/extras/transmitters/motorola/dctxxxx.conf"


#Configuration for the Windows Media Center Transceivers/Remotes (all) remote:
include "/usr/share/lirc/remotes/mceusb/lircd.conf.mceusb"
```

Here's my hardware.conf:
```
#Chosen Remote ControlREMOTE="Windows Media Center Transceivers/Remotes (all)"
REMOTE_MODULES="lirc_dev mceusb"
REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/lirc0"
REMOTE_SOCKET=""
REMOTE_LIRCD_CONF="mceusb/lircd.conf.mceusb"
REMOTE_LIRCD_ARGS=""


#Chosen IR Transmitter
TRANSMITTER="Serial Port (UART) : Motorola Cable box"
TRANSMITTER_MODULES="lirc_dev lirc_serial"
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE="/dev/lirc1"
TRANSMITTER_SOCKET=""
TRANSMITTER_LIRCD_CONF="motorola/dctxxxx.conf"
TRANSMITTER_LIRCD_ARGS=""
```

Any help would be greatly appreciated!

---

### Post by AppleTech on 2013-04-21
Well I got it fixed... it seems like the following lines must have somehow gotten changed in my hardware.conf... changing the settings back to these works:

TRANSMITTER="DCT2000"


LOAD_MODULES="true"

---

