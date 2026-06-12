---
title: "New Nano Amarok Config Mostly Solved"
date: 2008-12-09
forum: Multimedia Software
---

### Post by ubonetu on 2008-12-09
Hi,

Just thought I'd contribute this, keep in mind I'm on Kubuntu so this may not apply to Gnome.

I had a lot of problems getting files over and mounting and dismounting my new iPod Nano 1285 but this seemed to help:

First, open the iPod with the "Devices recently plugged in" applet and find out what the name is of the directory it creates for your (it's got to be Window's formatted) iPod in /media/

It's whatever name your user was in the Windows distribution you used or could be just "iPod".

Then add this by:

```
sudo kate /etc/fstab 
```

Add the line:

```
/dev/sd*1  /media/[ipod name here]  vfat  rw,user,check=relaxed  0 0
```

(You can find out what dev node your ipod mounts on within Amarok (it should automatically detect it and display it in the preferences under "Devices".  Use the for the /dev/sd[whatever] part in the fstab.)

to the bottom of /etc/fstab

Now, leave that open and plug select Apple Ipod from the Plugin drop-down menu and add these lines in the after clicking on the mechanical button right next to it:

```
mount %d %m
```

```
kdesudo eject %d
``` (I don't know why but you still need root privledges to eject the pod even after the "user" entry in /etc/fstab therefore: kdesudo may ask you for your password [sometimes it won't]).

Anyway, this should get you up and running.  It's a little buggy so input welcome.  Luckily, it does seem to work.

ubonetu

p.s.  If you don't see your iPod or have trouble, open it with the Devices recently plugged in applet.  And if that doesn't work, you may need to go back to the PC and allow disk access under iTunes prefs.

Also, aesthetic drawback, Amarok doesn't make the little mini icons for the bottom of the screen.  It does work in Coverflow, though.

---

