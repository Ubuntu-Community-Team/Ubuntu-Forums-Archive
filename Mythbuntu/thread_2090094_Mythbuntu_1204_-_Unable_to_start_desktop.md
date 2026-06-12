---
title: "Mythbuntu 12:04 - Unable to start desktop"
date: 2012-12-01
forum: Mythbuntu
---

### Post by MrHyde on 2012-12-01
Hi,  I have installed Mythbuntu 12.04 and everything has been working fine for over 3 months.  Today, I rebooted my machine as I had applied some patches that requires a reboot - I think new kernel 0.34.

Since then, I have been having problems.  On startup, the screen just froze and I did not get my expected Mythfrontend screen.  After nearly a day of doing things including uninstalling, installing graphic drivers and change Xorg.conf; I think the problem is actually with lightdm.  

I have uninstalled and re-installed lightdm as well as mythbuntu-desktop and have even reinstalled mythbuntu-default-settings with no luck.  The current state of my machine is that after startup, I get a login screen showing my name, followed by Other and then a field for a password.  After I enter my password, the screen goes blank for a second and then returns to the login screen.

Below are some of the log files and conf files that I believe may help in resolving this.

lightdm.conf
```

[SeatDefaults]
autologin-user=vivek
greeter-session=lightdm-gtk-greeter
user-session=mythbuntu
allow-guest=false

```

I previously had the greeter session pointing to mythbuntu-lightdm-gtk-greeter, but that failed with an error message that it could not find a session file for it.

