---
title: "VLC location"
date: 2008-05-28
forum: Multimedia Software
---

### Post by skunkbad on 2008-05-28
I've installed VLC, and want Firefox to use it as the default player of video files, but when I go into prefs to set VLC as the defauly player, I have to browse my computer to find VLC, and can't locate it. Anyone know the VLC location I am trying to find?

I'm assuming that VLC is supposed to play all movie files, so I'd like to change the default player to VLC.

---

### Post by meatlegs on 2008-05-28
Try this:
[https://addons.mozilla.org/en-US/firefox/addon/446](https://addons.mozilla.org/en-US/firefox/addon/446)

worked for me!

---

### Post by Bubba64 on 2008-05-28
> **skunkbad said:**
> I've installed VLC, and want Firefox to use it as the default player of video files, but when I go into prefs to set VLC as the defauly player, I have to browse my computer to find VLC, and can't locate it. Anyone know the VLC location I am trying to find?

I'm assuming that VLC is supposed to play all movie files, so I'd like to change the default player to VLC.

Vlc can be found in applications sound and video, if you want it to play any on board files right click on media then other then pick vlc from window, this will start opening similiar packages with vlc.

---

### Post by chochem on 2008-05-28
To answer the question of the original poster: VLC is in /usr/bin (as is most of the application that you yourself install). The vlc-mozilla plugin is fine but sometimes it's preferable having files open in a stand alone player.

---

### Post by phmadore on 2008-10-28
Thanks for that!

---

### Post by cariboo on 2008-10-28
THe next time you run into a problem like this, try:

```
which programname
```

This will work woth any program you can think of and will show the path.

```
 which vlc
/usr/bin/vlc
```

Jim

---

