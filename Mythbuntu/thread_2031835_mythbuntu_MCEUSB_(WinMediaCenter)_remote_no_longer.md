---
title: "mythbuntu MCEUSB (WinMediaCenter) remote no longer works"
date: 2012-07-22
forum: Mythbuntu
---

### Post by keepitsimpleengr on 2012-07-22
I had no problems using my Windows Media Center Remote with 10.10 Mythbuntu, but after upgrading to 12.04, it no longer affects Mythbuntu.

I have verified and re-installed it in Mythbuntu Control Centre.

I have used irw to verify the ir buttons actions are properly received by the HTPC.

I am running under Unity 2D to avoid the full-screen un&#8231;hidden Unity top panel problem.

64bit fully updated Mythbuntu.

Thanks

---

### Post by keepitsimpleengr on 2012-07-22
```
cat /etc/lirc/hardware.con

#Chosen Remote Control
REMOTE="Windows Media Center Transceivers/Remotes (all)"
REMOTE_MODULES="lirc_dev mceusb"
REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/lirc0"
REMOTE_SOCKET=""
REMOTE_LIRCD_CONF="mceusb/lircd.conf.mceusb"
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

# lsusb | grep -i infrared
Bus 003 Device 002: ID 0471:0815 Philips (or NXP) eHome Infrared Receiver
```

---

### Post by Lester_Burnham on 2012-07-23
If all buttons work using irw, you just need to edit ~/.lirc/mythtv and fix the button names that have changed. Use the name you see in irw.
Make sure you're editing the mceusb section.

Lester

---

### Post by keepitsimpleengr on 2012-07-23
> **Lester_Burnham said:**
> If all buttons work using irw, you just need to edit ~/.lirc/mythtv and fix the button names that have changed. Use the name you see in irw.
Make sure you're editing the mceusb section.

Lester

This was from irw: ```
000000037ff07bde 00 KEY_RIGHT mceusb
```

This was already in ~/.lirc/mytht:
```
begin
    remote = mceusb
    prog = mythtv
    button = KEY_RIGHT
    config = Right
    repeat = 0
    delay = 0
end
```

So I changed this in ~/.lirc/mythtv:
```
begin
    remote = mceusb_hauppauge
    prog = mythtv
    button = Right    
    config = Right
    repeat = 0
    delay = 0
end
```

To this:
```
begin
    remote = mceusb_hauppauge
    prog = mythtv
    button = KEY_RIGHT    
    config = Right
    repeat = 0
    delay = 0
end
```

Likewise here:
```
begin
    remote = vista_mce
    prog = mythtv
    button = KEY_RIGHT
    config = Right
    repeat = 0
    delay = 0
end
```

And I changed nothing else, now it works, and I don't know why, but then as long as it works, I don't care

Thanks...

---

### Post by Lester_Burnham on 2012-07-25
> **keepitsimpleengr said:**
> This was from irw: ```
000000037ff07bde 00 KEY_RIGHT mceusb
```

This was already in ~/.lirc/mytht:
```
begin
    remote = mceusb
    prog = mythtv
    button = KEY_RIGHT
    config = Right
    repeat = 0
    delay = 0
end
```

So I changed this in ~/.lirc/mythtv:
```
begin
    remote = mceusb_hauppauge
    prog = mythtv
    button = Right    
    config = Right
    repeat = 0
    delay = 0
end
```

To this:
```
begin
    remote = mceusb_hauppauge
    prog = mythtv
    button = KEY_RIGHT    
    config = Right
    repeat = 0
    delay = 0
end
```

Likewise here:
```
begin
    remote = vista_mce
    prog = mythtv
    button = KEY_RIGHT
    config = Right
    repeat = 0
    delay = 0
end
```

And I changed nothing else, not it works, and I don't know why, but then as long as it works, I don't care

Thanks...

Like you said, that doesn't really make sense, as you are using remote=mceusb. What's in your hardware.conf and lircd.conf

Lester

---

### Post by anonymousdog on 2012-07-25
> **Lester_Burnham said:**
> Like you said, that doesn't really make sense, as you are using remote=mceusb. What's in your hardware.conf and lircd.conf

Lester
The hardware.conf is above (although the file name looks truncated), but OP never posted lircd.conf.

---

### Post by keepitsimpleengr on 2012-07-25
> **Lester_Burnham said:**
> Like you said, that doesn't really make sense, as you are using remote=mceusb. What's in your hardware.conf and lircd.conf

Lester

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

#Configuration for the Windows Media Center Transceivers/Remotes (all) remote:
include "/usr/share/lirc/remotes/mceusb/lircd.conf.mceusb"
```

```
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Windows Media Center Transceivers/Remotes (all)"
REMOTE_MODULES="lirc_dev mceusb"
REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/lirc0"
REMOTE_SOCKET=""
REMOTE_LIRCD_CONF="mceusb/lircd.conf.mceusb"
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
```

---

### Post by Lester_Burnham on 2012-07-26
> **anonymousdog said:**
> The hardware.conf is above (although the file name looks truncated), but OP never posted lircd.conf.

Hi,

Thanks for pointing that out. It had been a while and thanks to the flu, I've just got back to this and was lazy :)

Lester

---

### Post by Lester_Burnham on 2012-07-26
> **keepitsimpleengr said:**
> /etc/lirc/lircd.conf

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

#Configuration for the Windows Media Center Transceivers/Remotes (all) remote:
include "/usr/share/lirc/remotes/mceusb/lircd.conf.mceusb"
```

```
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Windows Media Center Transceivers/Remotes (all)"
REMOTE_MODULES="lirc_dev mceusb"
REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/lirc0"
REMOTE_SOCKET=""
REMOTE_LIRCD_CONF="mceusb/lircd.conf.mceusb"
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
```

Hi,

Going by that lot only the entries in ~/.lirc/mythtv with remote = mceusb need to be fixed.
So it still doesn't make sense :)

How it works:
If you look in you "/usr/share/lirc/remotes/mceusb/lircd.conf.mceusb" file, they are what you see in irw. So you would use irrecord to create a file like that then add the path of that file like it is in both above. Then use the ~/.lirc/mythtv fle to map the button to mythtv's key for that function on a keyboard.

Lester

---

### Post by keepitsimpleengr on 2012-07-27
> **Lester_Burnham said:**
> Hi,

Going by that lot only the entries in ~/.lirc/mythtv with remote = mceusb need to be fixed.
So it still doesn't make sense :)

Lester

My best guess?  Since it worked before the upgrade, I figure something that should have gotten re-initialized wasn't, and my messing around (probably editing and changing the modify date) triggered a re-initialization.  The upgrade was a 10.10>11.04>11.10>12.04

In addition, the pushing a button on the remote now gets a much faster reaction on the screen.

In any case I'm a happy camper :D

---

### Post by Lester_Burnham on 2012-07-27
Who could argue with that :popcorn:

Lester

---

### Post by mark541 on 2012-11-29
Here's another thing to try. Run the command mythbuntu-lircrc-generator as shown here; 

$ mythbuntu-lircrc-generator

It renamed the ~/.lircrc and all of the conf files in ~/.lirc to <file>.old, then created the new versions, using the /etc/lirc/lircd.conf file as it's input. The /etc/lirc/lircd.conf file basically points to the /usr/share/lirc/remotes/mceusb/lircd.conf.mceusb file, which has all the button names (with the "KEY_" prefix). 
So when it was done, the new versions have the updated sections with all of the "KEY_" prefixes, and it did it for all the conf files in ~/.lirc/ at the same time (e.g. for mythtv, mplayer, etc.).

---

