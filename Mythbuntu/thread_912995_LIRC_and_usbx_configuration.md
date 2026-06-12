---
title: "LIRC and usbx configuration"
date: 2008-09-07
forum: Mythbuntu
---

### Post by ruister on 2008-09-07
Hi,

I've had Ubuntu(8.04) running for a while on my laptop (Toshiba satellite) and yesterday I tried hooking up a ADS-Tech usb IR Blaster which is listed in the support hardware list for LIRC using the usbx driver.  Using dmesg I can see the device coming up on /dev/ttyUSB0. I am not sure how I need to setup the hardware.conf file to make this thing work.
I tried a few different combinations and now I can start the LIRC daemon and it stays up and I can start irw without any problems.  But it does not provide any output.  I tried mode2 and it tells me that it cannot find the device.  I tried the command sequence bellow and as you can see the results are not any better.

>$ ls -asl /dev/lirc*
0 srw-rw-rw- 1 root root 0 2008-09-07 10:08 /dev/lircd
>$ sudo mode2 -d /dev/lircd
mode2: error opening /dev/lircd
mode2: No such device or address

I pasted my hardware.conf below.  Any suggestions?  Any help would be greatly appreciated.
-Rui

# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="USB-UIRT"
REMOTE_MODULES=""
REMOTE_DRIVER="usbx"
REMOTE_DEVICE=""
REMOTE_LIRCD_CONF=""
REMOTE_LIRCD_ARGS="-d /dev/ttyUSB0"

#Chosen IR Transmitter
TRANSMITTER="USB-UIRT2 : Direct TV Receiver"
TRANSMITTER_MODULES=""
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE=""
TRANSMITTER_LIRCD_CONF="directtv/general.conf"
TRANSMITTER_LIRCD_ARGS=""

DRIVER="usb_uirt_raw"

#Enable lircd
START_LIRCD="true"

#Don't start lircmd even if there seems to be a good config file
#START_LIRCMD="false"

#Try to load appropriate kernel modules
LOAD_MODULES="false"

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

