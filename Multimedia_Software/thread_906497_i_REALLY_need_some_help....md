---
title: "i REALLY need some help..."
date: 2008-08-31
forum: Multimedia Software
---

### Post by Prominence on 2008-08-31
Ok...I'm not sure when this started but I know it wasn't long ago, and nothing will play, my Videos and my Music will not play unless done with VLC Media player, but I want to play my music and videos with Songbird and the others. I have the Gstreamer plug ins and everything.

---

### Post by wolfen69 on 2008-08-31
some people have fixed their sound issues by uninstalling pulseaudio and just use alsa.

---

### Post by Prominence on 2008-08-31
And how do i do that?

---

### Post by Prefix100 on 2008-08-31
If it's a problem thats recently surfaced, then I doubt its pulseaudio.

Also, every time I try to get rid of pulse audio it destroys my gnome install.

However if you want to disable it safely to see if it is causing your problems you can use this command.

```
killall pulseaudio
```

---

### Post by Prominence on 2008-08-31
It worked! Thank you so much!

---

### Post by Prominence on 2008-08-31
now...how do I permently fix it?

---

### Post by Prefix100 on 2008-09-01
Goto System > Preferences > Sessions, then add the command there.

---

### Post by Prominence on 2008-09-01
Thanks!

---

