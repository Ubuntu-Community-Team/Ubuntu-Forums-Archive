---
title: "Changing IVTV boot settings"
date: 2006-10-14
forum: Multimedia &amp; Video
---

### Post by ebs16 on 2006-10-14
Hi,

I have IVTV up and running with a Hauppauge PVR-150.  I would like IVTV to enter widescreen mode by defualt.  Right now, IVTV loads with a standard 4:3 aspect ratio every time I turn on the computer.  I have to run the command **ivtvctl -c aspect=3** before I view video to have IVTV switch to the 16:9 widescreen aspect ratio.  Is there a way to configure IVTV to load at 16:9 automatically on boot? I'm relatively new to linux and can't seem to locate any configuration files for IVTV :confused: (I installed it using a tutorial).  Any help would be greatly appreciated.

Thanks!

---

### Post by wjston on 2006-11-28
log in as a mythtv user then, in a terminal (not root), copy the following command and press enter:
 $ echo 'ivtvctl -c aspect=3' >> ~/.profile
this should set your card to widescreen each and every time mythtv logs in to a session.

Hope this helps

---

### Post by ebs16 on 2006-12-04
Well, I'm not using myth tv.  i have a server set up to stream live TV from my server to my laptop using VLC and a very basic php web interface.  Is there a way to modify a driver file to set widescreen as the default?

Thanks for your help.

---

### Post by superm1 on 2006-12-15
> **ebs16 said:**
> Well, I'm not using myth tv.  i have a server set up to stream live TV from my server to my laptop using VLC and a very basic php web interface.  Is there a way to modify a driver file to set widescreen as the default?

Thanks for your help.
The easiest way to set this up is to add that command to

```
/etc/rc.local
```

This file is ran at bootup every time before you even login to X.

---

