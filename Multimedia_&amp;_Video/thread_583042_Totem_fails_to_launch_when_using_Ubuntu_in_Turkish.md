---
title: "Totem fails to launch when using Ubuntu in Turkish"
date: 2007-10-20
forum: Multimedia &amp; Video
---

### Post by sedatg on 2007-10-20
Totem fails to launch consistenly when Gutsy's locale is set to Turkish:
```
Gtk-ERROR **: Invalid type: GtkRadioButton
aborting...
Aborted (core dumped)
```

There's a crappy workaround, which is launching Totem with:
```
 env LC_CTYPE="en_US.UTF-8" totem
```

Mplayer has had similar long-standing issues, but I never managed to find a decent solution for it.
Any ideas/suggestions on how to solve this permanently?

---

### Post by Stemp on 2007-10-20
> **sedatg said:**
> Any ideas/suggestions on how to solve this permanently?

I really think you should fill a bug in Launchpad !

---

### Post by sedatg on 2007-10-20
> **Stemp said:**
> I really think you should fill a bug in Launchpad !
[https://bugs.launchpad.net/rhythmbox/+bug/118493](https://bugs.launchpad.net/rhythmbox/+bug/118493) is what happened the first & last time I filed a Launchpad ticket.

---

### Post by Stemp on 2007-10-20
I tried to reproduce this bug, but failed. It's working for me.

Is there a Turkish Loco Team ? Try to contact other people using the Turkish locals to see if they can Confirmed it.

Then look at the backtrace page in the wiki :
[https://wiki.ubuntu.com/Backtrace](https://wiki.ubuntu.com/Backtrace)

The backtrace will help the dev to understand the problem.

---

### Post by Vivaldi Gloria on 2007-10-25
> **sedatg said:**
> Totem fails to launch consistenly when Gutsy's locale is set to Turkish:
```
Gtk-ERROR **: Invalid type: GtkRadioButton
aborting...
Aborted (core dumped)
```

There's a crappy workaround, which is launching Totem with:
```
 env LC_CTYPE="en_US.UTF-8" totem
```


Same problem here. I have a clean Turkish Gutsy install. Totem is not working and thumbnails of the video files are not generated. I don't care much for totem as Ii use vlc but the lack of thumbnails is frustrating.

Is there a workaround to generate the thumbnails?

---

### Post by pacmannia on 2007-10-26
i have the exact same problem. any solutions ?

---

### Post by Vivaldi Gloria on 2007-10-31
I have thumbs back again thanks to that thread:

[http://ubuntuforums.org/showthread.php?t=536209](http://ubuntuforums.org/showthread.php?t=536209)

It tells how to use mplayer as a thumbmail generator.

---

