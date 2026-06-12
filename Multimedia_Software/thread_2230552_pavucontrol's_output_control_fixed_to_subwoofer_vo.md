---
title: "pavucontrol's output control fixed to subwoofer volume instead of master with 5.1"
date: 2014-06-19
forum: Multimedia Software
---

### Post by waitingroomsnap on 2014-06-19
Howdy.  I'm not quite sure how to go about fixing this problem.  I have a 5.1 audio card, and everything is working fine, except for the output volume control for pavucontrol / sound settings.  For some reason, adjusting the volume output in the pavucontrol panel indicator or in the ubuntu sound settings only changes the subwoofer volume, and not the master volume.  I can open alsamixer and adjust the master there effectively, but it's kind of annoying not being able to do it via the unity panel.  Any help would be appreciated!

---

### Post by lidex on 2014-07-01
If you have pulse audio volume control try using it to configure pulse.
The command is ```
pavucontrol
```

---

