---
title: "LIRC and Dvico remote"
date: 2008-06-10
forum: Multimedia Software
---

### Post by dusty_nz on 2008-06-10
Having Remote issues. Running a Dvico remote which works with the following command line
/usr/sbin/lircd --device=/dev/usb/hiddev0 --driver=dvico -n
and irw can pick up remote signals.

however can't seem to get the hardware.conf to work. 

get the following error
/etc/init.d/lirc restart -verbose
* Stopping remote control daemon(s): LIRC [fail]
* Loading LIRC modules [ OK ]
* Unable to load LIRC kernel modules. Verify your
* selected kernel modules in /etc/lirc/hardware.conf


# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="DViCO USB Remote"
# Arguments which will be used when launching lircd
LIRCD_ARGS=""
#Don't start lircmd even if there seems to be a good config file
START_LIRCMD=false
#Try to load appropriate kernel modules
LOAD_MODULES=true
# Run "lircd --driver=help" for a list of supported drivers.
DRIVER="dvico"
# If DEVICE is set to /dev/lirc and devfs is in use /dev/lirc/0 will be
# automatically used instead
DEVICE="/dev/usb/hiddev0"
MODULES=""
# Default configuration files for your hardware if any
LIRCD_CONF="/etc/lirc/lircd.conf"
LIRCMD_CONF=""

What is the issue?

Paul

---

### Post by daveisfera on 2009-04-17
Did you ever get this to work?

---

