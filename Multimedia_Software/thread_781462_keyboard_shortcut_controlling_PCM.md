---
title: "keyboard shortcut controlling PCM"
date: 2008-05-04
forum: Multimedia Software
---

### Post by hypertonic on 2008-05-04
Hi,
I am reeeeeeaaaaaaaaaaaally getting annoyed by searching for a solution to make the special function keys on my Dell Latitude D510 keyboard to control PCM instead of Master (or headphones, whilst searching I did make thàt switch). I tried every single solution posted on this forum and suggested by google.
I tried keytouch, I tried "System -> Preferences -> Sound...". Nothing, really nothing works. I'm even getting annoyed by trying to the extend that I no longer care how much double-posting-crimes I'm committing by posting this thread.
So pleeeeaaaaase, help me!

regards,
hype

Dell Latitude D510 Laptop
Ubuntu 8.04 Hardy Heron
[Hardware Overview]("http://www.hardware.info/en-UK/productdb/bGNkZJiXmJfK/viewproduct/Dell_Latitude_D510/index.php")

---

### Post by jettjunker on 2008-05-09
I'm in the same boat.  Setting sound properties to control PCM and Master works in that scrolling my mouse up/down while hovering over the panel icon works, but the keyboard shortcuts only control master.  I recall having this problem before, and I found a thread that actually gave two or three things to do to make the change global... but I can't find it :/

Anyway, as a temporary work around I'm using keytouch.  You mentioned you tried something with it, but if you have the same problem as me then you didn't try this...  Rather than using the default setting, I selected "Program:" which just seems to run terminal commands.  Thus, I set:

Volume Up:
```
amixer -c 0 set PCM 8+ & amixer -c 0 set Master 1+
```

Volume Down:
```
amixer -c 0 set PCM 8- & amixer -c 0 set Master 1-
```


-c 0 picks out card0 -- if you only have one that should be it.  I have PCM going by increments of 8 while the Master by 1 because the max of PCM is 255 and the max of Master is 31.  Master outruns PCM by a little, but not too bad.  I don't know if these numbers are standard though, so if yours are way off run the command in the terminal and it will display "Limits: 0-#", then just do some math to figure out what increments you want.

[of course, if you want your keyboard to only control PCM you can just omit the " & amixer -c 0 set Master 1+/-"]


EDIT: In my case the problem turned out to /be/ keytouch.  I installed keytouch for other reasons, and it turns out it borks the gnome setting for volume.  In the preferences section, under user settings, you can select a "Mixer Channel" which trumps whatever you set in gnome... problem is (for me anyway) that you can only select one... I'd really prefer to be able to have it control both PCM and master...

---

