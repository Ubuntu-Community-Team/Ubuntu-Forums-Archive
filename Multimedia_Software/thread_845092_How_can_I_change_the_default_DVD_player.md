---
title: "How can I change the default DVD player?"
date: 2008-06-30
forum: Multimedia Software
---

### Post by anton on 2008-06-30
I want to specify VLC as the default DVD player, but haven't had any success following the instructions in [this thread]("http://ubuntuforums.org/showthread.php?t=333714").

I've used gconf-editor to set the autoplay dvd command to vlc, and I've also entered the following command from the terminal:

```
gconftool-2 --type string --set /desktop/gnome/volume_manager/autoplay_dvd_command "vlc dvd://"
```

. . . but I'm still stuck with Totem opening every time I insert a DVD.

Would really appreciate some help!

---

