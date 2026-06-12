---
title: "Screen goes blank on boot"
date: 2008-05-26
forum: Mythbuntu
---

### Post by whiskeytits on 2008-05-26
Hello,

I just about have my Mythbuntu install set up the way I like it, but there is one nagging problem: The system only boots to the Mythtv frontend perhaps once every five times I restart my computer.  Now, to make this clear, all I get when I boot my computer is a black screen with a cursor.  

I can move my mouse around the screen, but there is nothing to click on, and I cannot left click to bring up any menu.  I am able to hit "Ctrl-Alt-Backspace" and bring up the "login" menu, but even when I try to log on as a different user here, I am returned back to the black screen.  Hence, all I can do is shut off my computer and hope that the frontend comes up the next time.

Further, hitting Alt-F2 to bring up the run-window does nothing.  At least if this was possible, perhaps I could still boot into the frontend from the terminal after typing in *gnome-terminal.*

Thanks for all of you help ahead of time!

---

### Post by tgm4883 on 2008-05-26
Perhaps the mythtv frontend is still loading?  How long do you wait until you restart it?  Have you checked top to see if it is running?

---

### Post by whiskeytits on 2008-05-26
I cannot get to top as I do not have access to the terminal or any sort of 'run' dialog box (ie: Alt-F2).

Additionally, I let it linger on this black screen for hours, and it does nothing.

Any other suggestions?

---

### Post by uMuppet on 2008-05-26
Try booting using the Recovery Mode and then fix x server option.  This will autodetect hardware for you.  Its a video driver problem this may fix it.

---

### Post by whiskeytits on 2008-05-28
> **uMuppet said:**
> Try booting using the Recovery Mode and then fix x server option.  This will autodetect hardware for you.  Its a video driver problem this may fix it.

I will try this.  Thank you.

Although, I am getting into a GUI of sorts, which makes me wonder if it is a video driver problem.  I get a blank screen, but there is a mouse cursor that I can move around on it, and additionally, I can bring the Session Manager menu using ctrl-alt-backspace.

---

### Post by dsbw on 2008-05-28
I've had this happen, weirdly enough, when the LAN wasn't connected. It'll just hang until I plug in the cat-5 cable.

---

### Post by whiskeytits on 2008-05-29
> **dsbw said:**
> I've had this happen, weirdly enough, when the LAN wasn't connected. It'll just hang until I plug in the cat-5 cable.

My patch cable is plugged in.  Nevertheless, I tried this in all variations (plugged, unplugged, replug after boot, etc) and still to no avail.

---

### Post by superm1 on 2008-05-29
When this happens, hit ctrl-alt-f1 or ssh into the box.  Look at the running processes and at relevant logs (~/.xsession-errors and /var/log/Xorg.0.log).

Also check for free space.  Very weird stuff happens if you are out.

---

### Post by jb5 on 2008-06-03
Hi - I'm experiencing the same problem with ca. 1 in 5 boots. Instead of the desktop and then MythWelcome starting up I get just a blank screen with mouse pointer that I can move around. NB This only started after upgrade to Hardy-64 from Gutsy-64.
```

<cntrl><Alt>backspace

```
Takes me back to a login screen and usually I can log in and the desktop then Mythwelcome will appear as normal.

However, to try and get a handle on the problem I tried the above suggestion```

<cntrl><alt>F1
```
which got me to a login prompt. After logging in as user I checked the memory & running processes using the command```
top
```
Memory was fine, over 3 Gb available for use and nothing appeared to be hogging CPU or Memory.

