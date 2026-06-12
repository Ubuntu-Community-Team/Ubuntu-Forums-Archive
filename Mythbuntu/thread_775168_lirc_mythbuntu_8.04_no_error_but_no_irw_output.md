---
title: "lirc mythbuntu 8.04 no error but no irw output"
date: 2008-04-29
forum: Mythbuntu
---

### Post by mrplow on 2008-04-29
I had everything working then when I went to watch a show my remote isn't working.
I'm running a FE/BE combo so I quit the FE and tried irw, it started without error but didn't respond to remote commands. Reboot didn't fix it.
Its like the batteries are dead but I'm sure they're not

```
myth@myth-desktop:~$ dmesg | grep -i lirc
[   49.721645] lirc_dev: IR Remote Control driver registered, at major 61 
[   50.136941] lirc_i2c: chip 0x10020 found @ 0x71 (Hauppauge PVR150)
[   50.136965] lirc_dev: lirc_register_plugin: sample_rate: 10
myth@myth-desktop:~$ ls -l /dev/lirc
lirc0  lircd  
myth@myth-desktop:~$ ls -l /dev/lir*
crw-rw---- 1 root root 61, 0 2008-04-29 07:39 /dev/lirc0
srw-rw-rw- 1 root root     0 2008-04-29 07:39 /dev/lircd
```

/etc/lirc/hardware.conf
```
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Hauppauge TV card"
REMOTE_MODULES="lirc_dev lirc_i2c"
REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/lirc0"
REMOTE_LIRCD_CONF="hauppauge/lircd.conf.hauppauge"
REMOTE_LIRCD_ARGS=""

#Chosen IR Transmitter
TRANSMITTER="None"
TRANSMITTER_MODULES=""
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE=""
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

#Forcing noninteractive reconfiguration
#If lirc is to be reconfigured by an external application
#that doesn't have a debconf frontend available, the noninteractive
#frontend can be invoked and set to parse REMOTE and TRANSMITTER
#It will then populate all other variables without any user input
#If you would like to configure lirc via standard methods, be sure
#to leave this set to "false"
START_LIRCMD=""
```

/etc/lirc/lircd.conf
```
#This configuration has been automatically generated via
#the Ubuntu LIRC package maintainer scripts.
#
#It includes the default configuration for the remote and/or
#transmitter that you have selected during package installation.
#
#Feel free to add any custom remotes to the configuration
#via additional include directives or below the existing
#Ubuntu include directives from your selected remote and/or
#transmitter.

#Configuration for the Hauppauge TV card remote:
include /usr/share/lirc/remotes/hauppauge/lircd.conf.hauppauge
```

~/.lircrc
```
#Custom lircrc generated via mythbuntu-lirc-generator
#All application specific lircrc files are within ~/.lirc
include ~/.lirc/mythtv
include ~/.lirc/mplayer
include ~/.lirc/xine
include ~/.lirc/vlc
include ~/.lirc/xmame
include ~/.lirc/xmess
include ~/.lirc/totem
include ~/.lirc/elisa
```

---

### Post by mrplow on 2008-04-29
[mythbackend.log]("http://paste.ubuntu.com/8811/") <paste.ubuntu.com>
[mythfrontend.log]("http://paste.ubuntu.com/8812/") <paste.ubuntu.com>

---

### Post by superm1 on 2008-04-30
Silly solution possibly, but try unplugging and plugging back in the IR receiver.  On the pvr-150's, those cables sometimes just need a small jostle.

---

### Post by mrplow on 2008-04-30
> **superm1 said:**
> Silly solution possibly, but try unplugging and plugging back in the IR receiver.  On the pvr-150's, those cables sometimes just need a small jostle.

Darn, it didn't make a difference. Thanks though.

---

### Post by stronzo on 2008-05-01
i think you have wrong settings in the
/etc/lirc/lircd.conf

it points to 
include /usr/share/lirc/remotes/hauppauge/lircd.conf.hauppauge

if you open this file with an editor, it is probably empty.
did you have an extra configuration file for your buttons?
if so, you have to point to it in the lircd.conf file with the include option!

if you have no configfile you can set up your own with "irrecord"
it produces a conf-file which then must be linked in the lircd.conf.
after that it will work!

---

### Post by mrplow on 2008-05-01
/usr/share/lirc/remotes/hauppauge/lircd.conf.hauppauge
is not empty, it is the default code settings for my pvr150 remote as far as I know, are there any more log files that would be of any help?

---

### Post by stronzo on 2008-05-02
try irrecord and check if it recognizes your remote. if it does not, you really have a serious problem! if it works, set your own config file.

---

