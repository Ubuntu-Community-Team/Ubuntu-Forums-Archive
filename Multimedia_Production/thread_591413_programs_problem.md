---
title: "programs problem"
date: 2007-10-25
forum: Multimedia Production
---

### Post by qbox on 2007-10-25
Hi
I have problem with programs. When I try to start some program like VLC, Kini, Caffeine, Azureus etc. The program open and close instantly. What can I do.
Thank you.

---

### Post by Stochastic on 2007-10-26
open a terminal, start the program from the commandline (enter "vlc" and hit enter), watch as the program spews out messages to the termial, then start troubleshooting any errors that come up.

---

### Post by qbox on 2007-10-27
I do that and I reseive this

qbox@qbox:~$ sudo -i
root@qbox:~# vlc
VLC media player 0.8.6c Janus
starting VLC root wrapper... using UID 1000 (qbox)
[00000308] ts demuxer error: cannot peek
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  140 (XVideo)
  Minor opcode of failed request:  19 ()
  Serial number of failed request:  83
  Current serial number in output stream:  84
root@qbox:~#

---

### Post by Stochastic on 2007-10-27
do you get similar errors with those other apps?  maybe it's a missing library or an incorrectly configured app.  I don't recognize the error so I can't help too much.

---

### Post by qbox on 2007-10-28
I have same problem vith azureus and another application. But when I turn off Compiz everithing work ok. Any help?

---

### Post by Stochastic on 2007-10-28
I'm no compiz expert and I don't understand the error message you posted so I'd recommend a new thread in the "Desktop Effects & Customization" section of the forums as it seems to be related more to the X server and Compiz than to the specific Multimedia Production programs.  Post that same error message (and maybe other messages from different programs) and describe it as "Compiz breaks my apps".

---

