---
title: "Can't get mplayer to work with lirc on no-gui system"
date: 2010-03-26
forum: Multimedia Software
---

### Post by lumix on 2010-03-26
I'm setting up a gui-less music server so there's no login, and I've tried using mplayer's lirc interface as well as irexec (sending mplayer slave commands to a fifo).  But I can't get mplayer to work unless I start either irexec or mplayer from a logged in session. So my S99test is something like:

```

#!/bin/sh
#irexec -d
#OR
#mplayer myfile.mp3

```

If I use the "mplayer" line, I do hear music at startup, but no lirc control.  Yet if I log in and kill the mplayer and rerun S99test as root, all works fine.

---

### Post by lumix on 2010-03-28
No thoughts?

---

### Post by Ryhi on 2011-04-26
Hi lumix
U c lirc is not runing, it only runs wen u log in as a user ie in2 a diferent runlevel. Runlevel 1 doesnt start lirc. U can copy the runlevel scripts from runlevel 2 3 4 or 5 to runlevel 1. U can create a playlist 4 mplayer aswel in plain text (if you want). Ps msg sent frm my mobile. Hope it helps.
Has this message helped anyone, could you please let me know.
cheerz

---

