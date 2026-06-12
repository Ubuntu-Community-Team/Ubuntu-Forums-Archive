---
title: "Haven't yet been able to get a working IR remote"
date: 2010-07-07
forum: Mythbuntu
---

### Post by ozybushwalker on 2010-07-07
I have done a fresh install of Mythbuntu 10.04. I have LEADTEK Winfast DTV2000H tuner card which has a supplied remote control and infra red sensor that plugs into the card. The tuner works fine and I've been controlling Myth from a keyboard. Now I want to enable an IR remote control to make the system more usable to my wife (particularly) and the rest of my family.

I've used a few previous versions of Mythbuntu and always found the challenge of getting a remote control working to be especially challenging (haven't succeeded yet) but thought I'd have another attempt.

As well as the remote that came with the card I have a couple of "Windows Media Center Edition compatible" remotes with USB sensors. 

I thought I would start with the remote that came with the tuner card. Unfortunately its not listed in Myth Control Centre's list of supported remotes so, knowing there is a /dev/input/eventX device associated with the tuner I selected *Linux input layer (/dev/input/eventX)* as the remote. I noted it didn't ask me what /dev/input/eventX was to be used. From other web pages on this tuner card I remote I figured I would have to edit /etc/lirc/hardware.conf to specify the correct device. I also followed the suggestion to use a udev rule to create a device name linked to the actual device name to avoid the problem of the device name possible changing.

Then when I manually started lircd I saw
> [FONT="Courier New"]# lircd -n /etc/lirc/hardware.conf
lircd-0.8.6[2690]: error in configfile line 16
lircd-0.8.6[2690]: reading of file '/etc/lirc/hardware.conf' failed
lircd-0.8.6[2690]: reading of config file failed
lircd-0.8.6[2690]: lircd(default) ready, using /var/run/lirc/lircd
[/FONT]

Line 16 in /etc/lirc/hardware.conf reads
> [FONT="Courier New"]REMOTE_DRIVER="devinput"[/FONT]
If I add a space just before the last quote then the file is apparently successfully read:
> [FONT="Courier New"]# lircd -n /etc/lirc/hardware.conf
lircd-0.8.6[2729]: error in configfile line 19
lircd-0.8.6[2729]: reading of file '/etc/lirc/hardware.conf' failed
lircd-0.8.6[2729]: reading of config file failed
lircd-0.8.6[2729]: lircd(default) ready, using /var/run/lirc/lircd
[/FONT]

I've not been able to find anything about the required format of /etc/lirc/hardware.conf nor hint of what is wrong with the file nor why adding a space apparently allows it to be read further.

If I run lircd and specify the input method and device I can get a bit further:

> [FONT="Courier New"]# lircd -n -H devinput -d /dev/input/wfrem
lircd-0.8.6[2734]: lircd(devinput) ready, using /var/run/lirc/lircd
[/FONT]

Is there anyone able to help me through this? I've found a number of web resources on remote controls matched with this card or the DTV1000T but they all seem to be associated with much older versions of Mythbuntu or LIRC and its not clear they are relevant to version 10.04. (For example, [http://ubuntuforums.org/showthread.php?t=1102033]("http://ubuntuforums.org/showthread.php?t=1102033") and its reference to adding a new HAL rule.)


OR, Is there anyone able to help me through getting a "Windows MCE Compatible USB" remote? I have not been able to get either of my MCR remotes working but I haven't yet investigated this.

---

### Post by goffa on 2010-07-08
Hi ozybushwalker

I have a Leadtek Winfast1800H tuner card and have the remote working well in Mythbuntu 10.04. I don't have access to my system at the moment but can post the config files in a few days. 

