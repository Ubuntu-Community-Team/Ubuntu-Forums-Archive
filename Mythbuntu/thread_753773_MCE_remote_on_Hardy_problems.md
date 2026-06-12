---
title: "MCE remote on Hardy problems"
date: 2008-04-13
forum: Mythbuntu
---

### Post by mekis on 2008-04-13
I am using the new Microsft MCE remote marked RC6 and I&#8217;ve followed this guide  [https://help.ubuntu.com/community/InstallLirc/Hardy](https://help.ubuntu.com/community/InstallLirc/Hardy). Tried it with irw and it works. Then I used mythbuntu-lirc-generator to create ~/.mythtv.lircrc, restarted lirc and tried the remote but no luck with MythTV. 

After that I tried Mythbuntu Control Center, Infrared Devices, selecting Windows Media Center Remotes (new version Philips et al.) and when I start MythTV frontend the remote works but only until next reboot!

What am I missing?

---

### Post by [Psyduck] on 2008-04-30
Did you manage to solve this issue?

I had the exact same behaviour. 
After running MCC and selecting the MCE Remote everything worked fine until next reboot.

I have an Antec Fusion case and after reboot the lirc_imon module were loaded as well and /dev/lirc0 now "pointed" to the lirc_imon module instead of the lirc_mceusb2.

It should be rather easy to see if you have the same issue.

-Run MCC selecting the MCE remote. 
-Make sure the MCE Remote is working and run "ls -la /dev/lirc*", you should see something like this:
```
.... /dev/lirc0
.... /dev/lircd
```

- Reboot
- Run "ls -la /dev/lirc*" again. If the ouput is:
```
.... /dev/lirc0
.... /dev/lirc1
.... /dev/lircd
```
then you have to change hardware.conf to use /dev/lirc1 instead of /dev/lirc0

---

### Post by superm1 on 2008-04-30
> **'[Psyduck] said:**
> Did you manage to solve this issue?

I had the exact same behaviour. 
After running MCC and selecting the MCE Remote everything worked fine until next reboot.

I have an Antec Fusion case and after reboot the lirc_imon module were loaded as well and /dev/lirc0 now "pointed" to the lirc_imon module instead of the lirc_mceusb2.

It should be rather easy to see if you have the same issue.

-Run MCC selecting the MCE remote. 
-Make sure the MCE Remote is working and run "ls -la /dev/lirc*", you should see something like this:
```
.... /dev/lirc0
.... /dev/lircd
```- Reboot
- Run "ls -la /dev/lirc*" again. If the ouput is:
```
.... /dev/lirc0
.... /dev/lirc1
.... /dev/lircd
```then you have to change hardware.conf to use /dev/lirc1 instead of /dev/lirc0
If they start to constantly flip, then you will need to explicitly list the order you want them to load in /etc/modules.

---

### Post by KillerKiwi on 2008-05-01
or write a udev rule...

---

### Post by [Psyduck] on 2008-05-02
They don't constantly flip. 

During configuration of lirc MCC unloads all lirc-modules and only reloads the one configured (in this case lirc_mceusb2).
After reboot the system "discoveres" the unconfigured hardware and loads the module lirc_imon first.

I think this should be considered as a minor bug in MCC?

---

### Post by axelsvag on 2008-05-02
After upgrade to 8.04something broke  in my installation also 
when I try 
ls -la /dev/lirc*
I get 
crw-rw---- 1 root root 61, 0 2008-05-02 15:47 /dev/lirc0
crw-rw---- 1 root root 61, 1 2008-05-02 15:47 /dev/lirc1
srw-rw-rw- 1 root root     0 2008-05-02 15:47 /dev/lircd
srw-rw-rw- 1 root root     0 2008-05-02 15:47 /dev/lircd1
lrwxrwxrwx 1 root root     5 2008-05-02 15:47 /dev/lirc_imon -> lirc1
lrwxrwxrwx 1 root root     5 2008-05-02 15:47 /dev/lirc_mce -> lirc0

I had some udev rules written that said this
#These rules are currently only adapted for a single lirc device.
#They are mainly used for hotplugability of the USB devices
#So that the user won't have to restart the lircd process.
#
#If a user has multiple lirc devices, and removes one of them
#The other will stop working as well.  This is a side effect
#of both this udev script as well as the lirc architecture
#Of chaining lircd processes.
ACTION=="add", KERNEL=="lirc[0-9]", RUN="/etc/init.d/lirc restart udev"
ACTION=="remove", KERNEL=="lirc[0-9]", RUN="/etc/init.d/lirc stop udev"

KERNEL=="lirc[0-9]*", SYSFS{idVendor}=="0609", SYMLINK+="lirc_mce"
KERNEL=="lirc[0-9]*", SYSFS{idVendor}=="15c2", SYMLINK+="lirc_imon"

and my hardware.conf says now this
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Windows Media Center Remotes (new version Philips et al.)"

# Arguments which will be used when launching lircd
REMOTE_LIRCD_ARGS="-d /dev/lirc_mce --output=/dev/lircd --listen"
LIRCD2_ARGS="-d /dev/lirc_imon --output=/dev/lircd1 --connect=localhost:8765 --pidfile=/var/run/lircd2.pid"

#Don't start lircmd even if there seems to be a good config file
#START_LIRCMD=false

#Try to load appropriate kernel modules
LOAD_MODULES=true

# Run "lircd --driver=help" for a list of supported drivers.
REMOTE_DRIVER=""
# If DEVICE is set to /dev/lirc and devfs is in use /dev/lirc/0 will be
# automatically used instead
REMOTE_DEVICE="/dev/lirc0"
REMOTE_MODULES="lirc_dev lirc_mceusb2"

# Default configuration files for your hardware if any
REMOTE_LIRCD_CONF="mceusb/lircd.conf.mceusb"
LIRCMD_CONF=""



TRANSMITTER="None"
TRANSMITTER_MODULES=""
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE=""
TRANSMITTER_LIRCD_CONF=""
TRANSMITTER_LIRCD_ARGS=""
START_LIRCD="true"
START_LIRCMD=""
FORCE_NONINTERACTIVE_RECONFIGURATION="false"

So somethings seems to have broken but where shall I start?

Sorry for not usig tags but firefox seem also to be broken after upgrade

---