So took a look at the files following boot into blank screen and once again after normal boot```

cat ~/.xsession-errors > ~/xsession-errors.jbblankscreenboot
cat /var/log/Xorg-0-log > ~/Xorg.0.log.jbblankscreenboot
```
comparing the differences between Xorg-0-log after 'blank screen' boot and normal boot into desktop yields
```

jb@COLIN:~/Desktop$ diff -u Xorg.0.log.jbblankbootscreen Xorg.0.log.jbnormalboot 
--- Xorg.0.log.jbblankbootscreen	2008-06-03 13:32:37.000000000 +0100
+++ Xorg.0.log.jbnormalboot	2008-06-03 13:32:37.000000000 +0100
@@ -20,7 +20,7 @@
 Markers: (--) probed, (**) from config file, (==) default setting,
 	(++) from command line, (!!) notice, (II) informational,
 	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
-(==) Log file: "/var/log/Xorg.0.log", Time: Tue Jun  3 10:51:59 2008
+(==) Log file: "/var/log/Xorg.0.log", Time: Tue Jun  3 11:00:30 2008
 (==) Using config file: "/etc/X11/xorg.conf"
 (==) ServerLayout "Default Layout"
 (**) |-->Screen "Screen0" (0)
@@ -532,3 +532,5 @@
 (II) evaluating device (Generic Keyboard)
 (II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
 (II) Configured Mouse: ps2EnableDataReporting: succeeded
+SetClientVersion: 0 9
+SetKbdSettings - type: 20 rate: 30 delay: 500 snumlk: 0
jb@COLIN:~/Desktop$ 

```
The big difference, apart  from the timestamps, is the extra two lines that are missing from the 'blank screen boot'.

More striking is the difference for the xsession-errors files under the two conditions, which shows
Blank Screen with mouse pointer
```

/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_GB.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.

2008-06-03 10:52:06.939 Using runtime prefix = /usr, libdir = /usr/lib
2008-06-03 10:52:06.977 Empty LocalHostName.
2008-06-03 10:52:06.977 Using localhost value of eric
2008-06-03 10:52:06.994 New DB connection, total: 1
2008-06-03 10:52:06.999 Connected to database 'mythconverg' at host: localhost
2008-06-03 10:52:07.000 Closing DB connection named 'DBManager0'
2008-06-03 10:52:07.001 Connected to database 'mythconverg' at host: localhost
irexec: no process killed
/usr/bin/startxfce4: X server already running on display :0
```

and for normal boot to desktop following complete reboot
```

/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_GB.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.

2008-06-03 11:00:37.900 Using runtime prefix = /usr, libdir = /usr/lib
2008-06-03 11:00:37.997 Empty LocalHostName.
2008-06-03 11:00:37.997 Using localhost value of eric
irexec: no process killed
2008-06-03 11:00:38.064 New DB connection, total: 1
2008-06-03 11:00:38.070 Connected to database 'mythconverg' at host: localhost
2008-06-03 11:00:38.072 Closing DB connection named 'DBManager0'
2008-06-03 11:00:38.072 Connected to database 'mythconverg' at host: localhost
/usr/bin/startxfce4: X server already running on display :0
** Message: Querying XINPUT extension
** Message: XINPUT extension found
** Message: Querying Xkb extension
** Message: Xkb extension found
** Message: Querying XF86Misc extension
** Message: XF86Misc extension found
** Message: Querying Xkb extension
** Message: Xkb extension found
** Message: another SSH agent is running at: /tmp/ssh-kPPsjT6380/agent.6380
ERROR: trackerd already running on your session dbus - exiting...
2008-06-03 11:00:43.515 Using runtime prefix = /usr, libdir = /usr/lib
2008-06-03 11:00:43.865 XScreenSaver support enabled
2008-06-03 11:00:43.866 DPMS is active.
2008-06-03 11:00:43.896 Empty LocalHostName.
2008-06-03 11:00:43.896 Using localhost value of eric


2008-06-03 11:00:43.907 New DB connection, total: 1
2008-06-03 11:00:43.912 Connected to database 'mythconverg' at host: localhost
2008-06-03 11:00:43.914 Closing DB connection named 'DBManager0'
2008-06-03 11:00:43.915 Primary screen 0.
2008-06-03 11:00:43.915 Connected to database 'mythconverg' at host: localhost
2008-06-03 11:00:43.917 Using screen 0, 1024x768 at 0,0
2008-06-03 11:00:44.207 Primary screen 0.
2008-06-03 11:00:44.208 Using screen 0, 1024x768 at 0,0
2008-06-03 11:00:44.267 Switching to square mode (blue)
2008-06-03 11:00:44.726 Using the OpenGL painter
2008-06-03 11:00:44.760 JoystickMenuClient Error: Joystick disabled - Failed to read /home/jb/.mythtv/joystickmenurc
2008-06-03 11:00:44.762 New DB connection, total: 2
2008-06-03 11:00:44.762 Connected to database 'mythconverg' at host: localhost
2008-06-03 11:00:44.763 lirc init success using configuration file: /home/jb/.mythtv/lircrc
QSettings::sync: filename is null/empty
QSettings::sync: filename is null/empty
QSettings::sync: filename is null/empty
QSettings::sync: filename is null/empty
QSettings::sync: filename is null/empty
QSettings::sync: filename is null/empty
QSettings::sync: filename is null/empty
QSettings::sync: filename is null/empty
QSettings::sync: filename is null/empty
QSettings::sync: filename is null/empty
2008-06-03 11:00:47.298 XMLParse::LoadTheme using /usr/share/mythtv/themes/default/welcome-ui.xml
2008-06-03 11:00:47.520 Connecting to backend server: 127.0.0.1:#### (try 1 of 5)
2008-06-03 11:00:47.535 Using protocol version 40
2008-06-03 11:00:49.202 mythshutdown --startup returned: 1
```

