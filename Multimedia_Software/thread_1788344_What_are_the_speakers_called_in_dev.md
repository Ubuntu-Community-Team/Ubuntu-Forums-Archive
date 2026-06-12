---
title: "What are the speakers called in /dev?"
date: 2011-06-22
forum: Multimedia Software
---

### Post by UmlautBanana on 2011-06-22
This might be a stupid question, or depend on my sound card (which is Realtek, I think), but which file/folder in /dev is my speakers? In fact, a page with the meaning of all the /dev folders would be nice if that exists, but if not, just the speakers.

---

### Post by Yellow Pasque on 2011-06-22
Speakers are not going to show as /dev files. What are you trying to do?

---

### Post by UmlautBanana on 2011-06-22
I read that you can redirect the output of "cat file.wav" to /dev/audio or whatever to play it. I know I can just open it in a media player but it'd still be nice to know where they are. But they won't show in /dev? What will show there?

---

### Post by Yellow Pasque on 2011-06-22
> But they won't show in /dev? What will show there?
soundcard outputs (/dev/snd)

---

