---
title: "Network doesn't work after standy or hibernate"
date: 2011-03-26
forum: Networking &amp; Wireless
---

### Post by wkcchampion on 2011-03-26
Hello. I have ubuntu 10.10 on my old desktop, I'm encountering  this problem.

If I put the computer on standy or hibernation, the network does no longer work after the system is resumed back!

I  tried both the current 28 and the previous 27 kernels, but it occurs anyway.

This computer has only an Ethernet/cable connection to my router. No Wi-fi. The motherboard is an old KV( 3rd eye by Abit.

My netbook has Ubuntu netbook edition and the issue doesn't take place there.

Thanks for the help

---

### Post by wkcchampion on 2011-04-02
bump anyone?

---

### Post by wkcchampion on 2011-04-02
> **aruna29 said:**
> I think you have to try pressing and holding the PC’s power button for five seconds or more.  On a PC that's configured to Suspend or Hibernate with a press of the  power button, holding down the power button will usually reset and  reboot it.

please, a serious answer! That will abruptly power down my computer...

---

### Post by matt_symes on 2011-04-02
Hi

After coming out of suspend open a terminal and type

```
sudo /etc/init.d/networking restart
```

Enter your password. It will not be echoed to the screen. Does that bring it back up ?

Kind regards.

---

### Post by wkcchampion on 2011-04-02
> **matt_symes said:**
> Hi

After coming out of suspend open a terminal and type

```
sudo /etc/init.d/networking restart
```Enter your password. It will not be echoed to the screen. Does that bring it back up ?

Kind regards.

Hi Matt,
I tried your solution. Unfortunately, it doesn't seem to work.

This is what appears in the terminal:

```

marco@casa:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          Ignoring unknown interface eth0=eth0.
                                                                         [ OK ]
marco@casa:~$

```

The network is still down after I've launched the command.

---

### Post by matt_symes on 2011-04-02
Hi

Please post the output of (case sensitive)

```
lspci -nnk | grep -A3 Network
```

EDIT: Hold on i have just realised you only have a wired network connection

Try this one instead.

```
**lspci -nnk | grep -A3 Ethernet**
```

Kind regards

---

### Post by wkcchampion on 2011-04-02
> **matt_symes said:**
> Hi

Please post the output of (case sensitive)

```
lspci -nnk | grep -A3 Network
```EDIT: Hold on i have just realised you only have a wired network connection

Kind regards


it seems to do nothing....
```

marco@casa:~$ lspci -nnk | grep -A3 Network
marco@casa:~$

```

---

### Post by matt_symes on 2011-04-02
Hi

Yes i was editing my post. I did not realise you had an ethernet connection and no wireless connection.

Please post

```
lspci -nnk | grep -A3 Ethernet
```

Kind regards

---

### Post by wkcchampion on 2011-04-02
> **matt_symes said:**
> Hi

Yes i was editing my post. I did not realise you had an ethernet connection and no wireless connection.

Please post

```
lspci -nnk | grep -A3 Ethernet
```Kind regards

Alright, here it is

```

marco@casa:~$ lspci -nnk | grep -A3 Ethernet
00:0e.0 Ethernet controller [0200]: VIA Technologies, Inc. VT6120/VT6121/VT6122 Gigabit Ethernet Adapter [1106:3119] (rev 11)
    Subsystem: ABIT Computer Corp. Device [147b:1413]
    Kernel driver in use: via-velocity
    Kernel modules: via-velocity
marco@casa:~$  

```

---

### Post by matt_symes on 2011-04-02
Hi

After suspend on resume, open a termina and type

```
sudo rmmod via-velocity
sudo modprobe via-velocity
```

What are your connection speed like after that ?

Kind regards

---

### Post by wkcchampion on 2011-04-02
> **matt_symes said:**
> Hi

After suspend on resume, open a termina and type

```
sudo rmmod via-velocity
sudo modprobe via-velocity
```What are your connection speed like after that ?

Kind regards

it works. The network gets back working. Any way to do this automatically on resume?

---

### Post by matt_symes on 2011-04-02
Hi

> **wkcchampion said:**
> it works. The network gets back working. Any way to do this automatically on resume?

Yes, but i will not be able to look at this for a couple of hours. 

I cant remember the exact file to put it in. I think it's one of the acpi configuration files but i will need to check.

Bump this thread so it appears in my user_cp area and i will be able to find it.

Kind regards

---

### Post by wkcchampion on 2011-04-02
> **matt_symes said:**
> Hi



Yes, but i will not be able to look at this for a couple of hours. 

I cant remember the exact file to put it in. I think it's one of the acpi configuration files but i will need to check.

Bump this thread so it appears in my user_cp area and i will be able to find it.

Kind regards

no hurry, I'll wait! Thanks

---

### Post by matt_symes on 2011-04-02
Hi

Can you post the output of

```
cat /etc/default/acpi-support
```

between code tags.

Kind regards

---

### Post by wkcchampion on 2011-04-02
> **matt_symes said:**
> Hi

Can you post the output of

```
cat /etc/default/acpi-support
```between code tags.

Kind regards

```

marco@casa:~$ cat /etc/default/acpi-support
#
# Configuration file for the acpi-support package
#
#
# The acpi-support package is intended as "glue" to make special functions of
# laptops work. Specifically, it translates special function keys for some
# laptop models into actions or generic function key presses.
#


#
# Suspend/hibernate method
# ------------------------
#
# When gnome-power-manager or klaptopdaemon are running, acpi-support will
# translate the suspend and hibernate keys of laptops into special "suspend"
# and "hibernate" keys that these daemons handle.
#
# Only in situations where there is no gnome-power-manager or klaptopdaemon
# running, acpi-support needs to perform suspend/hibernate in some other way.
# There are several options for this. The options are:
#
# dbus-pm:
#    Perform suspend and hibernate actions via a DBUS request to the power
#    management daemon. This works for power management daemons that we don't
#    know of. (For gnome-power-manager and klaptopdaemon this will do nothing,
#    since those will be detected when they are running, and triggered using
#    a virtual keypress.)
#
# dbus-hal:
#    Perform suspend and hibernate actions via a DBUS request directly to HAL,
#    bypassing any running power management daemons.
#
# pm-utils:
#    Use pm-suspend and pm-hibernate to suspend and hibernate. (The dbus method
#    normally results in this as well, but calls through dbus. Use this option
#    only if you don't have dbus installed.)
#
# hibernate:
#    Use the hibernate package to suspend and hibernate.
#
# acpi-support:
#    Use the legacy built-in suspend/hibernate support. (DEPRECATED)
# 
# none:
#    Do not attempt to suspend/hibernate. Set SUSPEND_METHODS="none" to
#    disable suspend/hibernate handling in acpi-support.
#
# If you specify dbus or pm-utils, the result will normally be the same as when
# you suspend from your desktop environment. If you specify "hibernate" or
# "acpi-support", be aware that this probably does not match what your desktop
# environment would do (unless you have managed to configure something so that
# the DBUS power management interfaces call the hibernate package).
#
#
# Please specify a space separated list of options. The recommended value is
# "dbus pm-utils"
#
SUSPEND_METHODS="dbus-pm dbus-hal pm-utils"



#
# LEGACY BUILT IN SUSPEND SUPPORT (DEPRECATED)
# --------------------------------------------
#
# These options only work for the "acpi-support" suspend method. This is NOT
# recommended, but is retained for backward compatibility reasons.
#

# Comment the next line to disable ACPI suspend to RAM
ACPI_SLEEP=true

# Comment the next line to disable suspend to disk
ACPI_HIBERNATE=true

# Change the following to "standby" to use ACPI S1 sleep, rather than S3.
# This will save less power, but may work on more machines
ACPI_SLEEP_MODE=mem

# Add modules to this list to have them removed before suspend and reloaded
# on resume. An example would be MODULES="em8300 yenta_socket"
#
# Note that network cards and USB controllers will automatically be unloaded 
# unless they're listed in MODULES_WHITELIST
MODULES=""

# Add modules to this list to leave them in the kernel over suspend/resume
MODULES_WHITELIST=""

# Should we save and restore state using the VESA BIOS Extensions?
SAVE_VBE_STATE=true

# The file that we use to save the vbestate
VBESTATE=/var/lib/acpi-support/vbestate

# Should we attempt to warm-boot the video hardware on resume?
POST_VIDEO=true

# Save and restore video state?
# SAVE_VIDEO_PCI_STATE=true

# Should we switch the screen off with DPMS on suspend?
USE_DPMS=true

# Use Radeontool to switch the screen off? Seems to be needed on some machines
# RADEON_LIGHT=true

# Uncomment the next line to switch away from X and back again after resume.
# This is needed for some hardware, but should be unnecessary on most.
# DOUBLE_CONSOLE_SWITCH=true

# Set the following to "platform" if you want to use ACPI to shut down
# your machine on hibernation
HIBERNATE_MODE=shutdown

# Comment this out to disable screen locking on resume
LOCK_SCREEN=true

# Uncomment this line to have DMA disabled before suspend and reenabled
# afterwards
# DISABLE_DMA=true

# Uncomment this line to attempt to reset the drive on resume. This seems
# to be needed for some Sonys
# RESET_DRIVE=true

# Add services to this list to stop them before suspend and restart them in 
# the resume process.
STOP_SERVICES=""

# Restart Infra Red services on resume - off by default as it crashes some
# machines
RESTART_IRDA=false

# Add to this list network interfaces that you don't want to be stopped
# during suspend (in fact any network interface whose name starts with
# a prefix given in this list is skipped)
SKIP_INTERFACES="dummy qemu"

# Note: to enable "laptop mode" (to spin down your hard drive for longer
# periods of time), install the laptop-mode-tools package and configure
# it in /etc/laptop-mode/laptop-mode.conf. 
marco@casa:~$

```

---

### Post by matt_symes on 2011-04-02
Hi

That looks good.  

I can't actually track down the info i read on this so this might not be the correct technique but it's worth a try. If not we can try something else.

I think this is what we need to do.

Open a terminal and type

```
sudo nano /etc/pm/10-wireless
```

Enter your password as normal.

Type 

```
SUSPEND_MODULES="via-velocity"
```

Ctrl + o to save and ctrl + x to exit.

Suspend and resume.

Kind regards

---

### Post by wkcchampion on 2011-04-02
> **matt_symes said:**
> Hi

That looks good.  

I can't actually track down the info i read on this so this might not be the correct technique but it's worth a try. If not we can try something else.

I think this is what we need to do.

Open a terminal and type

```
sudo nano /etc/pm/10-wireless
```Enter your password as normal.

Type 

```
SUSPEND_MODULES="via-velocity"
```Ctrl + o to save and ctrl + x to exit.

Suspend and resume.

Kind regards

nope :(

---

### Post by matt_symes on 2011-04-02
Hi

> **wkcchampion said:**
> nope :(

Don't worry. We'll fix it. 

I might have to look at this tomorrow though. I have a party to go to very soon.

Remove that file you created.

Kind regards

---

### Post by matt_symes on 2011-04-02
Hi

Try this. Create a file called /etc/pm/sleep.d/10_wireless_sleep

```
sudo nano /etc/pm/sleep.d/10_wireless_sleep
```

Add this code.

```
#!/bin/sh

if [ "$1" = "suspend" ]
then
        modprobe -r via-velocity
fi

if [ "$1" = "resume" ]
then
        modprobe via-velocity
fi
```

Make the script executable

```
sudo chmod +x /etc/pm/sleep.d/10_wireless_sleep
```

Suspend and resume.

If that does not work there is something else we can try. If it does work we can clean up the script tomorrow.

Kind regards

---

### Post by wkcchampion on 2011-04-03
> **matt_symes said:**
> Hi

Try this. Create a file called /etc/pm/sleep.d/10_wireless_sleep

```
sudo nano /etc/pm/sleep.d/10_wireless_sleep
```Add this code.

```
#!/bin/sh

if [ "$1" = "suspend" ]
then
        modprobe -r via-velocity
fi

if [ "$1" = "resume" ]
then
        modprobe via-velocity
fi
```Make the script executable

```
sudo chmod +x /etc/pm/sleep.d/10_wireless_sleep
```Suspend and resume.

If that does not work there is something else we can try. If it does work we can clean up the script tomorrow.

Kind regards

It works - the machine is online after the resume. I did a bandwidth test and the speed looks normal. I think it is solved!
Maybe take a note on this for future kernels

---

### Post by matt_symes on 2011-04-03
Hi

It's not the best script in the world. It was just more for testing.

If you want a better updated script reply and i will post one. I may post one anyway.

Glad it's fixed though.

Kind regards

---

### Post by wkcchampion on 2011-04-03
> **matt_symes said:**
> Hi

It's not the best script in the world. It was just more for testing.

If you want a better updated script reply and i will post one. I may post one anyway.

Glad it's fixed though.

Kind regards

Well, ok then... post one as u have time Does that script make my computer "believe" that the wifi has morphed into an ethernet connection?

---

### Post by matt_symes on 2011-04-03
Hi

> **wkcchampion said:**
> Well, ok then... post one as u have time Does that script make my computer "believe" that the wifi has morphed into an ethernet connection?

:D No morphing. I will post it in a couple of hours. It will give me something to do on a Sunday morning.

Kind regards

---

### Post by matt_symes on 2011-04-03
Hi

Try this script. It should handle both suspend and hibernate.

```
#!/bin/sh

case "{$1}" in
        suspend|hibernate)
                # Unload via-velocity
                modprobe -r via-velocity   
                ;;
        resume|thaw)
                # Reload via-velocity.
                modprobe via-velocity   
                ;;
esac
```

Call it the same name as before and make sure it's executable with chmod.

Kind regards

---

### Post by wkcchampion on 2011-04-03
> **matt_symes said:**
> Hi

Try this script. It should handle both suspend and hibernate.

```
#!/bin/sh

case "{$1}" in
        suspend|hibernate)
                # Unload via-velocity
                modprobe -r via-velocity   
                ;;
        resume|thaw)
                # Reload via-velocity.
                modprobe via-velocity   
                ;;
esac
```Call it the same name as before and make sure it's executable with chmod.

Kind regards
This one doesn't work. shall i get back to the old one?

---

### Post by matt_symes on 2011-04-03
Hi

I'll test it now. Maybe i should have done that first. Wait for a little while and i will get back to you.

Kind regards.

---

### Post by matt_symes on 2011-04-03
Hi

Try this.

```
sudo nano /etc/pm/sleep.d/10_wireless_sleep
```

copy and paste this

```
#!/bin/sh

case "$1" in
        suspend|hibernate)
                # Unload via-velocity
                rmmod via-velocity 
#              touch /home/matthew/suspending
                ;;
        resume|thaw)
                # Reload via-velocity.
                modprobe via-velocity 
#                touch /home/matthew/resuming
                ;;
esac
```

make it executable.

```
sudo chmod 751 /etc/pm/sleep.d/10_wireless_sleep
```

You can test to see if it's being called by removing the # infront of the touch /home/matthew/..... commands and changing matthew to your user name.

That created the two files in my home directory after hibernating.

```
matthew@matthew-laptop:~$ ls ~/*ing
/home/matthew/resuming  /home/matthew/suspending
matthew@matthew-laptop:~$
```

Hopefully that will fix it for you.

Kind regards

---

### Post by wkcchampion on 2011-04-03
it did it! Thank you!

---

### Post by brute.force1700 on 2011-12-10
If everything else fails, use the following script which unloads and loads all module in your system. Remember this script is dangerous to use on production and use it at ur own risk.
Also It may not work for you, but it worked for me. Just my 2 cents.


#!/bin/bash

lsmod >./lsmod.txt_everythingworking
cat ./lsmod.txt_everythingworking | while read LINE
do 
MODULE_NAME=`echo $LINE | awk '{print $1}'`
sudo rmmod $MODULE_NAME
sudo modprobe $MODULE_NAME
done

---