lightdm.log on startup
```

[+0.03s] DEBUG: Logging to /var/log/lightdm/lightdm.log
[+0.03s] DEBUG: Starting Light Display Manager 1.2.1, UID=0 PID=1207
[+0.03s] DEBUG: Loaded configuration from /etc/lightdm/lightdm.conf
[+0.03s] DEBUG: Using D-Bus name org.freedesktop.DisplayManager
[+0.03s] DEBUG: Registered seat module xlocal
[+0.03s] DEBUG: Registered seat module xremote
[+0.03s] DEBUG: Adding default seat
[+0.03s] DEBUG: Starting seat
[+0.03s] DEBUG: Starting new display for automatic login as user vivek
[+0.04s] DEBUG: Starting local X display
[+0.04s] DEBUG: X server :0 will replace Plymouth
[+0.07s] DEBUG: Using VT 7
[+0.07s] DEBUG: Activating VT 7
[+0.07s] DEBUG: Logging to /var/log/lightdm/x-0.log
[+0.07s] DEBUG: Writing X server authority to /var/run/lightdm/root/:0
[+0.07s] DEBUG: Launching X Server
[+0.07s] DEBUG: Launching process 1452: /usr/bin/X :0 -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch -background none
[+0.07s] DEBUG: Waiting for ready signal from X server :0
[+0.07s] DEBUG: Acquired bus name org.freedesktop.DisplayManager
[+0.07s] DEBUG: Registering seat with bus path /org/freedesktop/DisplayManager/Seat0
[+4.42s] DEBUG: Got signal 10 from process 1452
[+4.42s] DEBUG: Got signal from X server :0
[+4.42s] DEBUG: Stopping Plymouth, X server is ready
[+4.45s] DEBUG: Connecting to XServer :0
[+4.45s] DEBUG: Automatically logging in user vivek
[+4.45s] DEBUG: Started session 1661 with service 'lightdm-autologin', username 'vivek'
[+5.45s] DEBUG: Session 1661 authentication complete with return value 0: Success
[+5.52s] DEBUG: Autologin user vivek authorized
[+5.53s] DEBUG: Autologin using session xterm
[+6.24s] DEBUG: Dropping privileges to uid 1000
[+6.34s] DEBUG: Restoring privileges
[+6.35s] DEBUG: Dropping privileges to uid 1000
[+6.35s] DEBUG: Writing /home/vivek/.dmrc
[+6.68s] DEBUG: Restoring privileges
[+7.01s] DEBUG: Starting session xterm as user vivek
[+7.01s] DEBUG: Session 1661 running command /usr/sbin/lightdm-session xterm
[+8.04s] DEBUG: New display ready, switching to it
[+8.04s] DEBUG: Activating VT 7
[+8.04s] DEBUG: Registering session with bus path /org/freedesktop/DisplayManager/Session0
[+8.04s] DEBUG: Session 1661 exited with return value 1
[+8.04s] DEBUG: User session quit
[+8.04s] DEBUG: Stopping display
[+8.04s] DEBUG: Sending signal 15 to process 1452
[+8.57s] DEBUG: Process 1452 exited with return value 0
[+8.57s] DEBUG: X server stopped
[+8.57s] DEBUG: Removing X server authority /var/run/lightdm/root/:0
[+8.57s] DEBUG: Releasing VT 7
[+8.57s] DEBUG: Display server stopped
[+8.57s] DEBUG: Display stopped
[+8.57s] DEBUG: Active display stopped, switching to greeter
[+8.57s] DEBUG: Switching to greeter
[+8.57s] DEBUG: Starting new display for greeter
[+8.57s] DEBUG: Starting local X display
[+8.57s] DEBUG: Using VT 7
[+8.57s] DEBUG: Logging to /var/log/lightdm/x-0.log
[+8.57s] DEBUG: Writing X server authority to /var/run/lightdm/root/:0
[+8.57s] DEBUG: Launching X Server
[+8.57s] DEBUG: Launching process 1854: /usr/bin/X :0 -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch
[+8.57s] DEBUG: Waiting for ready signal from X server :0
[+9.58s] DEBUG: Got signal 10 from process 1854
[+9.58s] DEBUG: Got signal from X server :0
[+9.58s] DEBUG: Connecting to XServer :0
[+9.59s] DEBUG: Starting greeter
[+9.59s] DEBUG: Started session 1883 with service 'lightdm', username 'lightdm'
[+11.24s] DEBUG: Session 1883 authentication complete with return value 0: Success
[+11.24s] DEBUG: Greeter authorized
[+11.24s] DEBUG: Logging to /var/log/lightdm/x-0-greeter.log
[+11.38s] DEBUG: Session 1883 running command /usr/lib/lightdm/lightdm-greeter-session /usr/sbin/lightdm-gtk-greeter
[+16.49s] DEBUG: Greeter connected version=1.2.1
[+16.49s] DEBUG: Greeter connected, display is ready
[+16.49s] DEBUG: New display ready, switching to it
[+16.49s] DEBUG: Activating VT 7
[+16.49s] DEBUG: Stopping greeter display being switched from
[+20.86s] DEBUG: Greeter start authentication for vivek
[+20.86s] DEBUG: Started session 2793 with service 'lightdm', username 'vivek'
[+20.95s] DEBUG: Session 2793 got 1 message(s) from PAM
[+20.95s] DEBUG: Prompt greeter with 1 message(s)
[+46.63s] DEBUG: Continue authentication
[+46.67s] DEBUG: Session 2793 authentication complete with return value 0: Success
[+46.67s] DEBUG: Authenticate result for user vivek: Success
[+46.67s] DEBUG: User vivek authorized
[+46.67s] DEBUG: Greeter requests session xterm
[+46.67s] DEBUG: Using session xterm
[+46.67s] DEBUG: Stopping greeter
[+46.67s] DEBUG: Session 1883: Sending SIGTERM
[+46.75s] DEBUG: Greeter closed communication channel
[+46.75s] DEBUG: Session 1883 exited with return value 0
[+46.75s] DEBUG: Greeter quit
[+46.76s] DEBUG: Dropping privileges to uid 1000
[+46.76s] DEBUG: Restoring privileges
[+46.77s] DEBUG: Dropping privileges to uid 1000
[+46.77s] DEBUG: Writing /home/vivek/.dmrc
[+46.84s] DEBUG: Restoring privileges
[+46.89s] DEBUG: Starting session xterm as user vivek
[+46.89s] DEBUG: Session 2793 running command /usr/sbin/lightdm-session xterm
[+46.94s] DEBUG: Registering session with bus path /org/freedesktop/DisplayManager/Session1
[+46.94s] DEBUG: Session 2793 exited with return value 1
[+46.94s] DEBUG: User session quit
[+46.94s] DEBUG: Stopping display
[+46.94s] DEBUG: Sending signal 15 to process 1854
[+47.19s] DEBUG: Process 1854 exited with return value 0
[+47.19s] DEBUG: X server stopped
[+47.19s] DEBUG: Removing X server authority /var/run/lightdm/root/:0
[+47.19s] DEBUG: Releasing VT 7
[+47.19s] DEBUG: Display server stopped
[+47.19s] DEBUG: Display stopped
[+47.19s] DEBUG: Active display stopped, switching to greeter
[+47.19s] DEBUG: Switching to greeter
[+47.19s] DEBUG: Starting new display for greeter
[+47.19s] DEBUG: Starting local X display
[+47.19s] DEBUG: Using VT 7
[+47.19s] DEBUG: Logging to /var/log/lightdm/x-0.log
[+47.19s] DEBUG: Writing X server authority to /var/run/lightdm/root/:0
[+47.19s] DEBUG: Launching X Server
[+47.19s] DEBUG: Launching process 4788: /usr/bin/X :0 -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch
[+47.19s] DEBUG: Waiting for ready signal from X server :0
[+48.34s] DEBUG: Got signal 10 from process 4788
[+48.34s] DEBUG: Got signal from X server :0
[+48.34s] DEBUG: Connecting to XServer :0
[+48.35s] DEBUG: Starting greeter
[+48.35s] DEBUG: Started session 4791 with service 'lightdm', username 'lightdm'
[+48.40s] DEBUG: Session 4791 authentication complete with return value 0: Success
[+48.40s] DEBUG: Greeter authorized
[+48.40s] DEBUG: Logging to /var/log/lightdm/x-0-greeter.log
[+48.40s] DEBUG: Session 4791 running command /usr/lib/lightdm/lightdm-greeter-session /usr/sbin/lightdm-gtk-greeter
[+48.64s] DEBUG: Greeter connected version=1.2.1
[+48.64s] DEBUG: Greeter connected, display is ready
[+48.64s] DEBUG: New display ready, switching to it
[+48.64s] DEBUG: Activating VT 7
[+48.64s] DEBUG: Stopping greeter display being switched from
[+49.32s] DEBUG: Greeter start authentication for vivek
[+49.32s] DEBUG: Started session 4830 with service 'lightdm', username 'vivek'
[+49.34s] DEBUG: Session 4830 got 1 message(s) from PAM
[+49.34s] DEBUG: Prompt greeter with 1 message(s)

```

