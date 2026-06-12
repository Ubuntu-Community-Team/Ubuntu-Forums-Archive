---
title: "Amarok using 100%CPU on Ubuntu"
date: 2007-11-23
forum: Multimedia &amp; Video
---

### Post by luisjorge on 2007-11-23
Hi everyone! I've been using Amarok since Feisty, and I think it might be the best music player around. The thing is, I'd never had problems with amarok, but now every time I open it, it takes the CPU up to 100% for a few seconds, then it goes back to normal. I figured this was when it was loading my music collection, so it was fine.
But then, it takes the CPU up to 100% for about 40 seconds EVERY TIME it changes a song. No matter what I do, or what or where the song is, it does the same thing. This never happened in feisty. I'm using Gutsy, and Amarok v1.4.7.

Any ideas on how to fix this?

Thanks in advance for any help!!!

Luis Jorge.

---

### Post by luisjorge on 2007-11-26
Hi! I just realized one thing: Amarok uses 100% of the CPU almost for any task! For choosing an album cover for a song, saving a playlist, changing to the next song, etc...

Any help, anyone?

Thanks!!!

Luis Jorge.

---

### Post by SyL on 2007-12-16
Is amarok keeps updating the collection?
if so, have a look a this thread: [http://ubuntuforums.org/showthread.php?t=591647&highlight=amarok+CPU]("http://ubuntuforums.org/showthread.php?t=591647&highlight=amarok+CPU")

1/ turn off watch folder option
2/ delete ~/.kde/apps/share/amarok/collection.db
3/ turn on the watch folder option

it worked for me!

---

