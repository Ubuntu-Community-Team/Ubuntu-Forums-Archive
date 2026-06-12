---
title: "disable wireless powersave permanently"
date: 2011-09-15
forum: Networking &amp; Wireless
---

### Post by doogiekd on 2011-09-15
dear friends, 

disabling the wireless powersave permanently is not working to correct random disconnects of the wireless usb dongle.

as the solution posted elsewhere on the internet instructs:

entering: 

"sudo iwconfig wlan0 power off" 

turns off the wireless powersave mode - which is confirmed to be the solution to the random disconnects.

to make the change permanent, the instructions say to create a file (if it not already there) titled "wireless" at "etc/pm/power.d/wireless." using the command:

sudo gedit /etc/pm/power.d/wireless."

adding the following to the file:

#!/bin/sh

/sbin/iwconfig wlan0 power off

and changing access permissions to the file by entering:

"sudo chmod +x /etc/pm/power.d/wireless"

the problem: i have followed these instructions exactly. entering "sudo iwconfig wlan0 power off" at each session i confirm that powersave is turned off. 

however, doing the permanent change as detailed above, rebooting the computer and entering "iwconfig" shows that powersave for wlan0 is "on."

the change is not made permanent.

any suggestions for permanently disabling wlan0 powersave mode?

thanx, 

k.

---

### Post by doogiekd on 2011-09-15
i was thinking if it was possible to just add:

"sudo iwconfig wlan0 power off" to the startup applications - but i don't know how to execute a startup command that requires the sudo password.

---

### Post by doogiekd on 2011-09-15
solved! 

there seems to be dozens of ways to run a sudo command at startup. i found this one to be the best:

edit the following file by entering: 

sudo gedit /etc/rc.local

add the command to disable wlan0 wireless:

"iwconfig wlan0 power off"

important! make sure there is a line at the very end that reads:

"exit 0"

this will bypass any errors and allow the system to continue to boot.

you can add other commands here as well - very useful.

it should look like this:

#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.
iwconfig wlan0 power off
exit 0

---

