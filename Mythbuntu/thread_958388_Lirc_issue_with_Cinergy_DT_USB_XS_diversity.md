---
title: "Lirc issue with Cinergy DT USB XS diversity"
date: 2008-10-25
forum: Mythbuntu
---

### Post by dwand on 2008-10-25
My problem came with the clean reinstall of mythbuntu using a Terratec Cinergy DT USB.
Everything works fine except the remote control support.
I used my previously working hardware.conf / lircd.conf and .lircrc files.
irw gives no feedback when lirc is running. Regenerating the lircd.conf file with irrecord failed as it showed no response to keypresses and quit with "gap not found" after a few seconds. So my guess was a flaw with the hardware.conf file (below).
However the remotes arrow keys and numpad work even if lirc is not runnin!
So i have absolutely no clue what is wrong.

my hardware.conf
device paths are confirmed to be correct.
```

# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Terratec Cinergy DT USB XS Diversity"
REMOTE_MODULES=""
REMOTE_DRIVER="devinput"
REMOTE_DEVICE="/dev/input/event6"
REMOTE_LIRCD_CONF="/etc/lirc/lircd.conf"
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
#LIRCMD_CONF=""

#Forcing noninteractive reconfiguration
#If lirc is to be reconfigured by an external application
#that doesn't have a debconf frontend available, the noninteractive
#frontend can be invoked and set to parse REMOTE and TRANSMITTER
#It will then populate all other variables without any user input
#If you would like to configure lirc via standard methods, be sure
#to leave this set to "false"
FORCE_NONINTERACTIVE_RECONFIGURATION="true"
START_LIRCMD=""

```

Is the kernel based IR support somewhat overriding lirc?!
Any help is greatly appreciated!

---

### Post by bui_a on 2010-11-04
I have exactly the same problem, using hardware.conf and lircd.conf that have been working in Karmic and Lucid. However, my arrow keys and number path do not work at all, with or without lirc.

---

### Post by freak42 on 2011-01-15
bump(!!)

I have absolutely the same problem... can't get it to output anything in irw :(

was working in mythbuntu 8.04 but not now in mythbuntu 10.10
any help?

---

