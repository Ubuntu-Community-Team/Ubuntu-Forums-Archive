---
title: "libdvdread: can't seek to block"
date: 2009-09-22
forum: Multimedia Software
---

### Post by nebcanuck on 2009-09-22
I'm having trouble getting DVDs to play under Ubuntu Karmic right now. I don't think that it's specifically related to the development branch, though, since the issue seems to be common enough.

The error message I'm getting is that libdvdread is unable to seek block x, where x varies based on which DVD I'm playing. It's consistent across DVDs, and occurs when I either play a DVD to a certain point, or try to scene select past that point.

I found [a post on the Fedora Forums]("http://forums.fedoraforum.org/showthread.php?t=153413") which said the issue may be having the DVD play automatically when inserted. I cannot figure out how to alter that behaviour under GNOME, unfortunately, as I selected "always do this action" when I first put the DVD in.

If someone knows the solution to the issue, or if someone knows how to change the autorunning of DVDs so I can test that solution, I would be grateful!

---

### Post by mc4man on 2009-09-23
As far as changing default action, many ways, it's in 'file managemeht' which is a menu item in System Preferences that not shown by default.


one way to enable, in terminal
```
alacarte
```

access directly
```
nautilus-file-management-properties
```

or insert dvd and hold down the shift button till you get the pop up

As far as the block error, if it keeps occurring see if you can determine if it starts at or near the layer break, or a about the same area sector wise on multiple disks

There's an app that will show, I'll try it in a bit and see if it works in karmic.

Otherwise many standalone dvd players can be set to show what layer they're on.


edit ; it will work and give a graphical view of a  read ,let me know.

---

### Post by nebcanuck on 2009-09-23
Changing the default setting didn't work. Thanks for telling me how, though!

As for it being related to the disk layer, I don't suspect that's the case. I don't know what app you mean which will show me, but considering the DVD quits at 26 minutes into the first episode on my House CD, I'm pretty sure the layer break should be significantly later.

If I'm wrong, I'm willing to try any app that will tell me to be sure!

---

