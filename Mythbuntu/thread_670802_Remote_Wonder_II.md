---
title: "Remote Wonder II"
date: 2008-01-17
forum: Mythbuntu
---

### Post by Xenner on 2008-01-17
I have been unable to get this remote working in mythbuntu, it works fine if i run 

sudo lircd -d /dev/lirc0 /etc/lirc/lircd.conf

but on boot it doesn't work at all :confused:

any help?

---

### Post by Xenner on 2008-01-20
anyone?

---

### Post by superm1 on 2008-01-21
Post your /etc/lirc/hardware.conf.

This is the file that is sourced via the init script.

Also, does it start if you do this:

```
sudo /etc/init.d/lirc restart
```

If so, this likely means that there is something going on with the order things are loading (possibly a module order issue or a blacklist issue)

---

### Post by Xenner on 2008-01-21
```

# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="ATI/NVidia X10 RF (userspace)"

# Arguments which will be used when launching lircd
LIRCD_ARGS="-d /dev/lirc0 /etc/lirc/lircd.conf"

#Don't start lircmd even if there seems to be a good config file
#START_LIRCMD=false

#Try to load appropriate kernel modules
LOAD_MODULES=true

# Run "lircd --driver=help" for a list of supported drivers.
DRIVER="atilibusb"
# If DEVICE is set to /dev/lirc and devfs is in use /dev/lirc/0 will be
# automatically used instead
DEVICE="/dev/lirc0"
MODULES=""

# Default configuration files for your hardware if any
LIRCD_CONF="/etc/lirc/lircd.conf"
LIRCMD_CONF=""

```

sudo /etc/init.d/lirc does not work because i had altered that script when i was trying to get it to work. can someone post the original file as well?

---

### Post by superm1 on 2008-01-21
> **Xenner said:**
> ```

# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="ATI/NVidia X10 RF (userspace)"

# Arguments which will be used when launching lircd
LIRCD_ARGS="-d /dev/lirc0 /etc/lirc/lircd.conf"

#Don't start lircmd even if there seems to be a good config file
#START_LIRCMD=false

#Try to load appropriate kernel modules
LOAD_MODULES=true

# Run "lircd --driver=help" for a list of supported drivers.
DRIVER="atilibusb"
# If DEVICE is set to /dev/lirc and devfs is in use /dev/lirc/0 will be
# automatically used instead
DEVICE="/dev/lirc0"
MODULES=""

# Default configuration files for your hardware if any
LIRCD_CONF="/etc/lirc/lircd.conf"
LIRCMD_CONF=""

```sudo /etc/init.d/lirc does not work because i had altered that script when i was trying to get it to work. can someone post the original file as well?
You can obtain the original by purging lirc and reinstalling or by grabbing it from the deb (extracted).

Odds are there is your issue, if you can't start it that way.  That is the same way it is started when the PC is turned on.

As for that file, don't specify LIRCD_ARGS like that. (it's not necessary, as they get built from other parameters in that file)

---

### Post by Xenner on 2008-01-21
it is still not working, but once again works if i do

lircd -d /dev/lirc0 /etc/lirc/lircd.conf

something with the order that these processes are starting maybe?

---

### Post by Xenner on 2008-01-21
Fixed by removing all arguments in the DEVICE line.

---

