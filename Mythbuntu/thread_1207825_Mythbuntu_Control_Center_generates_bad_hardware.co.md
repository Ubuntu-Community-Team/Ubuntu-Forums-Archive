---
title: "Mythbuntu Control Center generates bad hardware.conf (lirc) using Hauppauge HVR-110"
date: 2009-07-08
forum: Mythbuntu
---

### Post by KarlReichert on 2009-07-08
I couldn't find a mythbuntu bug tracker, so I will post the bug in here. If someone can give me a hint where to find the bugtracker, I will open a bug there, too.

I'm using a Hauppauge HVR-1100 TV card with the shipped remote (45 buttons, grey-black), the shipped IR receiver connected via this TV card.

Only a few buttons of this remote work, although I selected the right remote in MCC and it generated appropriate lirc configuration files for it.

The problem is, MCC generates a buggy hardware.conf. It looks like this:
```
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Hauppauge HVR-1100"
REMOTE_MODULES="devinput"
REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/lirc0"
REMOTE_LIRCD_CONF="hauppauge/lircd.conf.hauppauge"
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

With this config file, some buttons don't workm e.g. the Stop button on the remote. The first paragraph has to look like this:
```
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Hauppauge HVR-1100"
REMOTE_MODULES=""
REMOTE_DRIVER="dev/input"
REMOTE_DEVICE="/dev/input/event6"
REMOTE_LIRCD_CONF="hauppauge/lircd.conf.hauppauge"
REMOTE_LIRCD_ARGS=""
```
(Please note the differences in REMOTE_MODULES, REMOTE_DRIVER and REMOTE_DEVICE. Of course, the path in REMOTE_DEVICE has to be adopted to users' current setup. It can be determined by calling "cat /proc/bus/input/devices".)

This should be fixed, as I spent a lot of time to get my remote finally working.

Nevertheless, thanks a lot for your great work, mythbuntu developers!

PS: Another bug: I created the user "myth" at installation (don't know if this is important) and this user had no write access to /var/lib/mythtv/posters/. So I was able to download movie posters (at least it seamed like that, but they were not saved, as there was no write access) but when using the MythVideo module, no posters appeared. After changing the access rights of the directory, it worked fine. I would like to post this bug to the mythbuntu bugtracker, too.

---

### Post by superm1 on 2009-07-08
Please log all bugs at launchpad.net/mythbuntu ([http://mythbuntu.org/testingandreporting](http://mythbuntu.org/testingandreporting))

---

### Post by KarlReichert on 2009-07-08
Thank you very much for the link!

I reported the problem in [https://bugs.launchpad.net/bugs/397194]("https://bugs.launchpad.net/bugs/397194") and [https://bugs.launchpad.net/bugs/397190]("https://bugs.launchpad.net/bugs/397190").

---

