---
title: "MCE Remote and a STB"
date: 2009-12-04
forum: Mythbuntu
---

### Post by Chewiesw on 2009-12-04
Hello

Where am I going wrong.....
I can't get my MCE remote to control my STB. I can do it by the commandline but not via the remote.

If I try to change the channel on the remote without any STB remote codes(configs) applied anywhere the blaster does not flash but the OSD displays info for the requested channel obivously the channel doesn't change.

If I put the stb config in either

/usr/share/lirc/remotes/mceusb/lircd.conf.mceusb

or

~/.lirc/mythtv

The remote will not work at all. I am sure I am ver close.

---

### Post by Chewiesw on 2009-12-09
This is driving me freeking insane. I have tried changing the script but still no joy. Myth simply doesn't blast.

```
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Windows Media Center Transceivers/Remotes (all)"
REMOTE_MODULES="lirc_dev lirc_mceusb"
REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/lirc0"
REMOTE_SOCKET=""
REMOTE_LIRCD_CONF="mceusb/lircd.conf.mceusb"
REMOTE_LIRCD_ARGS=""

#Chosen IR Transmitter
TRANSMITTER="Microsoft Windows Media Center V2 (usb) : Dish Receiver"
#TRANSMITTER="Microsoft Windows Media Center V2 (usb) : Dish Receiver"
TRANSMITTER_MODULES="lirc_zilog"
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE="/dev/lirc1"
TRANSMITTER_SOCKET=""
TRANSMITTER_LIRCD_CONF="dish/general.conf"
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


/etc/lirc/lircd.conf

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
include "/usr/share/lirc/remotes/mceusb/lircd.conf.mceusb"

#Configuration for the Microsoft Windows Media Center V2 (usb) : Dish Receiver transmitter:
include "/usr/share/lirc/extras/transmitters/dish/general.conf"


root@pvrbox:~# ls /dev/lir*
/dev/lirc0  /dev/lircd  /dev/lircd1
root@pvrbox:~# 


#!/bin/sh
 REMOTE_NAME=ir
 irsend SET_TRANSMITTERS 1
 for digit in $(echo $1 | sed -e 's/./& /g'); do
         irsend SEND_ONCE $REMOTE_NAME $digit
         sleep 0.4  # note, you may have to tweak the interdigit delay up a bit, depending on your STB model
 done
 irsend SEND_ONCE $REMOTE_NAME OK
 exit 0



root@pvrbox:~# irsend SEND_ONCE IR 1
root@pvrbox:~# irsend -d /dev/lirc0 SEND_ONCE IR 1
irsend: could not connect to socket
irsend: Connection refused
root@pvrbox:~# irsend -d /dev/lircd0 SEND_ONCE IR 1
irsend: could not connect to socket
irsend: No such file or directory
root@pvrbox:~# irsend -d /dev/lircd SEND_ONCE IR 1
root@pvrbox:~# irsend -d /dev/lircd1 SEND_ONCE IR 1
root@pvrbox:~# irsend -d /var/run/lirc/lircd0 SEND_ONCE IR 1
irsend: could not connect to socket
irsend: No such file or directory
root@pvrbox:~# irsend -d /var/run/lirc/lircd SEND_ONCE IR 1
root@pvrbox:~# 

```

---

### Post by dmfrey on 2009-12-09
did you set the channel changer script as the external channel changer when you setup your input connection in mythtv-setup?

---

### Post by Chewiesw on 2009-12-09
Yip under input connections. I also found a way to send any errors with the script to a log file and there AREN"T any !!!

Myth really thinks it is doing what it should. Except that he blaster does not flash and therefore the channels don't change.

---

### Post by sam_d on 2009-12-09
see if this post solves your problem

[http://ubuntuforums.org/showthread.php?p=8464899](http://ubuntuforums.org/showthread.php?p=8464899)

---

### Post by Chewiesw on 2009-12-11
It works!!! Yipppe - I followed the steps in the link and I now have a working remote / stb set up.

---

