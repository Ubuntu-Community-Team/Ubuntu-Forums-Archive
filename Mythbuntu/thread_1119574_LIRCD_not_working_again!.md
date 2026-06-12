---
title: "LIRCD not working again!"
date: 2009-04-08
forum: Mythbuntu
---

### Post by Keithamus on 2009-04-08
I never seem to have fun with lirc. I recently reinstalled my mythbox and all the troubles seem to have started again - I have no idea what I did last time to get it working, so here I am...


```

$ sudo lircd -n /etc/lirc/hardware.conf
lircd-0.8.4a[11003]: error in configfile line 10
lircd-0.8.4a[11003]: reading of file '/etc/lirc/hardware.conf' failed
lircd-0.8.4a[11003]: reading of config file failed
lircd-0.8.4a[11003]: lircd(default) ready

```

```

$ cat /etc/lirc/hardware.conf
# /etc/lirc/hardware.conf
#
# Arguments which will be used when launching lircd
#LIRCD_ARGS=""

#Don't start lircmd even if there seems to be a good config file
#START_LIRCMD=false

#Try to load appropriate kernel modules
LOAD_MODULES=true

# Run "lircd --driver=help" for a list of supported drivers.
#DRIVER="dev/input"
# If DEVICE is set to /dev/lirc and devfs is in use /dev/lirc/0 will be
# automatically used instead
DEVICE="/dev/lirc0"
MODULES=""
#LIRCD_ARGS="--device=/dev/lirc0"
#MODULES="lirc_pvr150"

# Default configuration files for your hardware if any
LIRCD_CONF="/etc/lirc/lircd.conf"
LIRCMD_CONF=""

```

If I explicitly call the driver and device (and subsequently call irw):
```

$ sudo lircd -n --device=/dev/lirc0 --driver=devinput
lircd-0.8.4a[11029]: lircd(devinput) ready
lircd-0.8.4a[11029]: accepted new client on /dev/lircd
lircd-0.8.4a[11029]: initializing '/dev/lirc0'

```

```

~$ irw
0000000000010069 00 ArrowLeft NOVA-T500
000000000001006c 00 ArrowDown NOVA-T500
000000000001006a 00 ArrowRight NOVA-T500
0000000000010067 00 ArrowUp NOVA-T500
0000000000010069 00 ArrowLeft NOVA-T500

```

So, as you can see, explicitly calling the device and driver works fine, but the hardware.conf seems to bug out - I can't see why though!

---

### Post by azmyth on 2009-04-08
syntax error

LOAD_MODULES=true

should be

LOAD_MODULES="true"

---

### Post by Keithamus on 2009-04-08
Still get the same error.

If I comment the line out it just says error on line 13, as though it doesn't like anything in the config.

---

### Post by azmyth on 2009-04-08
After looking at your hardware.conf more closely, are you using the h.c from a previous install on a previous rev of MB. My h.c on 8.10 doesn't look the same as my device is called REMOTE_DEVICE for the remote and TRANSMITTER_DEVICE for the blaster.

---

### Post by Keithamus on 2009-04-08
Rewrote my config file to match the style of one I found on the net using the style you mentioned:

```

cerberus@cerberus:~$ cat /etc/lirc/hardware.conf
# /etc/lirc/hardware.conf
#
REMOTE="Hauppauge TV Card"
REMOTE_DEVICE="/dev/lirc0"
REMOTE_DRIVER="devinput"
REMOTE_MODULES="lirc_dev lirc_i2c"
REMOTE_LIRCD_CONF="/etc/lirc/lircd.conf"
REMOTE_LIRCD_ARGS=""

START_LIRCD="true"
LOAD_MODULES="true"

```

Still get error on line 4. This stumps me!

--EDIT--
Ok... scratch that, I just rebooted for an unrelated reason - and everything works fine now. I guess the daemon works differently than calling LIRC from the command line...

---

### Post by azmyth on 2009-04-08
> Ok... scratch that, I just rebooted for an unrelated reason - and everything works fine now. I guess the daemon works differently than calling LIRC from the command line...
Yes, it threw me for awhile too.

---

