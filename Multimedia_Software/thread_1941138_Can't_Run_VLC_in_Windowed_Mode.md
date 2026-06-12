---
title: "Can't Run VLC in Windowed Mode"
date: 2012-03-15
forum: Multimedia Software
---

### Post by Ubuntist on 2012-03-15
Since upgrading to Oneiric, I can't open VLC in windowed mode (where it doesn't fill the entire screen).  I can minimize VLC, I can maximize it, but I can't resize it.  More generally, the controls bar (the one that appears when the cursor is moved to the top of the screen if an application is maximized) never appears.

Anybody have any ideas how to fix this?

---

### Post by papibe on 2012-03-15
Hi Ubuntist.

If you haven't customized VLC too much, or don't mind re doing it again, you can delete all stored settings by doing:
```
rm -rf ~/.config/vlc
```
Just a thought.
Regards.

---

### Post by Ubuntist on 2012-03-19
Thanks, papibe, removing the configuration file solved it!  To my knowledge, I had never configured VLC in the first place, so there was nothing to re-configure anyway.

---

### Post by papibe on 2012-03-19
:D Good news then! Please mark the thread [solved]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads") when you have the chance.
Regards.

---

### Post by Ubuntist on 2012-03-20
Done.  And thanks for showing me the mark-thread-solved technique too!

---

