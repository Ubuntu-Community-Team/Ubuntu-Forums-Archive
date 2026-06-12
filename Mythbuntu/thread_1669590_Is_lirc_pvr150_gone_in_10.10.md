---
title: "Is lirc_pvr150 gone in 10.10?"
date: 2011-01-17
forum: Mythbuntu
---

### Post by WiFlag on 2011-01-17
So I decided to finally upgrade... from 8.04 or 8.10 I think I was at.

Most everything seemed to have carried over well, but my remote for my Hauppauge PVR150 stopped working.

I think I narrowed it down to lirc_pvr150 missing from /lib/modules/2.6.32.27-generic
Do I have to pull the source from somewhere and build a new one?

Granted it's been 2 years since I had to do anything to this box, so I'm a little rusty.

EDIT: Correction - I upgraded to 10.04, not 10.10

EDIT2: 
Further research seems to indicate that lirc_pvr150 has been replaced by lirc_zilog, but that module is also missing in my install... 
- Installed lirc-modules-source, but /usr/src/lirc-0.8.6/drivers doesn't have lirc_zilog, which I think would be a prerequisite to applying the diff discussed in this thread:
[http://ubuntuforums.org/showthread.php?t=1598968&page=2](http://ubuntuforums.org/showthread.php?t=1598968&page=2)

EDIT3:
Found an updated diff that appeared to work, with some instructions:
[http://notepad.bobkmertz.com/2010/06/pvr-150-ir-blaster-on-mythbuntu-1004.html](http://notepad.bobkmertz.com/2010/06/pvr-150-ir-blaster-on-mythbuntu-1004.html)
This got me a lirc_zilog driver folder in the lirc source tree.
I try restarting lirc after this, and it fails.
I got the module installed by doing:
sudo rmmod lirc_dev {very important or the next line will fail}
sudo modprobe lirc_zilog
- After this, still fails when trying to restart lirc, but trying a reboot to see if that fixes it - I'll have to wait until I get home to see if my remote is working

EDIT4: 
Restart didn't work, but I narrowed that issue down to transmitter info being populated into /etc/lirc/hardware.conf during the upgrade
Removed the offending lines and lirc starts up. A restart was needed to make myth obey the remote, but it's working now.
Now to fix my display scaling...

---

### Post by snazzed on 2011-03-01
I have a little Linux behind me so I'm not a complete n00b but I've been up and down Google and I'm about to give up.

Remotes have not worked for:
 - Hauppauge 2250 (exchanged for: below)
 - Hauppauge 1600 - gave up on remote.  Now will be an extra tuner
 - Hauppauge PVR-150:  Worked on my 4yr old MythDora Box



Here's my Current system state.  Please help.

MythBunu 10.10 - 64bit.  I selected Hauppauge TV-Card in the Remote section of the Installation procedures.

```
uname -r
2.6.35-22-generic
__________________________________________

dmesg | grep lirc
[   14.942672] lirc_dev: IR Remote Control driver registered, major 250 
[   14.945000] lirc_i2c: module is from the staging directory, the quality is unknown, you have been warned.
__________________________________________

lsusb
Bus 006 Device 003: ID 046d:c303 Logitech, Inc. iTouch Keyboard
Bus 006 Device 002: ID 0409:55ab NEC Corp. Hub [iMac/iTouch kbd]
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 046d:c016 Logitech, Inc. Optical Wheel Mouse
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
______________________________________________

/etc/lircd/hardware.conf (commented sections removed for brevity)
#Chosen Remote Control
REMOTE="Hauppauge TV card"
REMOTE_MODULES="lirc_dev lirc_i2c"
REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/lirc0"
REMOTE_SOCKET=""
REMOTE_LIRCD_CONF="hauppauge/lircd.conf.hauppauge"
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
LOAD_MODULES="true"

# Default configuration files for your hardware if any
LIRCMD_CONF=""


FORCE_NONINTERACTIVE_RECONFIGURATION="false"
START_LIRCMD=""

____________________________________________

/etc/lirc/lircd.conf

#Configuration for the Hauppauge TV card remote:

include "/usr/share/lirc/extras/more_remotes/hauppauge/lircd.conf.hauppauge"
____________________________________________

irw
<no feedback when remote buttons are pressed>


```

I would be thrilled if I can get this running.

thanks 
snazzed

---

