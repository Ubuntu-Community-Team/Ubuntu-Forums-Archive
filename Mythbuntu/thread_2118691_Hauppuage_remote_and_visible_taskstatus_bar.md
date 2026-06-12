---
title: "Hauppuage remote and visible task/status bar"
date: 2013-02-21
forum: Mythbuntu
---

### Post by homeeey on 2013-02-21
I'm running the latest Mythbuntu on 12.04 and things are working pretty good.  I even have my grey remote working, thanks to these posts.

[http://ubuntuforums.org/showpost.php?p=11657822&postcount=16]("http://ubuntuforums.org/showpost.php?p=11657822&postcount=16")

and

[http://http://ubuntuforums.org/showthread.php?t=2113865]("http://http://ubuntuforums.org/showthread.php?t=2113865")

I ran into the problem of my event# changing after reboot and tried editing the hardware.conf file to determine the event, but do to my lack of linux skills was unable to do it.  But found that every time I restarted lirc it would correct the problem so I added the restart command to the /etc/rc.local file and it seems to work, anyone see a problem with this?

```
modprobe ir-kbd-i2c
**sudo service lirc restart**
exit 0
```


So it appears the last of my problems appears to be the upper status/task bar appearing on top of the frontend.  I can set it to autohide, but still there is a small line on top of the picture and it is bugging me.  I tried the compiz suggestion

"Install + run CompizConfig Settings Manager (ccsm)
Click on Workarounds (found in the Utility category) then tick the "Legacy
Fullscreen Support" option."

but that didn't work.  Anyone have a fix?

Thanks

---

### Post by PhilWig on 2013-02-22
Have you seen the discussion which now includes toolbars over at:

[http://ubuntuforums.org/showthread.php?t=2117053](http://ubuntuforums.org/showthread.php?t=2117053)

Come and join us!

Where is that autohide option?

Phil

---

