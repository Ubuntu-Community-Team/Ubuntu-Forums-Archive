---
title: "Trouble With Xine"
date: 2007-11-11
forum: Multimedia &amp; Video
---

### Post by nullfactor on 2007-11-11
Just attempted to open Xine.  No love.  I get the following error message:

```
This is xine (X11 gui) - a free video player v0.99.5cvs.
(c) 2000-2006 The xine Team.
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  141 (XVideo)
  Minor opcode of failed request:  19 ()
  Serial number of failed request:  2129
  Current serial number in output stream:  2130
```

Following the advice of somebody who had this exact issue, I added the following lines to my /etc/X11/xorg.conf file:

```
Section "Device"
        Identifier      "Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller"
        Driver          "i810"
        BusID           "PCI:0:2:0"
        Option "VideoRam" "131072"
        Option "CacheLines" "1980"
        Option "LinearAlloc" "8160"
EndSection
```

Problem still exists and is exactly the same after adding those lines.

Now, the interesting part... I run Beryl.  The Xine problem appears.  If I change to Metacity, the problem goes away.  Seeing that it is a pain in the rear end to change display managers, just to watch a video, there has GOT to be a fix.  I just don't know what that fix is.

If anybody can help me discover this fix, I would eternally appreciate it.

Much thanks,

+null factor

---

### Post by nullfactor on 2007-11-11
Interestingly... with Beryl running, if I double-click a video to play it, it doesn't matter which player I use (Movie Player, VLC, etc), the program opens, then immediately shuts down.  When Metacity, this does not happen.

Anybody have ideas?  Thanks, again.

---

### Post by nullfactor on 2007-11-12
Right... anybody, then?  I'm out of idears.

---

### Post by nullfactor on 2007-11-12
Oh wow... I must have asked a question that is a real stumper.  24 hours later and no one has any ideas???  That's atypical.

I've searched the internet up and down and have not found anything that helps, so if anybody here has ANYTHING I could try... anything at all?

:confused::confused::confused::confused::confused::confused::confused::confused:

---

### Post by nullfactor on 2007-11-14
Problem solved.  Upgraded to Gutsy, got rid of Beryl.  There you have it.  Yee haw.

---

### Post by WHiZZi on 2007-11-28
and for those who have the same problem on Gutsy (with Compiz-fusion running)

Set the following line in your ~/.xine/config
> 
video.driver:opengl


This did the trick here.

---

