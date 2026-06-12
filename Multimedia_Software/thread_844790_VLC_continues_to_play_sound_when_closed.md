---
title: "VLC continues to play sound when closed"
date: 2008-06-29
forum: Multimedia Software
---

### Post by richtable on 2008-06-29
anyone else noticed this - in VLC if you play a movie by opening a folder containing the vob files.... when you close or exit from VLC the sound keeps going and you cant shut it off since there are 'apparantly' no applications open.  Kind of irritating you have to reboot to shut it up.

---

### Post by mc4man on 2008-06-30
That occurs (at least here) when you don't stop playback before exiting,closing.

---

### Post by adrianmck on 2008-07-07
I have the same problem. Even though I closed VLC it is still running and you can see it with ps -e. This only happens when using Open Directory to playback a DVD  ripped to my hard drive. Any ideas why VLC isn't closing?

---

### Post by mc4man on 2008-07-08
Are you _stopping_ playback before closing vlc?, you know the little square button.

---

### Post by silviutp on 2008-07-10
> **richtable said:**
> anyone else noticed this - in VLC if you play a movie by opening a folder containing the vob files.... when you close or exit from VLC the sound keeps going and you cant shut it off since there are 'apparantly' no applications open.  Kind of irritating you have to reboot to shut it up.

You don't have to reboot, you can kill the vlc process.
```
sudo killall vlc
```


Anyway, I have the same problem, looks like after you stop the playback it exits normally.

---

### Post by Prefix100 on 2008-07-10
This used to happen to me when using pulseaudio.

---

