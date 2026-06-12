---
title: "lirc problem"
date: 2009-10-23
forum: Mythbuntu
---

### Post by prunesquallor on 2009-10-23
In the process of installing mythbuntu 9.04. All is fine except for the remote control. If I test the remote by entering:

```
sudo /etc/init.d/lirc start

```
I get the following:

 Starting remote control daemon(s) : LIRC   [fail] 

However all is well if I enter:

```
sudo lircd -n --driver=dev/input --device=/dev/input/event6
```

The contents of my hardware.conf is:

```
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
```


Any ideas why one will work  and the other will not?

---

### Post by bsntech on 2009-10-23
sudo dpkg-reconfigure lirc

Ensure you choose the correct transmitter (kind of remote used) and then on the next page, choose the IR device you will control if using that to control a set-top box.

---

### Post by azmyth on 2009-10-23
When lirc starts from the command line, it looks for the config file in /etc/lircd.conf. You've specified /etc/lirc/lircd.conf in your hardware.conf. Do you have the files in the correct locations.

---

