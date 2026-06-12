---
title: "LIRC isn't working at all"
date: 2007-04-17
forum: Multimedia &amp; Video
---

### Post by wishmechaos on 2007-04-17
Hi all. I'm using Feisty Beta (though release is tomorrow, so I guess it's not so beta anymore :)), and I can't get my remote control to work.

I have a really old Leadtek Winview 601 PCI card (bt848), which doesn't get autodetected by bttv, but with the correct options in /etc/modprobe.d/bttv (card=17 tuner=2) it works perfectly with TVtime (I get no audio with motv, but that's a different animal). 

I followed the instructions at [https://help.ubuntu.com/community/Install_Lirc_Feisty](https://help.ubuntu.com/community/Install_Lirc_Feisty) and everything goes without a hitch. The lirc_gpio module is loaded, lircd executes correctly, but irw doesn't receive anything.

dmesg says
```
[197640.085104] The bttv_* interface is obsolete and will go away,
[197640.085107] please use the new, sysfs based interface instead.
[197640.085113] lirc_gpio (-1): card type 0x11, id 0x0
[197640.087086] lirc_dev: lirc_register_plugin: sample_rate: 0
[197640.087134] lirc_gpio (0): driver registered

```

running
```
$ sudo lircd --nodaemon
lircd-0.8.2-CVS[21268]: lircd(userspace) ready
lircd-0.8.2-CVS[21268]: accepted new client on /dev/lircd # press some buttons, nothing happens
lircd-0.8.2-CVS[21268]: removed client #^C in irw
```
doesn't seem to tell me much

I know I have a correct lircd.conf in place, and hardware.conf seems right

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
DRIVER=""
# If DEVICE is set to /dev/lirc and devfs is in use /dev/lirc/0 will be
# automatically used instead
DEVICE=""
MODULES="lirc_gpio"

# Default configuration files for your hardware if any
LIRCD_CONF=""
LIRCMD_CONF=""
```

I know the remote works in Windows with Girder, so it's not a hardware problem. I read some stuff about the ir-common module, but documentation is scarce. I really don't know how to debug this, so any help would be really appreciated. Thanks in advance.

---

### Post by wishmechaos on 2007-05-25
bump... anyone, please? I still haven't been able to solve this.

---

