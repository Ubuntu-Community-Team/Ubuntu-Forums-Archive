---
title: "lirc not working"
date: 2012-03-18
forum: Multimedia Software
---

### Post by tylerx1040 on 2012-03-18
hi all,

using ubuntu 10.04 on an x86 box i have lately discovered mythtv and it  is great. also connected my "ancient" remote control (pinnacle pctv  rc1124125/00 via a serial/usb converter PL2303) and after some digging  everything worked fine.

however, after the latest kernel upgrade to 2.6.32-39-generic all was  screwed up. so after some fuzzing i made a complete deinstall of mythtv  and freshly installed it and now it is working fine again, but the rc  refuses service.
so i also completely deinstalled lirc, made a fresh install, but no use. irw gives no output and also booting the old kernel is no remedy anymore (besides the fact that this is no reasonable long term strategy anyway).

after discovering that /dev/lirc does not exist i created a link  following the hint in [http://www.mythtv.org/wiki/LIRC](http://www.mythtv.org/wiki/LIRC), but now i got a  "connection refused" when trying to start irw.

this is my hardware.conf:
```
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Pinnacle Systems PCTV (pro) receiver"
REMOTE_MODULES=""
#REMOTE_DRIVER=""
REMOTE_DRIVER="pinsys"
REMOTE_DEVICE=""
REMOTE_SOCKET=""
REMOTE_LIRCD_CONF="pinnacle_systems/lircd.conf.pctv"
REMOTE_LIRCD_ARGS="-d /dev/ttyUSB0"

#Chosen IR Transmitter
TRANSMITTER="Serial Port (UART) : Direct TV Receiver"
TRANSMITTER_MODULES="lirc_dev lirc_serial"
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE="/dev/lirc0"
TRANSMITTER_SOCKET=""
TRANSMITTER_LIRCD_CONF="directtv/general.conf"
#TRANSMITTER_LIRCD_ARGS=""
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
```and lircd.conf
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

#Configuration for the Pinnacle Systems PCTV (pro) receiver remote:
include "/usr/share/lirc/remotes/pinnacle_systems/lircd.conf.pctv"

#Configuration for the Serial Port (UART) : Direct TV Receiver transmitter:
include "/usr/share/lirc/extras/transmitters/directtv/general.conf"
```(/usr/share-stuff unchanged)

this is the output of ls -l /dev/lir*
```
crw-rw---- 1 root root 61, 0 2012-03-18 19:26 /dev/lirc0
lrwxrwxrwx 1 root root    19 2012-03-18 19:26 /dev/lircd -> /var/run/lirc/lircd
lrwxrwxrwx 1 root root    20 2012-03-18 19:26 /dev/lircd1 -> /var/run/lirc/lircd1
```and lsmod | grep lirc
```
lirc_serial            10198  0 
lirc_dev                8884  1 lirc_serial

```

actually it somehow looks like that pinsys-module has vanished. searching the varous lirc-stuff on the net just gave me a considerable amount of frustration.

any ideas?

(and yes, i have renewed the batteries of my rc :mrgreen: )

---

