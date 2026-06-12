---
title: "Amarok skips first few seconds of mp3"
date: 2008-02-23
forum: Multimedia &amp; Video
---

### Post by akwatve on 2008-02-23
Hi,

My Amarok behaves peculiarly. When I have aplaylist of mp3s, it just skips first few seconds  of current file  (and I suspect last few seconds of the previous file). I earlier thought that this is due to crossfading. but this happens even after, I disabled it ......

When I play the file double clicking it, amarok sweetly plays the file right from the start. I believe this is some preferences issue but couldn't find anything that will fix this.

Thanks,

---

### Post by akwatve on 2008-03-03
*bump*

---

### Post by enigma_0Z on 2008-03-31
*bump*

Similar problem here, but a bit different.

Amarok skips the first few seconds of a song if I double click it, but if the song is transitioned to, there is no skippage.

Try running:

```

xine filename.mp3

```

from the command line (replace filename.mp3 with your mp3 file) and see if there's still a lag. There is on my system.

---

### Post by akwatve on 2008-04-01
I tried to drilled down a bit in to this. I realized that the problem occurs for particular files not for for any mp3. may be something is wrong with the file. 

Unfortunately I do not have xine installed (?). So can't test xine as per enigma_0Z's suggestion. One more interesting thing is, when I tried to install xine, I got following error message:

```
 sudo apt-get install xine
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package xine is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package xine has no installation candidate

```

I am not sure whether this is normal or not :confused:

---

### Post by green0eggs on 2008-05-01
I am having the same problem with AmaroK even running the xine engine (on Kubuntu).

Have turned off cross fading and fadeout and I still get 5second skipping at the beginning of each track on the play list. Playing files individually works fine and they get played from the beginning.

Big apologies if this has already been answered somewhere else. You'll have to excuse my noobness.

Maybe same problem:
[https://lists.ubuntu.com/archives/kubuntu-bugs/2007-September/036327.html](https://lists.ubuntu.com/archives/kubuntu-bugs/2007-September/036327.html)

---

### Post by akwatve on 2008-05-01
I did not get solution but I think this problem is specific some version (or may be some particular "way" of creating) of music files. I used ffmpeg to re-encode my music files and the problem seems to have disappeared since then....

I don't know the exact solution though :-(

*EDIT*

This is what i did :
> ffmpeg -i old.mp3 -ab 256k new.mp3

You may want to give it a try

---

