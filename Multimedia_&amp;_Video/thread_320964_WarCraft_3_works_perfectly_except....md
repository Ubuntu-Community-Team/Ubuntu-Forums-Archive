---
title: "WarCraft 3 works perfectly except..."
date: 2006-12-18
forum: Multimedia &amp; Video
---

### Post by hk_2999 on 2006-12-18
[I]I tried running WarCraft III on the latest stable 0.9.26, and im quite [impressed](http://hk2999.livejournal.com/6612.html). I play a lot of B.net games so I really need the performance and the multitasking ability linux gives me. However, there is one problem. Whenever I clicked the right mouse button, it sometimes randomly opens a context menu with the On Top, Close,  etc. options. Is there any way to disable this um... 'feature'?

By the way, I tried running in KDE, but there are problems on the controls, sometimes they become unresponsive there, especially alt + click to put signal flares, it doesn't work. I use alt+g instead. Any help would be gladly appreciated, thank you.[/I]

FIX:
Metacity default hotkey for move a window except grabbing the top of it is alt + mouse1.
alt + mouse2 opens that context menu.

Just change that move window hotkey to another key like super (windows logo) and you'll be fine.

You can do that in System>Preferences>Windows then choose Super as the movement key.

---

### Post by pay on 2006-12-18
Try```
wine war3.exe -opengl -fullscreen -width 1024 -height 768
```

---

### Post by Elena678 on 2006-12-18
could you just install it with wine, i even can't install team hospital with wine :S how have you done?

kram
Elena

---

### Post by basse1989 on 2006-12-22
It because you're pressing alt at the same time.
Metacity default hotkey for move a window except grabbing the top of it is alt + mouse1.
alt + mouse2 opens that context menu you are talking about.
Just change that move window hotkey to another key like super (windows logo) and you'll be fine.
:D

you do that in System>Preferences>Keyboard Shortcuts

---

### Post by hk_2999 on 2006-12-22
> **basse1989 said:**
> It because you're pressing alt at the same time.
Metacity default hotkey for move a window except grabbing the top of it is alt + mouse1.
alt + mouse2 opens that context menu you are talking about.
Just change that move window hotkey to another key like super (windows logo) and you'll be fine.
:D

you do that in System>Preferences>Keyboard Shortcuts

Thank you!

That was very helpful, i didnt even know the shortcut alt+mouse2 exists. Now I can play WarCraft III without any problems anymore. 

One mistake though, to change the mapping of the move window hotkey, you go to System->Preferences->Windows and then choose Super as the movement key.

---

