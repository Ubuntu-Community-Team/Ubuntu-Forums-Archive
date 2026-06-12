---
title: "Flash, PulseAudio, Media Keys"
date: 2013-03-17
forum: Multimedia Software
---

### Post by zeug on 2013-03-17
At times the Flash plugin in my webs browser starts to make videos stutter.  Upon google-ing, I found that running
```
rm -r ~/.pulse* ; killall pulseaudio
```
makes the Flash playback as per normal.  However, after running these commands, the media keys no longer actually control the system volume, but they do make notifications (i.e. with Notify OSD) as if they do.

Is there a way to:
[LIST]
[*]get the media keys to start working again, without rebooting? 
[*]fix this "stuttering-Flash videos" problem without killing pulseaudio like that? 
[*]a way to see what command is being run when hitting the media keys (or any keyboard shortcut really)? (This would be helpful to know in order to establish user-defined shortcuts to the system volume control *with* the pop-up notifications.) 
[*]find out what the command to run is to change the system volume *including* the notification with Notify OSD? 
[/LIST]

---

### Post by tgalati4 on 2013-03-18
Try simply:

```
pulseaudio -k
```  and see if that works without messing up the media keys.

From:  [http://www.hecticgeek.com/2012/01/how-to-restart-pulseaudio-sound-server-ubuntu-linux/](http://www.hecticgeek.com/2012/01/how-to-restart-pulseaudio-sound-server-ubuntu-linux/)

---

### Post by zeug on 2013-03-18
Since it does not work after using killall, as mentioned, I am guessing that might work after a reboot.  Thanks!

Anyone else got an idea about the other things, or this?

---

### Post by zeug on 2013-03-29
Bump?

---

