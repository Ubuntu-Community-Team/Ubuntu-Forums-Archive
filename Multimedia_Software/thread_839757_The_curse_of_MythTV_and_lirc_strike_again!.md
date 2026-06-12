---
title: "The curse of MythTV and lirc strike again!"
date: 2008-06-24
forum: Multimedia Software
---

### Post by AndrewWalker on 2008-06-24
I'm having absolute hell getting lirc to work on Mythbuntu-8.04.
I'm using an 64 bit version of Mythbuntu and have a freeview digital terrestrial tuner Hauppauge Nova-T DVB-T which works fine but whatever I try I can't get the remote configured correctly.
The remote control is identical to one I have with a WinTV-HVR1300 card, it's silver on top, black on bottom so which driver should it be? Here's a link to a picture of it if it helps identify it

[http://lirc.sourceforge.net/remotes/hauppauge/PVR-350.jpg](http://lirc.sourceforge.net/remotes/hauppauge/PVR-350.jpg)

The Hauppauge Nova-T 500 configuration is the nearest but the back/exit button doesn't work which renders it useless for MythTV.
Can anyone tell me how to get it working correctly? Here's the dmesg info in case it's useful.
[   37.398618] cx88[0]: subsystem: 0070:9002, board: Hauppauge Nova-T DVB-T [card=18,autodetected]
[   37.398620] cx88[0]: TV tuner type 4, Radio tuner type -1
[   37.445756] cx88/0: cx2388x v4l2 driver version 0.0.6 loaded
[   37.544381] tveeprom 2-0050: Hauppauge model 90003, rev C2B0, serial# 771453
[   37.544385] tveeprom 2-0050: MAC address is 00-0D-FE-0B-C5-7D
[   37.544387] tveeprom 2-0050: tuner model is Thompson DTT75105 (idx 110, type 4)
[   37.544389] tveeprom 2-0050: TV standards ATSC/DVB Digital (eeprom 0x80)
[   37.544391] tveeprom 2-0050: audio processor is None (idx 0)
[   37.544393] tveeprom 2-0050: decoder processor is CX882 (idx 25)
[   37.544394] tveeprom 2-0050: has no radio, has IR receiver, has no IR transmitter
[   37.544396] cx88[0]: hauppauge eeprom: model=90003 
[   37.544479] input: cx88 IR (Hauppauge Nova-T DVB-T as /devices/pci0000:00/0000:00:10.0/0000:04:09.2/input/input7

Update! well I've now found a supposedly correct script for my remote in which every single button except the bloody one I need to configure actually works! I told you it was cursed didn't I!
The problem one is the Back/Exit button, all I want to be able to do is exit back out of MythTV like when you hit the esc button on the keyboard. I would be happy just to be able to remap the option to another key but I can't get irrecord to work to be able to find the correct ir code. If I try

sudo irrecord -H devinput -d /dev/input/by-path/pci-0000:04:09.2--event-ir test.conf

but regardless of which button I press it responds with

Hold down an arbitrary button.
irrecord: gap not found, can't continue
irrecord: closing '/dev/input/by-path/pci-0000:04:09.2--event-ir'
mythtv@mythtvbox:

which doesn't make sense as my remote works with the same config, here's my hardware.conf that works.


# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Custom"
REMOTE_MODULES=""
REMOTE_DRIVER="devinput"
REMOTE_DEVICE="/dev/input/by-path/pci-0000:04:09.2--event-ir"
REMOTE_LIRCD_CONF="/usr/share/lirc/remotes/hauppauge/lircd.conf.nova-t"
REMOTE_LIRCD_ARGS=""

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

Any suggestions cause I'm getting to the stage of stamping on my remote control!

I forgot to stop lirc daemon before running irrecord! I've now created a correct Hauppauge Nova-T card remote control config script which is also an identical remote to a Hauppauge HVR-1300 card in case anyone needs one. I'm emailing it to the lirc developers.

---

