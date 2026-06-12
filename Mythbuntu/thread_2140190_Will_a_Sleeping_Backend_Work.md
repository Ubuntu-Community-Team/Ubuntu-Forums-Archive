---
title: "Will a Sleeping Backend Work?"
date: 2013-04-28
forum: Mythbuntu
---

### Post by gga96 on 2013-04-28
Hi All,

I have implemented frontend sleep/wake with reference to [http://www.mythtv.org/wiki/Putting_mythfrontend_to_sleep](http://www.mythtv.org/wiki/Putting_mythfrontend_to_sleep) and now have implemented on the backend MythShutdown and MythWelcome with reference to [ttp://www.mythtv.org/wiki/ACPI_Wakeup]("http://www.mythtv.org/wiki/ACPI_Wakeup"). All works as advertised but I do have one problem.

[SIZE=2]Unfortunately[/SIZE] my backend machine is not Wake-On-LAN and a shutdown backend will not endear the family to the myth system.

Is it considered rational to have the backend go to sleep instead of shutting down and thus start up quickly?

Could MythShutdown, MythWecome be modified to achieve backend sleep and then wakeup to eth0 activity?

I am a linux newbie and would appreciate [SIZE=2]community [/SIZE]feedback.

Looking forward to responses with interest.

Thanks
Glen.

---

### Post by alien878 on 2013-04-30
If your backend doesn't support WOL, I don't think you will be able to wake it with eth activity.

Sleeping/Hibernating a backend-only system does work, but it needs WOL for the frontend system to be able to wake it up.  I'm not aware of any other way to automatically start the backend when a separate frontend starts.

Cheers,

Allen

---

### Post by gga96 on 2013-04-30
Hi Allen,

I am hoping the best I can do without WOL, is provide a remote control button that will wake the backend from sleep. This would provide the response time and simplicity for others to  physically do. 
I think the remove control button concept would be possible[SIZE=2], it would be similar to the frontend experience[/SIZE]. 

The more problematic is to get MythWelome and/or MythShutdown recompiled with the sleep option implemented. That is beyond my ability on the linux platform.  It may not be such a large task, the implementation on the frontend sleep function was relatively simple.

Regards
Glen

---

### Post by alien878 on 2013-04-30
Mythwelcome is designed to work on a combined FE/BE.  It isn't really going to work well on a backend only.  Normally, for a backend only, the backend settings (set wakeup command, shutdown command, etc.) are enough to set the wakeup time and shutdown.  Any frontends would use WOL to wake up the backend.

This might work with sleep if:
[LIST]
[*]The backend and all the HW recover from sleep (older HW doesn't recover well)
[*]Your PC supports a sort of ACPI wakeup from sleep (i.e. you can set the wakeup time and the PC will wakeup from sleeping to record)
[/LIST]

---

### Post by gga96 on 2013-04-30
[FONT=Verdana][COLOR=#222222]Hi 
Allen,
I have a combined BE/FE with one remote FE with more FEs on the way.

[/COLOR][/FONT][FONT=Verdana][COLOR=#222222]I may be able to get WOL working via a rec-configure of the BIOS. I will try this over the next couple of days. 

[/COLOR][/FONT][FONT=Verdana][COLOR=#222222]To have the BE restart from a sleep condition is much quicker than from a reboot and sleeping is a lot more user  friendly than a cold boot.  The major problem is to [FONT=Tahoma][COLOR=#000000]get MythWelome and/or MythShutdown recompiled with the sleep option implemented. 

[FONT=Tahoma][SIZE=2]I currently sleep the BE from the terminal with myth-suspend.sh from [FONT=Tahoma][SIZE=2][http://www.mythtv.org/wiki/Putting_mythfrontend_to_sleep](http://www.mythtv.org/wiki/Putting_mythfrontend_to_sleep)[/SIZE][/FONT][/SIZE][/FONT][/COLOR][/FONT][/COLOR][/FONT]
[FONT=Verdana][COLOR=#222222][FONT=Tahoma][COLOR=#000000][FONT=Tahoma][SIZE=2][FONT=Tahoma][SIZE=2]
[/SIZE][/FONT][/SIZE][/FONT][/COLOR][/FONT][/COLOR][/FONT]> 
#!/bin/sh
# This script uses dbus to tell HAL or UPower to suspend your computer
# Use one of the following lines; the UPower line worked for a Zotac ZBox running MythBuntu 12.04

dbus-send --system --print-reply --dest="org.freedesktop.UPower" /org/freedesktop/UPower org.freedesktop.UPower.Suspend
#dbus-send --system --print-reply --dest=org.freedesktop.Hal /org/freedesktop/Hal/devices/computer org.freedesktop.Hal.Device.SystemPowerManagement..Suspend int32:0

It may be woken by WOL or activity on the USB with a script using "echo "USB0" > /proc/acpi/wakeup".

Thanks for your interest.
Cheers
Glen

---

