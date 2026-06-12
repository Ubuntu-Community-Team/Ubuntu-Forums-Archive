---
title: "xfce applications bar at top of screen."
date: 2014-05-06
forum: Mythbuntu
---

### Post by khPWXxF on 2014-05-06
You may be interested in my solution to the problem of the irritating desktop bar at the top of the Mythtv frontend screen which I first saw with 14.04.
 
It’s described in these articles:
 
[https://bugs.launchpad.net/mythbuntu/+bug/1282868](https://bugs.launchpad.net/mythbuntu/+bug/1282868)
[http://www.gossamer-threads.com/lists/mythtv/users/567567#567567](http://www.gossamer-threads.com/lists/mythtv/users/567567#567567)
[http://www.mythtv.org/pipermail/mythtv-users/2012-May/333127.html](http://www.mythtv.org/pipermail/mythtv-users/2012-May/333127.html)
 
Others have cleverly suggested a wmctrl command issued:
a) from a startup script.   That won’t work because frontend needs to be running when wmctrl is issued.  It will if you put in a delay but then will fail in a mythwelcome scenario or on restarting mythfrontend after maintenance work.
b)  from a script triggered from a remote button.  Ingenious but low WAF.
 
I thought it more direct to trigger a script from the frontend script.
A new script is put in /usr/bin/fullscreenfrontend.sh (with 755 permissions) and is:
 
```
#!/bin/bash
#get rid of junk at top of screen
#this script called from /usr/bin/mythfrontend
sleep 10
DISPLAY=:0 wmctrl -r "MythTV Frontend" -b add,fullscreen
```
 
It is triggered by a small addition to the wrapper script /usr/bin/mythfrontend just after check_groups
 
```

[…...]
#check that we are in the mythtv group
check_groups

#added prb 6 May 2014.  Send fullscreen command to FE in 10 secs.
/usr/bin/fullscreenfrontend.sh&
#end of addition
 
[...…]
```
 
It’s a terrible cludge for a silly bug but it seems to work though testing has been very limited.  That delay may need tuning – 5 secs is too low on my system, 10 secs works.  Not tried yet with mythwelcome.
 
Incidentally, can anyone explain that DISPLAY=:0 bit?
 
Phil

---

### Post by blm-ubunet on 2014-05-08
DISPLAY is an environment variable that set the target X server/screen. 
Can be exported to the current session.

If using multiple X screens (on 1 server) instead of twinview or xinerama.

To launch FE on 2nd X screen on local X server
DISPLAY=:0.1 mythfrontend

---

### Post by zzztownsend2 on 2014-05-14
deleted

---

### Post by khPWXxF on 2014-07-29
I’m updating this thread because this bug is so persistent and just won’t go away.
 
It did get fixed following an upgrade in 0.27.2, but it then re-appeared.  I think that changing host name on my system to match that of my 0.25 database backup and then restoring may have been the cause.
 
I have just applied latest fixes and it still has that bar across the top of the screen.
 
I do have a work-around (see above) but it is zapped by any upgrades because
/usr/bin/mythfrontend --> /usr/share/mythtv/mythfrontend.sh gets re-written.
 
I’m now trying a different tack of calling a modified version of mythfrontend.sh from mythwelcome.  Hopefully that will survive any upgrades.
 
My system is Mythbuntu 12.04, fixes/0.27 (v0.27.3-110-g5e37f9c) 64 bit on an Asus M3N78EM with Nvidia 8300 onboard to HDMI.
 
Am I alone in still having this fault without the work-around?

Phil

---

### Post by Lester_Burnham on 2014-07-30
Hi Phil,

I only see the menu bar at the top on a TV with no overscan adjustment, where I've used nvidia-settings to adjust the overscan. If I do that, I then need to adjust mythtv appearance with the very hard to use tool with the mythbusters background (hard to read).

If I leave the desktop over scanned, and reset the front end adjustments, it's fine. 

Lester

---

### Post by khPWXxF on 2015-01-12
I’m returning to this thread to give an update in case anyone still has this problem.
 
Readers will see from the above that despite the fixes introduced in 27.1 I had the xfce artefacts across the top of the frontend screen return after I had done a restore from a 0.25 database backup.
 
I fixed it with the kludge documented above but I seemed to be alone in having this problem.  I don’t like unexplained mysteries but I now think I understand what might have been different about my setup.
 
I’ve been re-examining screen resolutions recently (see  [http://ubuntuforums.org/showthread.php?t=2258886](http://ubuntuforums.org/showthread.php?t=2258886))
 
Not only have I forced 1920x1080 with an xrandr command but I have spotted a comment against
Frontend > settings > appearance > GUI > screen settings> GUI width/height
 
These were set to 1920x1080.    These settings were inherited during a database import from a 0.25 backup and the settings were necessary to force full screen displays.
 
Setting both gui pixels to zero eliminates the bug.
 
Now why should that cause the problem?  Is it a new bug?
 
Phil

---

