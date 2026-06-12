---
title: "Lirc and USB-UIRT Mythbuntu Hotplug Issue [SOLVED]"
date: 2011-09-21
forum: Mythbuntu
---

### Post by one30nav on 2011-09-21
This is a fix to an issue with Lirc remotes and USB-UIRT. It also compliments the Community Documentation link entitled, Lirc_USB-UIRT. The IR and remote no longer work after a hard or soft reboot. The alternate solution has been to plug the USB-UIRT in again after a reboot (irritating especially for the spouse). Putting a "sleep 15" in "/usr/bin/mythfrontend" fixes that issue.

Further detail if you need it:

Lirc_USB-UIRT link for initial setup (follow these directions): [https://help.ubuntu.com/community/Lirc_USB-UIRT]("https://help.ubuntu.com/community/Lirc_USB-UIRT") 

My hardware.conf file for reference (I use a Hauppauge remote):

```
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="none"
REMOTE_MODULES=""
REMOTE_DRIVER="uirt2_raw"
REMOTE_DEVICE=""
REMOTE_SOCKET=""
REMOTE_LIRCD_CONF=""
REMOTE_LIRCD_ARGS="-d /dev/ttyUSB0"

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
LOAD_MODULES="false"

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

Hotplug fix:

Again, USB-UIRT was failing to work after a reboot and I had to plug it in again for it to be recognized. I found out that the mythfrontend startup sequence was somehow interrupting the lirc startup.

I resolved this by putting a "sleep 15" delay in the mythfrontend script. After that, things work great! It's truly a wonderful IR receiver and I am experiencing near-wireless responsiveness.

So, make this change by: sudo nano /usr/bin/mythfrontend:

```
**[COLOR="Red"]sleep 15[/COLOR]**

pidof mythfrontend.real 2>&1 >/dev/null && wmctrl -a "MythTV Frontend" 2>/dev/null && exit 0

```
Hope this helps with your MythTV setups. Cheers, Al

---

### Post by one30nav on 2012-08-19
An alternate way to accomplish the delay and negate the need to re-input it after an update, is to use a bash script instead.

Refer to the following link:

[http://ubuntuforums.org/showthread.php?p=12182148#post12182148]("http://ubuntuforums.org/showthread.php?p=12182148#post12182148")

Cheers, Al

---