Contents of /etc/lightdm
```

root@duper:/etc/lightdm# ls -ltr
total 12
-rw-r--r-- 1 root root 166 Dec  1 22:37 mythbuntu-lightdm-gtk-greeter.conf
-rw-r--r-- 1 root root 166 Dec  1 22:38 lightdm-gtk-greeter-ubuntu.conf
lrwxrwxrwx 1 root root  55 Dec  1 22:38 lightdm-gtk-greeter.conf -> /etc/alternatives/lightdm-gtk-greeter-config-derivative
-rw-r--r-- 1 root root 114 Dec  1 22:40 lightdm.conf

```

My .xsession-errors log file is empty, so nothing to paste from there.

I think the log shows that the auto-login worked and then something went wrong.  The log also shows that the authentication when I try to log in works and then something goes wrong.  Its that something that I don't know what it is and how to resolve it.

I have previously tried switching to gdm and that got me logged into a blue screen with a blank xterm on the top left hand side of the screen... but I wanted a desktop as I had previously... looking at screenshots on the net, it looked like I had a xfce desktop, so I tried getting lightdm to work.  Now, when I revert to gdm, it does not work at all.

Any help to troubleshoot this problem will be appreciated.

---

### Post by MrHyde on 2012-12-01
I've made some progress.  I deleted my .Xauthority file and the system now automatically logs in.

It shows a screen with the Mythbuntu text and 5 dots as the background and has an xterm session on the top left corner.  Myth Frontend still is not started and there is no start button or program bar at the top of the screen.

What makes the frontend run automatically on login?  and which desktop or theme brings out the program bar at the top?

---

### Post by MrHyde on 2012-12-01
No more progress, but have learnt a few more things.

The lightdm.conf says to use the session mythbuntu.

