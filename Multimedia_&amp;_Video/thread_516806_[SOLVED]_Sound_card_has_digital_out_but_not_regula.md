---
title: "[SOLVED] Sound card has digital out but not regular"
date: 2007-08-03
forum: Multimedia &amp; Video
---

### Post by pgcudahy on 2007-08-03
I just set-up the Feisty alternate install so I could set up a mythtv box. Most things came up automatically but I'm having a strange problem with my sound card. It's a SB audigy and when I play any audio nothing comes out of the two regular minijack outputs but when I plug a regular line into the digital out I get really scratchy output. I tried unmuting with alsamixer but that hasn't helped. Any suggestions? Thanks.
-Patrick

---

### Post by benerivo on 2007-08-03
I had a similar sounding problem when i installed. I had to add the volume applet to the menu bar and open the sound settings from there. Under the 'Switches' tab i unclicked the 'analog/digital' box and both of the minijack outpuits started working.

---

### Post by pgcudahy on 2007-08-04
Thanks for the tip. Is there any way to do that from the command line?

---

### Post by benerivo on 2007-08-04
```
gnome-volume-control
```

---

### Post by pgcudahy on 2007-08-05
Well I wasn't able to get that working from the command line but I used alsamixer and muted the analog/digital output jack and that did the trick. Thanks for the help.

---

