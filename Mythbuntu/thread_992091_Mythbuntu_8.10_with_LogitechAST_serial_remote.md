---
title: "Mythbuntu 8.10 with Logitech/AST serial remote"
date: 2008-11-24
forum: Mythbuntu
---

### Post by FlypSyde on 2008-11-24
I'm trying to set up Mythbuntu 8.10 with a Logitech/AST serial remote. I followed what little instruction was available in the Mythbuntu documentation but it's not working. I have the correct remote selected in the MCC under Infrared Devices and it looks like my

/etc/lirc/hardware.conf
/etc/lirc/lircd.conf

are configured correctly and the configuration file

/usr/share/lirc/remotes/logitech/lircd.conf.logitech

exists. The serial receiver and remote work under Windows so I know it's functioning. I was originally going to use Mythbuntu 8.04 and after upgrading the default LIRC package to 0.8.3 I was able to test the remote with irw. But in 8.10 I can't even get irw to stay up. It immediately returns to the prompt and then refuses connections.

Everything I've read says that this serial receiver and remote should work so I guess it's something I'm missing as far as configuring this to work in Mythbuntu. Any help is greatly appreciated!

Thanks!

-FlypSyde

---

### Post by FlypSyde on 2008-11-24
Here's what is in my hardware.conf and lircd.conf if it helps:

/etc/lirc/hardware.conf
```

# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Logitech/AST"
REMOTE_MODULES=""
REMOTE_DRIVER="logitech"
REMOTE_DEVICE=""
REMOTE_LIRCD_CONF="logitech/lircd.conf.logitech"
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
FORCE_NONINTERACTIVE_RECONFIGURATION="false"
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

#Configuration for the Logitech/AST remote:
include /usr/share/lirc/remotes/logitech/lircd.conf.logitech

```

---

### Post by FlypSyde on 2008-11-25
I modified my hardware.conf by adding an entry for REMOTE_DEVICE

```

#Chosen Remote Control
REMOTE="Logitech/AST"
REMOTE_MODULES=""
REMOTE_DRIVER="logitech"
**REMOTE_DEVICE="/dev/ttyS0"**
REMOTE_LIRCD_CONF="logitech/lircd.conf.logitech"
REMOTE_LIRCD_ARGS=""

```

Now irw works as it should and I see the data output from my remote. It still doesn't work with Mythbuntu but I'm getting closer!

-FlypSyde

---

### Post by FlypSyde on 2008-11-25
I ran mythbuntu-lirc-generator to generate the .lircrc file. Mythbuntu now responds to some of the buttons on my remote but not enough to be usable. Still, it's a lot closer than it was 12 hours ago!

-FlypSyde

---

### Post by FlypSyde on 2008-11-25
Ok, I finally got this thing working. Turns out the remote was fully functional when I got it going earlier, I just didn't try all of the buttons on the remote. The .lircrc file had some of the buttons mapped to different functions. I also figured out how to change the functions of the buttons by looking at how the .lircrc ties in to the lircd.conf.

I hope my notes here help someone!

-FlypSyde

---

