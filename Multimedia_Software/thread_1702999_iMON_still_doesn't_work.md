---
title: "iMON still doesn't work"
date: 2011-03-08
forum: Multimedia Software
---

### Post by tachikoma0023 on 2011-03-08
I've been trying to get the iMON receiver to work for the past few weeks, following every guide I could find, all without success.

I have lirc configured to use the devinput device and have made sure that all of the configuration settings are correct. I've even added a rule to keep hal from claiming it. None of this has managed to get it to work. irw outputs nothing. Same with evtest.

My goal is to eventually use an MCE (rc6) remote with the receiver for XBMC.

I've got a soundgraph imon 15c2:0038 device with the LCD. I have the LCD communicating correctly, but not the receiver.

Does anyone have any idea what I need to do to get this to work? Below are all the details i think are necessary. Let me know if you want me to try anything or need any more info.

Thanks,
Cory

lsusb
```

Bus 008 Device 002: ID 046d:c52e Logitech, Inc. 
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 15c2:0038 SoundGraph Inc. GD01 MX VFD Display/IR Receiver
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```ls -Al /dev/input/by-id
```

total 0
lrwxrwxrwx 1 root root 9 2011-03-08 13:22 usb-15c2_0038-event-mouse -> ../event5
lrwxrwxrwx 1 root root 9 2011-03-08 13:22 usb-15c2_0038-mouse -> ../mouse1
lrwxrwxrwx 1 root root 9 2011-03-08 13:22 usb-Logitech_USB_Receiver-event-kbd -> ../event3
lrwxrwxrwx 1 root root 9 2011-03-08 13:22 usb-Logitech_USB_Receiver-event-mouse -> ../event4
lrwxrwxrwx 1 root root 9 2011-03-08 13:22 usb-Logitech_USB_Receiver-mouse -> ../mouse0

```/etc/lirc/hardware.conf
```

# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Linux input layer (/dev/input/eventX)"
REMOTE_MODULES=""
REMOTE_DRIVER="devinput"
REMOTE_DEVICE="/dev/input/event5"
REMOTE_SOCKET=""
REMOTE_LIRCD_CONF="devinput/lircd.conf.devinput"
REMOTE_LIRCD_ARGS=""

#Chosen IR Transmitter
TRANSMITTER="None"
TRANSMITTER_MODULES=""
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE=""
TRANSMITTER_SOCKET=""
TRANSMITTER_LIRCD_CONF=""
TRANSMITTER_LIRCD_ARGS=""

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

```

---

