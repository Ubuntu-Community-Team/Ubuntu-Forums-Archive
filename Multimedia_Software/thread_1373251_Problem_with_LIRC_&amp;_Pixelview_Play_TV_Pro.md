---
title: "Problem with LIRC &amp; Pixelview Play TV Pro"
date: 2010-01-05
forum: Multimedia Software
---

### Post by skolim on 2010-01-05
Hello!

I'm quite new to Ubuntu I have used Linux before but not as my primary desktop system. Recently i decided to give it a chance. 
There was always one thing that I couldn't handle in Linux - that is my TV Tuner card (Prolink Pixelview PV-BT878P+ Rev 4C). I got it working on Ubuntu (finally :) ), but there is one thing that keeps me from fully replacing windows. I can't get remote control working :(

I've installed lirc with apt-get and choose my TV Tuner card. but when I start lirc demon i get following output:
```

root@marek-desktop:/home/marek# /etc/init.d/lirc start
 * Loading LIRC modules                                                                                                     [ OK ] 
 * Unable to load LIRC kernel modules. Verify your
 * selected kernel modules in /etc/lirc/hardware.conf

```and when I try to start irw I get:
```

root@marek-desktop:/home/marek# irw
connect: No such file or directory

```My hardware.conf looks like this:
```

# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Prolink Pixelview PV-BT878P+ (Rev.4C8E card=70)"
REMOTE_MODULES="devinput"
REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/lirc0"
REMOTE_SOCKET=""
REMOTE_LIRCD_CONF="pixelview/lircd.conf.playtv_pro"
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

```and my lircd.conf is:
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

#Configuration for the Prolink Pixelview PV-BT878P+ (Rev.4C8E card=70) remote:
include "/usr/share/lirc/remotes/pixelview/lircd.conf.playtv_pro"
```I'm sure that I choose correct TV card model because xatv and tvtime work perfectly. Maybe there is something wrong with auto-generated config or maybe I should do some additional configuration.

Please help me to find what is wrong because I'm so close to getting rid of Windows and I don't want to miss that chance:-|

PS. Sorry for any mistakes I've made - English is not my primary language.

---

### Post by gladiss on 2010-01-17
I am also working on the same isssue..
Will post here if i get any solution

---

### Post by sports.car.guy on 2010-01-17
Is the IR receiver initialized on the card or even supported with Linux?

For $5 to $25 USD why not just purchase a Windows Media Center / Vista or Windows 7 certified remote for your Myth TV setup? I got mine off of New Egg and love it.

If the remote is like the only thing stopping you from making the switch completely it seems to me for cheap money you can have something work beautifully.

If the IR receiver is supported I have found the Mythbuntu Control Centre's Lirc configuration gives a great starting point for remote files for your apps like MythTV obviously,  VLC, and MPlayer. It should get things up and running with only a couple tweaks to your files and things will be perfect.

For example the Mythbuntu Control Centre makes my record button somthing obscure and makes my recorded television button record. No biggie and easy to fix.

---

### Post by dhstolfi on 2010-04-07
Hello.
I had the same problem and I solve it using **/dev/input/eventX**:

```
sudo cat /proc/bus/input/devices
```

(...)
I: Bus=0001 Vendor=109e Product=036e Version=0001
N: Name="bttv IR (card=50)"
P: Phys=pci-0000:05:01.0/ir0
S: Sysfs=/devices/pci0000:00/0000:00:1e.0/0000:05:01.0/input/input6
U: Uniq=
H: Handlers=kbd **event6**
B: EV=100003
B: KEY=2c0814 10000400000000 0 402008000 209000002001 1e000000004400 ffc
(...)

I my system was event6. Check yours and change it in the next commands

```
sudo apt-get install joystick
sudo evtest /dev/input/event6
``` 

Check the reception pushing r/c buttons.

Then install lirc: ```
sudo apt-get install lirc
```
or ```
sudo dpkg-reconfigure lirc
```

choose: **Linux input layer (/dev/input/eventX)**

restart the service: ```
sudo invoke-rc.d lirc restart
```

Check the communication with lirc (pressing buttons on r/c): ```
irw
```

This is my file /etc/lirc/hardware.conf (remember change **event6**)
```

# /etc/lirc/hardware.conf
#
# Arguments which will be used when launching lircd
LIRCD_ARGS=""

#Don't start lircmd even if there seems to be a good config file
START_LIRCMD=false

#Try to load appropriate kernel modules
LOAD_MODULES=true

# Run "lircd --driver=help" for a list of supported drivers.
DRIVER="dev/input"
# If DEVICE is set to /dev/lirc and devfs is in use /dev/lirc/0 will be
# automatically used instead
DEVICE="/dev/input/event6"
MODULES=""

# Default configuration files for your hardware if any
LIRCD_CONF=""
LIRCMD_CONF=""

REMOTE="Linux input layer (/dev/input/eventX)"
REMOTE_MODULES=""
REMOTE_DRIVER="devinput"
REMOTE_DEVICE="/dev/input/event6"
REMOTE_SOCKET=""
REMOTE_LIRCD_CONF="devinput/lircd.conf.devinput"
REMOTE_LIRCD_ARGS=""
TRANSMITTER="None"
TRANSMITTER_MODULES=""
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE=""
TRANSMITTER_SOCKET=""
TRANSMITTER_LIRCD_CONF=""
TRANSMITTER_LIRCD_ARGS=""
START_LIRCD="true"
FORCE_NONINTERACTIVE_RECONFIGURATION="false"

```

I hope it was useful for you
regards

Daniel

source: [http://parker1.co.uk/mythtv_ubuntu2.php](http://parker1.co.uk/mythtv_ubuntu2.php)

---

