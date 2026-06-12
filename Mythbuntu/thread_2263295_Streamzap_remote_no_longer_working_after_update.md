---
title: "Streamzap remote no longer working after update"
date: 2015-01-30
forum: Mythbuntu
---

### Post by CSharpe67 on 2015-01-30
Hi all,

I followed this post and had my remote working

[http://forum.kodi.tv/showthread.php?tid=101151](http://forum.kodi.tv/showthread.php?tid=101151)

After a recently update Mythbuntu and my streamzap remote no longer responds to button presses.  I have been looking for an answer since then.

sudo ir-keytable
Found /sys/class/rc/rc0/ (/dev/input/event4) with:
    Driver cx88xx, table rc-hauppauge
    Supported protocols: NEC RC-5 RC-6 JVC SONY SANYO LIRC RC-5-SZ other 
    Enabled protocols: RC-5 
    Name: cx88 IR (pcHDTV HD5500 HDTV)
    bus: 1, vendor/product: 7063:5500, version: 0x0001
    Repeat delay = 500 ms, repeat period = 125 ms

Found /sys/class/rc/rc1/ (/dev/input/event6) with:
    Driver streamzap, table rc-streamzap
    Supported protocols: NEC RC-5 RC-6 JVC SONY SANYO LIRC RC-5-SZ other 
    Enabled protocols: LIRC 
    Name: Streamzap PC Remote Infrared Rec
    bus: 3, vendor/product: 0e9c:0000, version: 0x0100
    Repeat delay = 500 ms, repeat period = 125 ms

When I try and test

sudo ir-keytable -t
Testing events. Please, press CTRL-C to abort.

No events show up


------------------------------------------------------------------------------------------------------------------------
lircd.conf
--------------------------------------------------------
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

#Configuration for the Streamzap PC Remote remote:
include "/usr/share/lirc/remotes/devinput/lircd.conf.devinput"
#include "/usr/share/lirc/remotes/streamzap/lircd.conf.streamzap"




------------------------------------------------------------------------------------------------------------------------
lircmd.conf
--------------------------------------------------------
#UNCONFIGURED
#
# To find out how to get a proper configuration file please read:
# 
#    /usr/share/doc/lirc/README.Debian


------------------------------------------------------------------------------------------------------------------------
hardware.conf
--------------------------------------------------------
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Streamzap PC Remote"
REMOTE_MODULES="lirc_dev streamzap"
REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/lirc0"
REMOTE_SOCKET=""
REMOTE_LIRCD_CONF="streamzap/lircd.conf.streamzap"
REMOTE_LIRCD_ARGS=""

#Chosen IR Transmitter
TRANSMITTER="None"
TRANSMITTER_MODULES=""
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE=""
TRANSMITTER_SOCKET=""
TRANSMITTER_LIRCD_CONF=""
TRANSMITTER_LIRCD_ARGS=""

#Disable kernel support.
#Typically, lirc will disable in-kernel support for ir devices in order to
#handle them internally.  Set to false to prevent lirc from disabling this
#in-kernel support. 
#DISABLE_KERNEL_SUPPORT="true"

#Enable lircd
START_LIRCD="true"

#Don't start lircmd even if there seems to be a good config file
START_LIRCMD="true"

#Try to load appropriate kernel modules
LOAD_MODULES="false"
DRIVER="devinput"
DEVICE="/dev/input/by-id/streamzap"

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


----------------------------------------------------------------------------------------------------------------------------------------------
version information

apt-cache policy mythtv
mythtv:
  Installed: 2:0.27.0+fixes.20140324.8ee257c-0ubuntu3
  Candidate: 2:0.27.0+fixes.20140324.8ee257c-0ubuntu3
  Version table:
 *** 2:0.27.0+fixes.20140324.8ee257c-0ubuntu3 0
        500 [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) trusty-updates/multiverse amd64 Packages
        100 /var/lib/dpkg/status
     2:0.27.0+fixes.20140324.8ee257c-0ubuntu2 0
        500 [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) trusty/multiverse amd64 Packages

lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.1 LTS
Release:    14.04
Codename:    trusty

---

### Post by benlyboy on 2015-02-04
I'm having the same problem setting up a  streamzap remote. I haven't found an answer as of yet, so I will be interested to see what you come up with. Mine is a new build so I wasn't sure if it was a hardware issue, there is some talk on here about linux having problems with USB drivers on later mb. However I don't think that's the case with mine as if I uninstall LIRC some of the arrow keys work.

---