In the mean time you could follow these instructions to make the lirc device static [http://parker1.co.uk/mythtv_tips.php](http://parker1.co.uk/mythtv_tips.php) This worked for me with 10.04. Typing cat /proc/bus/input/devices in the terminal will also let you know if your remote is been detected. (look for something like cx88 IR winfast)

I've also noted you have REMOTE_DRIVER="devinput" and post you link has REMOTE_DRIVER="dev/input"

goffa

---

### Post by goffa72 on 2010-07-09
As promised, here is my hardware config file -

```

# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Linux input layer (/dev/input/eventX)"
REMOTE_MODULES=""
REMOTE_DRIVER="dev/input"
#REMOTE_DEVICE="/dev/lirc0"
#REMOTE_DEVICE="/dev/input/event7"
REMOTE_DEVICE="/dev/input/winfastremote"
REMOTE_SOCKET=""
#REMOTE_LIRCD_CONF="devinput/lircd.conf.devinput"
REMOTE_LIRCD_CONF="/etc/lirc/lircd.conf"
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


```note I made my remote device static and called it winfastremote.

Hope this helps

---

### Post by adamc on 2010-07-09
A friend of mine bought a remote / usb receiver combo from Jaycar that's recognised as a keyboard. Think it was around the $30 mark from memory.

When I see him again, I'll ask for a model number.

---

### Post by ozybushwalker on 2010-07-09
> Typing cat /proc/bus/input/devices in the terminal will also let you know if your remote is been detected. (look for something like cx88 IR winfast)

Its detected.

> I've also noted you have REMOTE_DRIVER="devinput" and post you link has REMOTE_DRIVER="dev/input"

I get an "error in config file line 16" report when it reads REMOTE_DRIVER="devinput" and when it reads REMOTE_DRIVER="dev/input" but not when it reads REMOTE_DRIVER="devinput " (note the trailing space).

I've noticed older documentation reported a driver type of dev/input but lircd in Mythbuntu 10.04 doesn't accept that as parameter to the -H option. Unfortunately I've not been able to find any documentation on hardware.conf for lircd so its difficult to say what the argument to REMOTE_DRIVER should be.

---

### Post by ozybushwalker on 2010-07-09
goffa72: Thanks for your configuration file. I changed my hardware.conf so the first few lines read:
```
[FONT="Courier New"]# more /etc/lirc/hardware.conf
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Linux input layer (/dev/input/eventX)"
REMOTE_MODULES="" 

# Arguments which will be used when launching lircd
[/FONT]
```
and lircd reports:
```
[FONT="Courier New"]# lircd -n /etc/lirc/hardware.conf
lircd-0.8.6[4348]: error in configfile line 5
lircd-0.8.6[4348]: reading of file '/etc/lirc/hardware.conf' failed
lircd-0.8.6[4348]: reading of config file failed
lircd-0.8.6[4348]: lircd(default) ready, using /var/run/lirc/lircd
[/FONT]
```

I don't understand what's going on. Is the lircd error reporting broken, reporting the wrong location of the "error"?

---

### Post by ozybushwalker on 2010-07-09
adamc - thanks for the suggestion about the remote from Jaycar. I bought a Digitech WMCE remote control from Jaycar quite a few months ago and couldn't get it to work then. I've worked a bit on the other MCE remote I have but wasn't able to get it working. Maybe I should start other threads for those remotes.

---

### Post by goffa72 on 2010-07-09
what is line five of the config file, i think you have only posted the first two lines, the lines with # are ignored. It might help if you post the full config file along with the output of cat /proc/bus/input/devices

---

### Post by ozybushwalker on 2010-07-10
I have figured out the problem with hardware.conf. It has been described as a configuration file for lircd which it is, but not in the way I thought. I thought it was to be processed by lircd but it is processed by the startup script for lircd: /etc/init.d/lirc and its format is a shell script.

When it was starting lircd with -n I should have been doing so by something like
```
# lircd -H devinput -d /dev/input/wfrem /etc/lirc/lircd.conf
```

lircd can be started or stopped by ```
# service lirc start
``` or ```
# service lirc stop
```

---

