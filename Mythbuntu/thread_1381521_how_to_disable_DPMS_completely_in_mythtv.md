---
title: "how to disable DPMS completely in mythtv?"
date: 2010-01-14
forum: Mythbuntu
---

### Post by dannysauer on 2010-01-14
So, I want my screen to stop going blank after a few minutes of inactivity.  I know where the power button is on my TV which doesn't support DPMS, and I will push that when I want the screen to be blank. :)

I've searched around, and found nothing that works.  I'm running a fully up-to-date (as of the time of this post) Karmic system, but not running the auto builds [yet].  Here's my *whole* xorg config:

```
sauer@stinky:~$ cat /etc/X11/xorg.conf 

Section "Screen"
	Identifier	"Default Screen"
	DefaultDepth	24
EndSection

Section "Device"
	Identifier	"Default Device"
	Driver	"nvidia"
	Option	"TVOutFormat"	"SVIDEO"
	Option	"NoLogo"	"1"
	Option	"UseEvents"	"1"
	Option	"ConnectedMonitor"	"TV"
	Option	"DPI"	"100x100"
	Option	"TVStandard"	"NTSC-M"
        Option  "DPMS" "false"
EndSection
```

And here's the code which starts the session - note that there is no window manager, I just run mythfrontend (on another machine the windowmanager stuff is uncommented, but it has the same problem):

```
sauer@stinky:~$ sed '/^#/d' /usr/share/xsessions/mythtv.desktop 
[Desktop Entry]
Encoding=UTF-8
Name=MythTV Session
Comment=Use this session to start up the MythTV front end
Exec=/usr/share/xsessions/mythtv.wrapper
Icon=
Type=Application

sauer@stinky:~$ cat /usr/share/xsessions/mythtv.wrapper 
cat: /^#/d: No such file or directory
#!/bin/bash --norc
#/usr/bin/metacity --sm-disable &
#wmpid=$!
/usr/bin/mythfrontend -nw
#/bin/kill $wmpid || /bin/kill -9 $wmpid # clean up after myth terminates...
```

The myth process isn't spawning any screensavers - this is all that it's currently running:

```
sauer@stinky:~$ ps -ef | grep ^myth
mythtv    2135  2121  0 20:56 ?        00:00:00 /bin/bash --norc /usr/share/xsessions/mythtv.wrapper
mythtv    2165  2135  0 20:56 ?        00:00:00 /usr/bin/ssh-agent /usr/bin/dbus-launch --exit-with-session /usr/share/xsessions/mythtv.wrapper
mythtv    2168     1  0 20:56 ?        00:00:00 /usr/bin/dbus-launch --exit-with-session /usr/share/xsessions/mythtv.wrapper
mythtv    2169     1  0 20:56 ?        00:00:00 /bin/dbus-daemon --fork --print-pid 7 --print-address 9 --session
mythtv    2170  2135 15 20:56 ?        00:00:16 /usr/bin/mythfrontend.real -nw
```


I'm pretty confident that it's actually mythtv, given these two lines in the .xsession-errors:

```
2010-01-14 20:38:03.930 ScreenSaverX11Private: Gnome screen saver support enabled
2010-01-14 20:38:03.932 DPMS is active.
```

So, DPMS is supposedly shut off in xorg.conf.  But then when mythtv starts up, it's enabling the screensaver and turning dpms on?  I thought that mythtv was supposed to respect the dpms settings as of a while ago, but maybe that's a new change which hasn't made it into the current build?  Does anyone have further thoughts?  Perhaps I should send mythfrontend to the background and then run "xset -dpms" in a tight loop until the myth process exits? :P

---

### Post by azmyth on 2010-01-14
I use a script that is called with irexec by using the power button. I turn the tv on with a RS232 connection echo command and then issue the following command.

xset -dpms
xset s reset

I couldn't get this to work on boot so I when I reboot I turn the TV on and off quickly luckily I don't reboot often.

---

### Post by ZedThou on 2010-01-15
I fixed a similar problem with

```

$ cat ~/.xprofile 
xset -dpms
xset s off

```

---

### Post by dannysauer on 2010-01-15
Nevermind - I'm a bone head.  I originally had "option dpms false" in xorg.conf with FALSE in all-caps (copied from Some Random Internet Source(TM)).  Before I posted this, I changed false to lowercase, but didn't reload the x server.  I didn't think it was case-sensitive on those.  Apparently it is, because the screen no longer blanks with the configuration as-posted after I restarted X. :)

So, to recap, it works to put
```
Option  "DPMS" "false"
```
in the Device section of xorg.conf when running myth without a windowmanager, using the no-windowmanager mythtv session I posted earlier.  A window manager may have its own screensaver which needs disabled separately.

---

### Post by dannysauer on 2010-01-15
and...

Installed the daily build packages after posting that.  15 minutes later, the screen's black.  But then it wakes back up "a while" later (I didn't time it), and seems to stay awake.  This is weird.

I don't know if it did that last night, as I just restarted gdm and went to bed.  Since the TV was still on when I came up this morning, I assumed it had stayed on all night.  It may have done the same thing: shutting off and then turning back on once.

---

### Post by josephmc on 2010-04-15
> **dannysauer said:**
> and...

Installed the daily build packages after posting that.  15 minutes later, the screen's black.  But then it wakes back up "a while" later (I didn't time it), and seems to stay awake.  This is weird.

I don't know if it did that last night, as I just restarted gdm and went to bed.  Since the TV was still on when I came up this morning, I assumed it had stayed on all night.  It may have done the same thing: shutting off and then turning back on once.

I have the same problem! Sometimes it's seconds apart. It just goes blank. I have tried every way of disabling DPMs and blanking possible but it still does it. It's just an old CRT HDTV hooked up through HDMI. Boxee does just fine and when I rewind after it goes blank it plays fine so it's not the file. Please please does anybody have any ideas?

---

