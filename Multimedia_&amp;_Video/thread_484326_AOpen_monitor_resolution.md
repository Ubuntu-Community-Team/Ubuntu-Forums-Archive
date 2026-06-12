---
title: "AOpen monitor resolution"
date: 2007-06-25
forum: Multimedia &amp; Video
---

### Post by sparX CG on 2007-06-25
Hi everyone.  I'm having problmes with my friend's computer.  I just installed Ubuntu on it, it's working great except for one thing.  The screen resolution does not go higher than 1024x768 at 50Hz.  He knows for sure that his monitor can go up to 1280x1024 at 70Hz, from his experience in Windows.  He got rid of Windows now, but the screen resolution is really bugging us.

I installed the correct nVidia driver for his 6600, glxinfo reports that direct rendering is working correctly.  I tried adding entries to the xorg.conf file but it's as if it keeps ignoring them and goes back to the usual 1024x768.

His monitor is an AOpen F2705 17 inch LCD, bought in some Chinese store.  I'm suspecting that would be the cause of this but I don't know how to fix it.

Any ideas for causes to this and fixes?  Thanks in advance!

---

### Post by rklauco on 2007-06-25
It's not a problem of the monitor.
Reconfigure the X - go to text console using ALT+F1, log in, execute following commands:
```

sudo /etc/init.d/gdm stop
sudo dpkg-reconfigure xserver-xorg

```
This will force the graphic card and monitor detection. You will have to answer few questions (the default answers usualy works fine).
Anyhow, for LCD display I recommend using 60Hz - the dimm of liquid crystal has nothing to do with the electrone emited light with CRT monitor, so you do not have to run for high refresh rates in order to save your eyes.
Check nice description at
[http://www.tftcentral.co.uk/speccontent.htm](http://www.tftcentral.co.uk/speccontent.htm)
and especialy the part on Refresh Rate.

---

### Post by sparX CG on 2007-06-25
I've tried it already, it didn't work.  I even took out 1024x768 explicitly.  It's really odd, it's like it ignores the resolutions from xorg.conf.

---

### Post by rklauco on 2007-06-26
Seems to me that the part of display definition in xorg file is frong - the frequency settings.
Could you post the xorg.conf here?

---