In /usr/share/xsessions/ there is a file called mythbuntu.desktop and it contains as below.  Permissions are 644 and owned by root:root
```

[Desktop Entry]
Encoding=UTF-8
Name=Mythbuntu Session
Comment=Use this session to boot into mythbuntu.
Exec=/usr/share/mythbuntu/session.sh
Icon=
Type=Application

```

/usr/share/mythbuntu/session.sh exists and its permissions are 755 and owned by root:root.  Its contents are:

```

#!/bin/sh
#Mythbuntu Install & Settings Session
# Copyright Â© 2007  Mario Limonciello

#Set the background to black
xsetroot -solid black

#source frontend session settings
if [ -f /etc/mythtv/session-settings ]; then
    . /etc/mythtv/session-settings
fi

#Don't process me if in live mode
if [ ! -x /usr/bin/mythbuntu-startup ]; then
    #if nvidia settings are saved and nvidia drivers installed, load them
    if [ -x /usr/bin/nvidia-settings ] && [ -f ~/.nvidia-settings-rc ]; then
        nvidia-settings -l
    fi

    #If we have mtd around (and not running), good idea to start it too
    if ! `pgrep mtd>/dev/null`; then
        if [ -x /usr/bin/mtd ]; then
            /usr/bin/mtd -d
        fi
    fi
    #check if irexec is needed, and start if need be
    if [ -x /usr/bin/irexec ] && [ ! -f ~/.noirexec ] && [ -f ~/.lircrc ]; then
        if [ -n "$(cat ~/.lirc/* | grep --invert-match "#" | grep irexec | grep prog)" ]
        then
            killall irexec
            irexec -d
        fi
    fi
    #x11vnc
    if [ -x /usr/bin/x11vnc ]; then
        [ -f /root/.vnc/passwd ] && PASSWORD="/root/.vnc/passwd"
        [ -f $HOME/.vnc/passwd ] && PASSWORD="$HOME/.vnc/passwd"
        [ ! -z "$PASSWORD" ] && x11vnc -rfbauth $PASSWORD -rfbport 5900 -shared -forever -nowf -norc -notruecolor -bg -xkb
    fi
    #Customized home commands
    if [ -x $HOME/.mythtv/session ]; then
        $HOME/.mythtv/session &
    fi
fi

#Start window manager
export XDG_CONFIG_DIRS=/etc/xdg/xdg-mythbuntu
export XDG_DATA_DIRS=/etc/xdg/xdg-mythbuntu
exec startxfce4

```

So, all of this look good so far.

However, the lightdm logs say:
```


[+1.40s] DEBUG: Started session 2546 with service 'lightdm-autologin', username 'vivek'
[+1.60s] DEBUG: Session 2546 authentication complete with return value 0: Success
[+1.60s] DEBUG: Autologin user vivek authorized
[+1.62s] DEBUG: Autologin using session xterm
[+1.64s] DEBUG: Dropping privileges to uid 1000
[+1.64s] DEBUG: Restoring privileges
[+1.64s] DEBUG: Dropping privileges to uid 1000
[+1.64s] DEBUG: Writing /home/vivek/.dmrc
[+1.95s] DEBUG: Restoring privileges
[+3.03s] DEBUG: Starting session xterm as user vivek
[+3.04s] DEBUG: Session 2546 running command /usr/sbin/lightdm-session xterm

```
which says that it is running session xterm and not session mythbuntu.
Also, my .dmrc file says, 

```

[Desktop]
Session=xterm

```

I've tried changing .dmrc to say mythbuntu, but that does not help as it is written by lightdm on startup.

So, I think the problem is that the mythbuntu session is not being run, but I don't know where to look for why as the configuration all seems to be correct and pointing to the right files.

The sessions folder does contain an xterm.session, which contains ```

[Desktop Entry]
Encoding=UTF-8
Name=Recovery Console
Comment=Failsafe session with only xterm
Exec=xterm
TryExec=xterm
Icon=
Type=Application
X-Ubuntu-Gettext-Domain=gdm

```

That suggests that it should run when starting the recovery console.  But I am not choosing recovery mode at any point, so why would it start that session.  Is that part of the problem - ie somehow I'm booting into recovery mode??

Anyone out there with similar issues and has got a solution to this.

Cheers.

---

