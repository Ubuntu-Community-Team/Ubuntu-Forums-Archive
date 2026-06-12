---
title: "LIRC wont start"
date: 2009-07-26
forum: Multimedia Software
---

### Post by capo1949 on 2009-07-26
Hi All

I cannot get my remote to work, as supplied with the hauppauge nova T500.
I have followed the wiki as at
[http://www.mythtv.org/wiki/Hauppauge_WinTV_Nova-T_500_PCI](http://www.mythtv.org/wiki/Hauppauge_WinTV_Nova-T_500_PCI)

 So I established that my system is using event 6 and amended /etc/udev/rules.d/10-local.rules as detailed. Replaced the /etc/lirc/hardware.conf with the sample amending the event to 6

the next step is to start the Lirc daemon and test, it wont start and alarms with
graham@graham-desktop:~$ sudo /etc/init.d/lirc start irw
[sudo] password for graham: 
 * Loading LIRC modules                                                  [ OK ] 
 * Unable to load LIRC kernel modules. Verify your
 * selected kernel modules in /etc/lirc/hardware.conf

here is contents of hardware config

# /etc/lirc/hardware.conf
#
# Arguments which will be used when launching lircd
LIRCD_ARGS=""

#Don't start lircmd even if there seems to be a good config file
#START_LIRCMD=false

#Try to load appropriate kernel modules
LOAD_MODULES=true

# Run "lircd --driver=help" for a list of supported drivers.
DRIVER="dev/input"
# If DEVICE is set to /dev/lirc and devfs is in use /dev/lirc/0 will be
# automatically used instead
DEVICE="/dev/input/event6"
# DEVICE="/dev/input/dvb-ir"
MODULES=""

# Default configuration files for your hardware if any
LIRCD_CONF="/etc/lirc/lircd.conf"
LIRCMD_CONF=""

sudo gedit /etc/udev/rules.d/10-local.rules
KERNEL=="event6", ATTRS{name}=="IR-receiver inside an USB DVB receiver", SYMLINK+="input/dvb-ir"
 
Now I am completely stuck, any help would be appreciated
Graham

---

