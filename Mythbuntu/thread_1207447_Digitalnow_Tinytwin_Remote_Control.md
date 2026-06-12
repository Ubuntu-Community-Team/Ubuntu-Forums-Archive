---
title: "Digitalnow Tinytwin Remote Control?"
date: 2009-07-08
forum: Mythbuntu
---

### Post by fredinator on 2009-07-08
Hi, I've built a mythtv htpc recently, and I'm having trouble getting input from the remote. I've tried gnome-lirc-properties, which does seem to autodetect it in some way, and then after starting lircd manually (as it doesn't seem to do so automatically), I don't get any input.
Has anyone succesfully set up this remote?
I'm running mythbuntu 9.04 btw.

Also, while on the topic of this tuner, is it possible to get the second tuner working? I can get it detected via [_this guide_]("http://www.mythtv.org/wiki/DigitalNow_Tiny_Twin_Dual_Tuner"), however it doesn't seem to pick up any channels, and accessing channels results in a timeout...

---

### Post by guid on 2009-08-05
I'm also struggling with this remote control - I can't get the daemon to start with my hardware.conf file, has anyone got a hardware.conf file I can try? or can spot what's wrong with mine?




when I run:

 sudo /usr/sbin/lircd -n /etc/lirc/hardware.conf

I get:
lircd-0.8.4a[6221]: error in configfile line 7
lircd-0.8.4a[6221]: reading of file '/etc/lirc/hardware.conf' failed
lircd-0.8.4a[6221]: reading of config file failed
lircd-0.8.4a[6221]: lircd(default) ready


here's my hardware.conf file:  line 7 looks fine to me?!?

# /etc/lirc/hardware.conf
#
#Chosen Remote Control
#REMOTE="None"
REMOTE="IR-receiver inside an USB DVB receiver" 
#REMOTE_MODULES=""
REMOTE_DRIVER="devinput"
REMOTE_DEVICE="/dev/input/event7"
REMOTE_LIRCD_CONF=""
REMOTE_LIRCD_ARGS=""

#Chosen IR Transmitter
TRANSMITTER="None"
TRANSMITTER_MODULES=""
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE=""
TRANSMITTER_LIRCD_CONF=""
TRANSMITTER_LIRCD_ARGS=""

#Enable lircd
START_LIRCD=true

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

# Receiver settings required by gnome-lirc-properties
RECEIVER_MODEL="Afatech DVB-T 2"
RECEIVER_VENDOR="Linux Input Device"

# Remote settings required by gnome-lirc-properties
REMOTE_MODEL="Linux Input Layer compatible Remote"
REMOTE_VENDOR="Generic"

Thanks in advance.

---

### Post by siren09 on 2009-09-01
I'm also trying to get this working.  See my post [http://ubuntuforums.org/showthread.php?t=1255749](http://ubuntuforums.org/showthread.php?t=1255749)

Have you guys made any progress?  I'm happy to help!

---

### Post by siren09 on 2009-09-02
I had both tuners recognised, but the picture on both had lots of visual noise and artifacts.  Eventually I recompiled the v4l-dvb from scratch and edited the af9015.c file to manually turn off the second tuner (I don't think there was a module option to do this).  Now works perfectly, but of course I don't have a second tuner!

---

