---
title: "grey tint in videos"
date: 2007-03-21
forum: Multimedia &amp; Video
---

### Post by kanpachi on 2007-03-21
hello
i'm using dapper on an athlon xp 2800 with 512 ram and a 80 gb hd (i just bought the hd a few weeks ago)
a few days ago, without any warning, 
every video i play started to have a weird grey tint on it, 
however, when i switch to opengl on mplayer, it looks ok
problem is, i'm not the only one using the computer, and the other people using the computer, prefer totem as a video player.
but i have no idea on how to change totem's display to opengl, or how to fix it
any ideas please?

---

### Post by Daveth on 2007-03-25
I found this:

"You can set Totem to use opengl as video output...

You can set Totem to use opengl as video output by editing ~/.gnome2/totem_config file.
Make sure you have this line in totem_config:

video.driver:opengl"

@ [http://forums.fedoraforum.org/search.php?searchid=3592423](http://forums.fedoraforum.org/search.php?searchid=3592423)

which might help you. Looks like you can do it.

---

### Post by enopepsoo on 2007-03-25
if you use VLC you can use filters to gain a lot of control over the output.

---

