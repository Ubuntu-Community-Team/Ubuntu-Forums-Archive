---
title: "Launching two VLC windows using a script"
date: 2008-05-29
forum: Multimedia Software
---

### Post by b166er on 2008-05-29
Yesterday I ran into a problem when trying to run a script that should launch two vlc windows. The script looks something like this:

vlc -ZL /home/rickard/playlist1.m3u
vlc -ZL /home/rickard/playlist2.m3u

The problem I'm having is that the second line won't start until I close the first vlc window. I think that this is because vlc won't say that it's finished until it has finished playing the files in the playlist. (note that I have vlc set to repeat). If I on the other hand make two scripts (one containing the first line and the other script the second line) and then launch them manually everything seams to work (I can have both windows play the same time).
  Is there something I can put in the script that states to not wait for vlc to  finish?

---

### Post by kpkeerthi on 2008-05-29
You need to background the commands (with an '&' character) in the script file as in
```

#! /bin/bash
vlc -ZL /home/rickard/playlist1.m3u &
vlc -ZL /home/rickard/playlist2.m3u &

```

---

### Post by b166er on 2008-05-29
Ah! sweet. It worked.
I remember something about the & now. But I have only used it when x wouldn't start.
Thanks man

---

