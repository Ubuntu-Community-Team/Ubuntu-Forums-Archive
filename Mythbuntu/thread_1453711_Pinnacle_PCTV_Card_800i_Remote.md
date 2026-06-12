---
title: "Pinnacle PCTV Card 800i Remote"
date: 2010-04-13
forum: Mythbuntu
---

### Post by dewmanstl on 2010-04-13
Hello,

Wondering if anyone could give me some insight as to how I might get the remote that came with this card working. 
I have done the following:

 Removed the cx88 from the blacklist. from here. ```
/usr/share/hal/fdi/preprobe/20thirdparty/lirc.fdi
```

Then

```
cat /proc/bus/input/devices
```
which gave me this

```
I: Bus=0001 Vendor=11bd Product=0051 Version=0001
N: Name="cx88 IR (Pinnacle PCTV HD 800i)"
P: Phys=pci-0000:04:00.0/ir0
S: Sysfs=/devices/pci0000:00/0000:00:1e.0/0000:04:00.0/input/input5
U: Uniq=
H: Handlers=kbd event5 
B: EV=100003
B: KEY=c0000 142000 0 0 0 0 10000 190 1 1e0000 0 0 10000ff
```

I then made the edit

```
sudo nano /etc/lirc/hardware.conf
```
I added "devinput"
and modifed REMOTE_DEVICE 

which now looks like this

```
#Chosen Remote Control
REMOTE="Pinnacle Systems PCTV (pro) receiver"
REMOTE_MODULES=""
REMOTE_DRIVER="devinput"
REMOTE_DEVICE="/dev/input/event5"
REMOTE_SOCKET=""
REMOTE_LIRCD_CONF="pinnacle_systems/lircd.conf.pctv"
REMOTE_LIRCD_ARGS="''"

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

# Remote settings required by gnome-lirc-properties
REMOTE_MODEL="PinnacleSysPCTVRemote"
REMOTE_VENDOR="Pinnacle\ Systems\ PCTV\ Pro\ Remote"

# Receiver settings required by gnome-lirc-properties
RECEIVER_MODEL="Power\ Button"
RECEIVER_VENDOR="Linux\ Input\ Device"
```

and then finally restarted lirc
```

sudo /etc/init.d/lirc restart
```

So, now...None of the keys seem to work on the remote....

---

### Post by dewmanstl on 2010-04-14
bump.

Anyone?

---

