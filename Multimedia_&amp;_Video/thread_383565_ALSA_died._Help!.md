---
title: "ALSA died. Help!"
date: 2007-03-13
forum: Multimedia &amp; Video
---

### Post by hotspoons on 2007-03-13
In an attempt to change which channel the sound comes out of on my soundcard (through using modified asound.state files and running 'alsactl restore'), I somehow borked ALSA. Currently, no sound comes out of my PC, and I had to blacklist the kernel module for my soundcard so ALSA doesn't load as it causes login problems as it is currently configured. Where are the configuration files for ALSA located so I can try to fix this? I removed my asound.state file as a start. Any help would be much appreciated. Thank you,

-Rich

---

### Post by Ambimom on 2007-03-13
[http://www.ubuntuforums.org/showthread.php?t=205449](http://www.ubuntuforums.org/showthread.php?t=205449)

Will show you how to reinstall.  Good luck.

---

### Post by hotspoons on 2007-03-13
Alright, I got it working. The instructions provided did reinstall ALSA, but as soon as you log into Gnome, the old asound.state is restored, so the problem persisted every time I logged out and back in. This is what I did to fix it.

shutdown alsa:
```
sudo /etc/init.d/alsa-utils stop
```

remove the asound.state file:
```
sudo rm /var/lib/alsa/asound.state
```

remove the following files/directories:

~/.gconfd/saved_state
~/.gconf/apps/gnome-volume-control
~/.gconf/desktop/gnome/sound

Then power off the computer. Don't shut it down, yank the plug. That way none of these files will be written upon logging out. When I booted back in, Alsa was like new and sound worked again. Thank you for the link.

-Rich

---

