---
title: "Bluetooth Headset as Speaker"
date: 2007-12-21
forum: Multimedia &amp; Video
---

### Post by mjpolifka on 2007-12-21
After a few hours, I have become way too frustrated with this (normally I last much longer).  Alsa REFUSES to write to my bluetooth headset.  I got it to work once when I had just installed the gnome-vfs-obexftp package.  I used mplayer -ao alsa:device=bluetooth and it worked perfectly.  But then I hit ctrl-c to stop it and it never worked again.  When I try that command now I get:
```

[AO_ALSA] alsa-lib: pcm_bluetooth.c:1179:(bluetooth_cfg) Error 22 while configuring device
[AO_ALSA] Playback open error: Invalid argument
Could not open/initialize audio device -> no sound.
Audio: no sound
Video: no video

Exiting... (End of file)

```
In order to get that far, I created a .asoundrc:
```

pcm.bluetooth {
        type bluetooth
        device "00:19:7F:53:34:D6"
}

```
I'm thinking there is some problem with the gnome-vfs-obexftp package, as it didn't work until I installed that, and stopped working after I abruptly stopped mplayer (maybe it's still in use?).  I'll try restarting and see if it works again.

Does anyone know how to get this to work?  It works so well in XP (with the blue soleil software), I was very disappointed when I moved it over to my laptop.  Maybe I could try running bluesoleil in wine?  Probably not.

Thanks for your help.

---

### Post by mjpolifka on 2007-12-21
Yep, works again after restart.
Also, I can only play once, even if I let the whole song play and mplayer exits normally.  wtf.

EDIT:  If I remove and reinsert the bluetooth dongle it works again.  Another big wtf.  Some package in here is very messed up.

---

### Post by mjpolifka on 2007-12-31
Bump?  Does no one know anything about bluetooth?

---

### Post by zonky on 2007-12-31
I'm also having problems with bluetooth where my headphones stop working after around 2.5 minutes.

You may find blueman [http://blueman.tuxfamily.org](http://blueman.tuxfamily.org) a much easier way of managing bluetooth in ubuntu.

---

### Post by zonky on 2007-12-31
```
pcm.!default {
        type bluetooth
        device "00:19:7F:53:34:D6"
}
```

You can also set your asoundrc to be all audio output using the code above.

---

