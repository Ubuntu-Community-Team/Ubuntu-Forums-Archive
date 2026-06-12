---
title: "Sound lost after updates"
date: 2014-09-05
forum: Multimedia Software
---

### Post by synapse46 on 2014-09-05
I'm fairly certain one of the updates is breaking sound in my Xubuntu install.  It also seems to prevent X from loading at start up.  This is a fairly new install, I've reinstalled and after I believe the 2nd round of updates the issues repeat.  Any ideas what is going on here? 

[https://www.dropbox.com/s/07inzc5m0hxbjy3/Screenshot%20-%2009052014%20-%2010%3A01%3A03%20PM.png?dl=0](https://www.dropbox.com/s/07inzc5m0hxbjy3/Screenshot%20-%2009052014%20-%2010%3A01%3A03%20PM.png?dl=0)

Also new since the updates, systemd prompting for authentication on restart.


Thanks
Jason

---

### Post by synapse46 on 2014-09-05
Further update, just noticed under PulseAudio volume it shows Dummy Output.

---

### Post by Yellow Pasque on 2014-09-06
[https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by synapse46 on 2014-09-07
So in trying to correct the issue I damanged something and had to reload it.  Like clockwork I had a series of errors on bootup after updates were installed.  I should have taken a screenshot of the errors the system wanted to phone home, I can't find the errors mentioned in any logs.  I did find the errors mentioned below, after 4-5 reboots the errors cleared up and I haven't lost the sound drivers. 

8:14:29 xubuntu1 pulseaudio[2426]: [pulseaudio] server-lookup.c: Unable to contact D-Bus: org.freedesktop.DBus.Error.NotSupported: Unable to autolaunch a dbus-daemon without a $DISPLAY for X11
Sep  7 08:14:29 xubuntu1 pulseaudio[2426]: [pulseaudio] main.c: Unable to contact D-Bus: org.freedesktop.DBus.Error.NotSupported: Unable to autolaunch a dbus-daemon without a $DISPLAY for X11

---

### Post by Yellow Pasque on 2014-09-07
You may have removed the pulseaudio-module-x11 package. Make sure it is installed:
```
sudo apt-get install pulseaudio-module-x11
```

---

### Post by synapse46 on 2014-09-08
Looks like I got this fixed.  I found the .crash file and found some xorg errors and some google searching found something mentioning wrong kernel and so I ran the following and looks like all is good now.  I very much enjoy Xubuntu, it runs great out of the box, it is frustrating that the first round of updates caused all these issues.  Glad it looks like it is sorted, it is a great desktop os/environment.
Commandline: apt-get autoremove
Remove: linux-headers-generic:amd64 (3.13.0.35.42), linux-image-generic:amd64 (3.13.0.35.42)

---

