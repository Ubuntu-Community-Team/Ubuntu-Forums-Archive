---
title: "Amarok will not change m4a audio tags"
date: 2008-06-28
forum: Multimedia Software
---

### Post by jbaerbock on 2008-06-28
So I have a music collection managed by Amarok but I have some m4a audio filed in the uknown artists folder and Amarok will not let me change the tags (track info) on them. Any way I can get them changed?

---

### Post by cozmicharlie on 2008-06-28
I don't believe Amarok supports m4a tagging.  The only program I have found that does is Xfalso (see this thread for a discussion [http://ubuntuforums.org/showthread.php?t=502349&highlight=easytag](http://ubuntuforums.org/showthread.php?t=502349&highlight=easytag)).  If you want an integrated player you could check out Quod Libet - it has Xfalso integrated into it.

Enjoy

---

### Post by jbaerbock on 2008-06-28
Ok I'll give exfalso a shot. These files are reminicent from my XP days before i figured out how to rip CDs with mp3 instead of default. Been trying to use soundKonverter to convert them but no such luck thus far.

---

### Post by jbaerbock on 2008-06-28
Ok converting to no format worked except when selecting AC3 in soundKonverter and using lowquality. For some odd reason this works fine for converting m4a's when converting them to any other format failes miserably lol. Ah well w00t :)

---

### Post by jbaerbock on 2008-06-28
For some reason one converted but the rest wont, anyway that tag editor works awesome thanks!

---

### Post by cozmicharlie on 2008-06-28
> **jbaerbock said:**
> Ok converting to no format worked except when selecting AC3 in soundKonverter and using lowquality. For some odd reason this works fine for converting m4a's when converting them to any other format failes miserably lol. Ah well w00t :)

You should be able to convert m4a to any format in SoundKonverter.  Do you have the faac, faad and gstreamer plug ins all installed?

Glad Xfalso worked for you.

---

### Post by jbaerbock on 2008-06-28
Yes yes and yes :(. Have all of em and it konverts it but when you look at the size of the output file it is like 120kb or so and when played is a bunch of noise and thats it. Oh and it did convert the one m4a but the other it would not for some odd reason. Ah well.

---

### Post by cozmicharlie on 2008-06-28
> **jbaerbock said:**
> Yes yes and yes :(. Have all of em and it konverts it but when you look at the size of the output file it is like 120kb or so and when played is a bunch of noise and thats it. Oh and it did convert the one m4a but the other it would not for some odd reason. Ah well.

There are other methods - this explains how to use a different decoder [http://ubuntuforums.org/showthread.php?t=631835](http://ubuntuforums.org/showthread.php?t=631835).  And, pacpl now has the ability to use a different decoder and integrates into Amarok.   This tutorial explains how to install and use pacpl [http://ubuntuforums.org/showthread.php?t=712064&highlight=pacpl](http://ubuntuforums.org/showthread.php?t=712064&highlight=pacpl).  If you want to try one of this alternative methods and need help just post back to this thread and I will help.

---

### Post by jbaerbock on 2008-06-29
No thanks, now that the m4a's are labeled correctly I should be fine. Besides I re-installed into Ubuntu 8.04 so am using Banshee instead of Amarok.

---

