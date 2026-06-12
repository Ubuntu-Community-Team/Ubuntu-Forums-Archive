---
title: "nvram-wakeup and the new mithwelcome (8.10)"
date: 2008-11-05
forum: Mythbuntu
---

### Post by spoky99 on 2008-11-05
I'm using mythbuntu 8.10 I want use the nvram-wakeup.
My motherboard isn't official supported but, using the nvram-wakeup script, I found the correct nvram-wakeup.conf file and I understand that I could reboot the computer for make work nvram-wakeup but I'm not in able to understand how I could set mythwelcome and mythtv-setup for make work it.
this is my configuration of **mythwelcome**
*command to Set Wakeup Time:* [COLOR="Blue"]sudo /usr/sbin/nvram-wakeup -A -C /etc/nvram.wakeup.conf --settime $time[/COLOR]
*Wakeup time format:* [COLOR="Blue"]time_t[/COLOR]
*nvram-wakeup Restart Command:* [COLOR="Blue"]sudo /usr/sbin/grub-set-default 5[/COLOR]
*Command to reboot:* [COLOR="Blue"]sudo /sbin/reboot[/COLOR]
*Command to shutdown:* [COLOR="Blue"]sudo /sbin/poweroff[/COLOR]
*Command to run Xterm*  [COLOR="Blue"]xterm[/COLOR]
*Command to start frontend:* [COLOR="Blue"]/usr/bin/mythfrontend[/COLOR]

**mythtv-setup**
*Startup command:*[COLOR="Blue"] "blank"[/COLOR]
*Block shutdown before client connected:* [COLOR="Blue"]selected[/COLOR]
*Idle shutdown timeout (secs):*[COLOR="Blue"] 40[/COLOR]
*Max. wait for recording (min):* [COLOR="Blue"]10[/COLOR]
*Startup before rec. (secs):* [COLOR="Blue"]120[/COLOR]
*Wakeup time format:* [COLOR="Blue"]yyyy-MM-ddThh:mm[/COLOR]
*Command to set Wakeup Time:* [COLOR="Blue"]sudo -H /usr/bin/mythshutdown --setwakeup $time[/COLOR]
*Server halt command:*[COLOR="Blue"] sudo -H /usr/bin/mythshutdown --shutdown[/COLOR]
*Pre Shutdown check-command:* [COLOR="Blue"]/usr/bin/mythshutdown --check[/COLOR]

I start with mythwelcome, i select one recording program and when I exit from mythtv mythwelcome open it's windows, show me the future recorded program, start the count down and the computer goes down but... don't reboot immediately and don't write in the bios. What error I made?
I think that is a time format problem, I don't understand why in some configuration text i put the $time in some other time_t and... I set the time format to yyyy-MM-dd hh:mm.
If $time is one variable.. what application convert day, hour and minute in "seconds since unix epoch"?
thanks for help :D

---

### Post by spoky99 on 2008-11-09
nobody know the answer?

---

### Post by spoky99 on 2008-11-12
help me!

---

### Post by tohc1 on 2008-11-15
When I've had problems with mythwelcome not shutting down in the past, it's usually a permissions problem. Try running mythwelcome from a terminal. It may be that it's trying to get a password for the sudo commands.

I can't remember exactly what to do but I think you need to edit the sudoers file to allow those commands to be run without a password.

Hope that helps.

---

### Post by spoky99 on 2008-11-18
> **tohc1 said:**
> When I've had problems with mythwelcome not shutting down in the past, it's usually a permissions problem. Try running mythwelcome from a terminal. It may be that it's trying to get a password for the sudo commands.

I can't remember exactly what to do but I think you need to edit the sudoers file to allow those commands to be run without a password.

Hope that helps.
I still do it, I give the permission to execute all the command with sudo but without give the password.
But.. happens a strange thing. I edit visudo (sudo visudo) I add the path command for my username. I saved it
I add the user mythtv at admin group
I try using the command into terminal and.. they work using my username but using the mythtv username work "udo nvram-wakeup" but not work "grub-set-default".
I start from mythwelcome launcing it from a terminal (for to see the log), if I set the record of one program and exit, the computer open the mytwelcome windows with the count down (the computer is idle etc etc) but the count wen goes to 0 restart.
In the bash terminal i see this log:
[I]2008-11-18 18:24:23.641 Deleting UPnP client...
2008-11-18 18:25:06.035 MythWelcome received a SHUTDOWN_NOW event
2008-11-18 18:25:07.015 MythWelcome received a SHUTDOWN_NOW event
2008-11-18 18:25:06.055 MythWelcome received a SHUTDOWN_NOW event[/I]

I suppose that mytwelcome try to launch one sudo command but the computer don't accept it.
I don't know which command and who launch it, I don't know if is my user (luca) or the user mythtv (the old user used by old mythtv installation)
Every time I try all the sudo command write into mythwelcome -s and mythtv-setup and some time... they don't work, and I really don't know why

---

### Post by spoky99 on 2008-11-20
I understand the problem.
mythwelcome don't write into the bios for a permission problem.
I edited with "sudo visudo" the sudoers file for make executable all the sudo command needed and visudo make a strange thing.
There are two problem which user launch the command? I thunk that is not the user (luca in my case) but mythtv. The user mythtv aren't into the admin group and if you try to give it the permission of execute a sudo command whit visudo it give you an error. You could add mythtv user at the admin group and after modify the /etc/sudoers file (using sudo visudo)
Don't ask me why but you could repeat the list of sudo command for the user mythtv and the group mythtv. Enabling only the user mythtv it's in able to execute all the sudo command but not the "sudo grub-set-default" giving also the permission at the mythtv group mythwelcome start to work making shutdown the computer, setting the reboot in power off and writing into the bios the rc alarm.
I edited the first post with the correct setting that work for me.
I want make one how-to for help someone that want use mythbuntu in the same way, I had only a little problem.. I use a bad english! :D
this is my sudoers file (edit it with sudo visudo! correct you the wrong thing)

[I]> # /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

Defaults	env_reset

# Host alias specification 

# User alias specification 
User_Alias     MYTHSH = luca, mythtv

# Cmnd alias 
Cmnd_Alias     NVRAM = /usr/sbin/nvram-wakeup, /usr/sbin/grub-set-default, /usr/bin/mythshutdown, /sbin/halt, /sbin/reboot, /sbin/poweroff

# specification User privilege specification
root	ALL=(ALL) ALL
MYTHSH	ALL=NOPASSWD: NVRAM

# Uncomment to allow members of group sudo to not need a password 
# (Note that later entries override this, so you might need to move 
# it further down) 
%sudo ALL=NOPASSWD: ALL 

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL
%luca	ALL=NOPASSWD: NVRAM
%mythtv	ALL=NOPASSWD: NVRAM[/I]

---

