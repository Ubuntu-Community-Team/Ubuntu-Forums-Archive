---
title: "vmplayer guest (Win7Pro) stomps on host sound 10.10"
date: 2011-06-21
forum: Multimedia Software
---

### Post by skaramanger on 2011-06-21
Greetings,

Recently, my sound has started acting up.  If starting from a fresh boot, (sound apparently working) I start vmplayer and start my win 7 pro 64 bit guest. Alls "good" it starts plays the windows sound.  So sound works.  I didn't test audio in windows, I dont' have it configured. Now my problem begins when I put windows 7 guest to sleep or shutdown and exit vmplayer.

I no longer have system sounds and audio.  I have fiddled around with this and managed to get it working.  I think a reboot did eventually bring it back, but that is not a fix.  Has anybody else experienced something like this?

```

desktop:~$ cat alsa_installed.out 
i   alsa-base                       - ALSA driver configuration files           
i   alsa-tools                      - Console based ALSA utilities for specific 
i   alsa-tools-gui                  - GUI based ALSA utilities for specific hard
i   alsa-utils                      - Utilities for configuring and using ALSA  
i   bluez-alsa                      - Bluetooth audio support                   
i   gnome-alsamixer                 - ALSA sound mixer for GNOME                
i   gstreamer0.10-alsa              - GStreamer plugin for ALSA                 
i   libclalsadrv-dev                - ALSA driver C++ access library (developmen
i A libclalsadrv2                   - ALSA driver C++ access library            


```

Version: alsa-base is: 1.0.23+dfsg-1ubuntu4
Vmplayer: version 3.1.4 build-385536
Kernel:  ```
2.6.35-28-generic
```

I have tried pheneggling alsamixer (unmuting) and maxing out the volume.  I have tried killing the pulseaudio daemon and restarting it. Stopping alsa and restarting it.  Then I just rebooted. temporary fix.
Any suggestions?

Tia


Bump please?

---

