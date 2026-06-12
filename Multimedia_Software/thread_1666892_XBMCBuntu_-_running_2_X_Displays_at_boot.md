---
title: "XBMCBuntu - running 2 X Displays at boot"
date: 2011-01-14
forum: Multimedia Software
---

### Post by ztripez on 2011-01-14
I have a Asus EEE Box EB1007-W0067 running as htpc in my livingroom. Due to the limited hardware in the box i'm running Ubuntu server with a minimal xorg-xserver installation. The system autoinlogs into the xbmc user and spawns a xserver only running XBMC. Slim,fast and no fuzz ;). So far i'm realy happy about the setup. 1080p? no problem.

However, since there is no Spotify Addon for XBMC yet (in development but still way to buggy to use in a none development enviroment) i have to fallback to running Spotify native. And here comes the problem; I can't start Spotify in XBMC because XBMC will run it in the background. And since my wife must be able to use the system i've to come out with something easy to use. 

Is it possible to make ubuntu-server to boot into 2 diffrent X-Displays. One running XBMC and one running Spotify, i think my wife (and others) would be able to switch displays with ctr-alt-F7/F8.

---

### Post by tjones00 on 2011-01-14
Theoretically it's possible to enable two concurrent tty logins with separate X sessions. However using a nettop with an Intel NM10 card you would most likely not be able to get twin 1080p resolutions. This should depend on the max virtual resolution of the card and I doubt it's around the combined area of 1920x1080 + 1920x1080.

For the functionality you are describing you could setup a minimal openbox system and have hot keys toggle between xmbc and spotify. eg. press one combination it closes xbmc and launches spotify, press another (or the same one) and it does vice versa. This should just involve some minor bash scripting. 

Base openbox system:

Install server base system:

sudo apt-get install alsa-utils xinit openbox obmenu obconf

sudo apt-get install your perfered display manager or edit the default bash (startx) and .xsession entries to work without a display manager. To start up X without a displaymanager your default bash session will need to include startx and the .xsession file will have to point to openbox.

It's just easier to use a display manager and enable auto login the smaller ones are slim or lxdm installed via apt-get --no-recommends-install install lxdm.

Use nano or vi as a text editor to configure files.

For lxdm edit the lxdm.conf file at /etc/lxdm/lxdm.conf to enable auto login and openbox-session. For slim it should be something similar just find the master slim.conf file.

This will give you a minimal desktop environment with full audio/video and an terminal emulator x-term that you can use to install video drivers xbmc wget spotify whatever.

You can configure the hotkeys in openbox to call upon a script in either /home/user/bin/ or a shared bin directory to toggle between applications.

Possible script method for a hotkey toggle:
search process (figure out which of the two is currently running)
kill the active process
then launch other application with parameters like fullscreen etc.

The openbox wiki should be able to cover any issues you might have.


The openbox method would be much more plausible and friendlier with a nettop system and provide the same functionality you described. The downside is you'll have to create some scripts.

---

### Post by ztripez on 2011-01-15
Oh, thanks for all the info. Why i never thought of openbox (or any other lightweight windowmanager) will remain a mistery :P. I know that if run a Gnome install i will get flickers when i run 720p and above.

I'll try openbox. Thanks again.

---

### Post by tjones00 on 2011-01-15
I toy around with openbox installs myself hence why it seemed like a no brainer to me a lot of people never think of openbox.

For xbmc stand alone you need to install alsa-utils (will grab complete sound base) and xinit anyway. Adding openbox obmenu obconf only takes up about 30mb more. Remember with the openbox system you don't want to use the xbmc stand alone method. Just install xbmc like any other app. the display manager will handle the login (which is all xbmc stand alone really does). You can configure the openbox autostart.sh to launch the preferred  application first.

If you use lxdm make sure you use the --no-recommends-install option or it will drag the full lxde package in with it. With no recommends it's about 5mb I can't remember exactly I know slim is like 1-2mb.

---

### Post by ztripez on 2011-01-17
I got openbox and lxmd up and running, xbmc works like a charm. :).

However i can't get xbmc to autostart when i login as the xbmc user.

