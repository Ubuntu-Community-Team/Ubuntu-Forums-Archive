---
title: "How to Fix Really Loud Drumroll"
date: 2011-11-24
forum: Multimedia Software
---

### Post by ttoolin on 2011-11-24
I am using Ubuntu 10.04LTS on an old P3 box with a basic soundcard.  When I installed some PulseAudio utilities and some other applications, like Audacity and VLC, the drumroll that occurs at the login screen got really, really loud, and I ran into difficulty trying to find a solution for it.  I searched through the forums, and found two posts, from which I was able to combine information from, and I came up with a solution that worked for me.

To fix this, I opened up the following file using 'sudo gedit':

```
sudo gedit /usr/share/gdm/autostart/LoginWindow/libcanberra-ready-sound.desktop
```

and changed this line:

```
Exec=/usr/bin/canberra-gtk-play --id="system-ready" --description="GNOME System Ready"
```

to this (this must have the decimal point and zero):

```
Exec=/usr/bin/canberra-gtk-play --id="system-ready" --description="GNOME System Ready" --volume="-25.0"
```

I understand that the value is adjustable to your needs, but the example I found of -25.0 worked very well for me.

I hope others find this information useful.

I was able to draw upon the knowledge of towheedm and jmatcam in these posts:

[http://ubuntuforums.org/showthread.php?t=1718680](http://ubuntuforums.org/showthread.php?t=1718680)
[http://ubuntuforums.org/showthread.php?t=1346211](http://ubuntuforums.org/showthread.php?t=1346211)

terry

---

