---
title: "Autostart xboxdrv on boot (Xbox controller driver in XBMC)"
date: 2009-08-12
forum: Multimedia Software
---

### Post by driesel on 2009-08-12
Hi all,

I've just finished installing the xboxdrv userspace driver ([[COLOR="DarkOrange"]http://pingus.seul.org/~grumbel/xboxdrv/[/COLOR]]("http://pingus.seul.org/~grumbel/xboxdrv/")) for Xbox 360 USB (wired) controller support.  I'm working with minimal Ubuntu 9.04 x64.  I'm trying to enable the controller from boot and use it in XBMC.

My references for installation: [http://www.stolennotebook.com/anthony/category/xbmc/]("http://www.stolennotebook.com/anthony/category/xbmc/"), [http://www.aranea.be/blog/?p=42]("http://www.aranea.be/blog/?p=42")

So far I've successfully compiled the driver and mapped the keys in Keymap.xml for XBMC.  When I run the driver as root in terminal I can immediately use it in XBMC.
Now what I want to do is have the driver loaded after boot without going into terminal or gaining access via SSH (like I do without leaving XBMC on the host PC).

These are the commands I enter after every boot to load the driver (with Putty SSH client on Windows PC):
```
cd ~/xboxdrv
```
```
sudo ./xboxdrv --id 0 -s -l 2 --dpad-as-button --deadzone 12000
```
Or just:
```
sudo ./xboxdrv/xboxdrv --id 0 -s -l 2 --dpad-as-button --deadzone 12000
```

Somehow it needs root priviliges to work as this is what I get when I run as a normal user:
```
xbmc@miniHTPCion330:~$ ./xboxdrv/xboxdrv --id 0 -s -l 2 --dpad-as-button --deadz                                                                                                                                one 12000
xboxdrv 0.4.8
Copyright (C) 2008 Ingo Ruhnke <grumbel@gmx.de>
License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.

USB Device:        002:004
Controller:        "Microsoft Xbox 360 Controller" (idVendor: 0x045e, idProduct:                                                                                                                                 0x028e)
Controller Type:   Xbox360
Deadzone:          12000
Trigger Deadzone:  0
Rumble Debug:      off
Rumble Speed:      left: -1 right: -1
LED Status:        2
Square Axis:       no
ButtonMap:         none
AxisMap:           none
RelativeAxisMap:   none
AutoFireMap:       none
RumbleGain:        255
ForceFeedback:     disabled
Error: Error couldn't claim the USB interface: Operation not permitted
Try to run 'rmmod xpad' and start xboxdrv again.
```

Running as root ... no problems at all:
```
xbmc@miniHTPCion330:~$ sudo ./xboxdrv/xboxdrv --id 0 -s -l 2 --dpad-as-button --deadzone 12000
xboxdrv 0.4.8
Copyright (C) 2008 Ingo Ruhnke <grumbel@gmx.de>
License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.

USB Device:        002:004
Controller:        "Microsoft Xbox 360 Controller" (idVendor: 0x045e, idProduct: 0x028e)
Controller Type:   Xbox360
Deadzone:          12000
Trigger Deadzone:  0
Rumble Debug:      off
Rumble Speed:      left: -1 right: -1
LED Status:        2
Square Axis:       no
ButtonMap:         none
AxisMap:           none
RelativeAxisMap:   none
AutoFireMap:       none
RumbleGain:        255
ForceFeedback:     disabled

Starting with uinput... done

Your Xbox/Xbox360 controller should now be available as:
  /dev/input/js0
  /dev/input/event6

Press Ctrl-c to quit
```

What do I need to do to autostart the xboxdrv program (and leave it running) as root after booting?

P.S. Also I need to load the uinput kernel module.  I added it to /etc/modules like below, but it still isn't loaded.
```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

loop
lp
rtc
joydev # for joystick devices
uinput # for creating userspace drivers
```

```
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
modprobe uinput
chmod a+r /dev/input/uinput

exit 0
```
So to fix this I made some changes to /etc/rc.local (see above) and that works.  I understand this script is loaded relatively late in the booting process, so this can't be ideal.  Why isn't uinput loaded on boot in /etc/modules?

greetings,
driesel

---

### Post by driesel on 2009-08-12
Okay, I think I've found something that works for me...

First I added the standard user (being "xbmc") to the root group:
```
sudo usermod -a -G root xbmc
```

Then I created a file called "55-permissions-uinput.rules" in /etc/udev/rules.d with the following contents:
```
KERNEL=="uinput", MODE="0660", GROUP="root"
```

Finally I altered /etc/rc.local
```
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

./home/xbmc/xboxdrv/xboxdrv --id 0 -s -l 2 --dpad-as-button --deadzone 12000

exit 0
```

I'm still a very entry-level linux user.  I made this work using bits and pieces from other posts and the xboxdrv readme.
This is working really great for me, but I'm still open for more elegant solutions.  Any advice is more than welcome!

greetings,
driesel

---

### Post by souldrinker014 on 2009-08-15
> **driesel said:**
> Hi all,
Why isn't uinput loaded on boot in /etc/modules?


I had this prob myself and found a error dmesg about uinput choking on a unknown token '#'. So I modified my /etc/modules to look like the following. 

```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

loop
lp
rtc
# for joystick devices
joydev 
# for creating userspace drivers
uinput 
```

Now it loads each time on boot for me. I hope this helps you out.

---

### Post by MetalMusicAddict on 2009-12-30
Hey driesel. Is this still working for you in Karmic?

I have a minimal XBMC install and I'm also trying to start my wired controller @logon.

Works great if I start it with sudo after but your info above (as well as xboxdrv's README) doesn't seem to work right now.

Something change again in Karmic?

EDIT: For some reason, I had better luck putting it in ~/.xsession than rc.local. I wonder why? In any case, that worked for me.

[SIZE="1"]mbc@htpc:~$ nano .xsession[/SIZE]
```

xbmc --standalone &
exec /home/mbc/xboxdrv/xboxdrv --wid 0 -s -l 2 --dpad-as-button --deadzone 12000
```

---