I'm afraid this is rather over my head, but does this shed any light on the problem for any experts out there?

---

### Post by laga on 2008-06-03
Hum.

I wonder if this is a race condition between the mysqld and X/mythwelcome.

What happens if you reorder the start up a bit, eg ```
sudo mv /etc/rc2.d/S30gdm /etc/rc2.d/S99gdm
```?

---

### Post by robgue on 2008-06-04
I'm getting the same black screen with the mouse cursor only also. rebooted about 3 times now its back to normal.:confused:

---

### Post by jb5 on 2008-06-04
> **laga said:**
> Hum.

I wonder if this is a race condition between the mysqld and X/mythwelcome.

What happens if you reorder the start up a bit, eg ```
sudo mv /etc/rc2.d/S30gdm /etc/rc2.d/S99gdm
```?

Unfortunately, that doesn't fix the problem. Failed again this morning.
So I ```
<alt><ctrl>F1
```
to get me to a login prompt again and swapped it back to S30gdm. Then when I ```
sudo reboot
```I noticed a message informing me that gdm was going to shut down, and then a few seconds later [OK] appears and then proceeds to reboot. I don't know if that adds anything or not?

---

### Post by jb5 on 2008-06-13
Anybody any further thoughts on this?

Just had to reboot three times, after several attempts to ctl+alt+backspace to try and fix the problem!

---

### Post by jb5 on 2008-06-21
OK no solution yet but I have found a slightly better way to deal with the problem, other than re-booting or logging out/in.

ctrl+alt+F1, and log in at the prompt. Then:-```
sudo /etc/init.d/gdm stop
sudo /etc/init.d/gdm start
```

NB - Wait until gdm has stopped before trying to start again. ;)

This method comes into its own when the machine has woken to start a recording and has booted into the 'blank screen', as it will not disturb the current recording, unlike logging out or rebooting.

---

### Post by jb5 on 2008-07-19
OK - Ten days without the problem recurring.

I noticed that I was running the 169.XXXX version of the nvidia driver.
Installed [Envy](http://albertomilone.com/nvidia_scripts1.html) and used the program to update the driver to version 173.XXXXX

So far no blank screens! :)

[Aside]To determine the driver version :- 
In a terminal type```
nvidia-settings
``` maximise the window, and one of the options on the left hand side of the screen will display info about your card and driver.

---

