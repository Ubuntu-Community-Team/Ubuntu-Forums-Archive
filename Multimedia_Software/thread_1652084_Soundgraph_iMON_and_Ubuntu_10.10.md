---
title: "Soundgraph iMON and Ubuntu 10.10"
date: 2010-12-24
forum: Multimedia Software
---

### Post by turkosbon on 2010-12-24
Hello , i have ubuntu 10.10

well i have problem with imon doesn't work fine (but in my old ubuntu 9.10 work fine), 

i have this display in my nox live2 carcase
[IMG]http://www.soundgraph.com/assets/Uploads/products/Pro_OEMLCD/Pro_OEMLCD_04.jpg[/IMG]

> 
Bus 006 Device 002: ID 15c2:0038 SoundGraph Inc. GD01 MX VFD Display/IR Receiver
my lirc config selected
> Soundgraph iMON Antec Veris
with this remote controll

[IMG]http://www.soundgraph.com/assets/Uploads/products/Pro_Ultra/Pro_Ultra03.jpg[/IMG]


> 
lircd -v
lircd 0.8.7-pre3
> 
lcdproc -v
LCDproc 0.5.3
hardware.conf
> 
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Soundgraph iMON Antec Veris"
REMOTE_MODULES="lirc_dev lirc_imon"
REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/lirc0"
REMOTE_SOCKET=""
REMOTE_LIRCD_CONF="imon/lircd.conf.imon-antec-veris"
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

#Forcing noninteractive reconfiguration
#If lirc is to be reconfigured by an external application
#that doesn't have a debconf frontend available, the noninteractive
#frontend can be invoked and set to parse REMOTE and TRANSMITTER
#It will then populate all other variables without any user input
#If you would like to configure lirc via standard methods, be sure
#to leave this set to "false"
FORCE_NONINTERACTIVE_RECONFIGURATION="false"
START_LIRCMD=""
lircd.conf
> 
#
#It includes the default configuration for the remote and/or
#transmitter that you have selected during package installation.
#
#Feel free to add any custom remotes to the configuration
#via additional include directives or below the existing
#Ubuntu include directives from your selected remote and/or
#transmitter.

#Configuration for the Soundgraph iMON Antec Veris remote:
include "/usr/share/lirc/remotes/imon/lircd.conf.imon-antec-veris"
can you help me?

Thank you.

---

### Post by macid on 2011-01-11
Hy out there,

I have absolutley the same problem, and the same hardware. Testet many lirc.conf's without any succsess.

I think, the problem ist nested in the new, linux-core-includet imon drivers, automatically loaded by hal.

But blacklisting the imon does not seems to do anything.

(Sorry for my baaaaad english, hope anyone understand ist ;o) No chance for better english)

---

### Post by macid on 2011-01-13
Take a look at this thread, the Problem is solved:

[http://www.uluga.ubuntuforums.org/showthread.php?t=1665657](http://www.uluga.ubuntuforums.org/showthread.php?t=1665657)

---