i've added the /home/xbmc/.config/openbox/autostart.sh 
with
/usr/bin/xbmc &
in it. But nothing happends.

also tried

#!/bin/bash
xbmc &

#!/bin/bash
sleep 5 && xbmc &


also chmod with +x but nothing.

---

### Post by tjones00 on 2011-01-17
Confirm xbmc is in /usr/bin/ the system will have several bin directories typically /usr/bin /usr/share/bin /home/user/bin. The ones you're most interested in using are /usr/share/bin and /home/user/bin (/home/xbmc/bin in your case)

The autostart.sh shouldn't require a full path if opening a terminal and typing xbmc launches the program xbmc & should suffice. Your default bash session bin definitions should handle the proper routing. So it short it a command works in a terminal emulator from the desktop it should work in autostart.sh. 

Edit: I see you tried xbmc &

Try this:

```
(sleep 4s && xbmc) &

exit 0
```Ubuntu is typical fast enough that a sleep isn't required. Perhaps you needed the exit 0.



Query the system for the all xbmc entries.

```
sudo find / -name xbmc
```It's most likely at /usr/share/bin/xbmc.

This thread might help you out for some scripting ideas.

[http://forum.xbmc.org/showthread.php?t=30230](http://forum.xbmc.org/showthread.php?t=30230)

Ignore the remote stuff start at 

> Create the following scripts. These actually start and kill XBMC.I'm not sure if startXMBC.sh is a script included with the standard xbmc install.

---

### Post by tjones00 on 2011-01-17
Ok since you're active on the forum right now I'll stop editing my original reply. Just didn't want to unnecessarily bump this I didn't notice you were active.

---

### Post by tjones00 on 2011-01-17
Try confirming the /home/xbmc/.config/openbox/autostart.sh is being called upon as well.

xterm should be your default terminal emulator.

```
(sleep 4s && xbmc) &

xterm &

exit 0
```At least this way if xterm pops up you know it ran the autostart.sh. If not you might have to configure some more default settings.

---

### Post by ztripez on 2011-01-17
It appears that autostart isn't running, when i added xterm nothing happend.

---

### Post by tjones00 on 2011-01-17
Try deleting the .config directory 

```
rm -rf ~/.config
```

To confirm it's gone

```
ls -a ~/
```


Then run obconf and obmenu (just start and close them)they should generate a new .config/openbox directory and tell openbox to use the local autostart.sh at ~/.config/openbox/autostart.sh

If it still doesn't work try editing the master openbox autostart.sh

It should be located at /etc/xdg/menus/openbox/autostart.sh or somewhere around there.

```
sudo find / -name autostart.sh
```

The openbox wiki should be able to tell you how to troubleshoot this I've never had an issue with the local autostart.sh after running obmenu/obconf.

Make sure you sudo chmod +x ~/.config/openbox/autostart.sh as well. It might just be a simple permissions error.

Test the script from a terminal via sh ~/.config/openbox/autostart.sh this should cut down on time if you're relogging just to test it.

---

### Post by ztripez on 2011-01-17
Omg! I feel so stupid.

I only changed "autologin" in the lxdm.conf

```
[base]
autologin=xbmc
session=/usr/bin/startlxde
# numlock=0
greeter=/usr/lib/lxdm/lxdm-greeter-gtk

[server]
# arg=/usr/bin/X -nr vt1

[display]
gtk_theme=Clearlooks
bg=/usr/share/backgrounds/default.png
bottom_pane=1
lang=1
theme=Industrial

[input]


```

as you can se i never started openbox but startlxde instead.
When i changed it to openbox-session everything worked.

 (oh! Just using openbox didn't work, had to use openbox-session to get the autorun.sh to fire up)

Sorry about that.. :|

Now let the scripting commence!

---

### Post by tjones00 on 2011-01-17
Ha! isn't that how it always is? At least after this experience you'll never make that mistake again ;)

Good luck with the rest of the project I'll be on vacation for two weeks starting tonight. If you need further help with scripting and openbox you might want to ask over at the crunchbang or archlinux forums. Alot of them use openbox. Both communities are rather friendly as well.

---

