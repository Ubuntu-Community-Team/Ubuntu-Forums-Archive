---
title: "Mce usb"
date: 2009-10-27
forum: Mythbuntu
---

### Post by srmcatee on 2009-10-27
I have purchased a new hauppage card that came with the MCE remote and IR blaster.  I am trying to get the blaster setup.  I have backed out the remote settings and I am only setting up the Blaster.

In the Mythtv setup I have only selected "Microsoft Windows Media Center V2 (usb): Dish Receiver".

When I do an irsend command I get:
irsend --device=/dev/lircd send_once dish 1 2 3 4

rsend: command failed: send_once dish 1
rsend: hardware does not support sending

I am using the standard out of the box from the config lircd.conf and hardware.conf.

Any ideas?

---

### Post by srmcatee on 2009-10-27
Forgot to mention.  I am on Mythbuntu 9.04.

---

### Post by srmcatee on 2009-10-27
Also,  Here is my hardware config.  I think it has something to do with hardware.

# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="None"
REMOTE_MODULES="lirc_dev lirc_streamzap"
REMOTE_DRIVER=""
REMOTE_DEVICE=""
REMOTE_LIRCD_CONF="streamzap/lircd.conf.streamzap"
REMOTE_LIRCD_ARGS=""

#Chosen IR Transmitter
TRANSMITTER="Microsoft Windows Media Center V2 (usb) : Dish Receiver"
TRANSMITTER_MODULES="lirc_dev lirc_mceusb2"
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE="/dev/lirc0"
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

---

