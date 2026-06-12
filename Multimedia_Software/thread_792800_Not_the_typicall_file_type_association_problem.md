---
title: "Not the typicall file type association problem"
date: 2008-05-13
forum: Multimedia Software
---

### Post by curumbao on 2008-05-13
I know how to change the default application for a file type. I already have my music files to open with audacious, my favourite player nowadays.

But I'm lazy, I usually listen to 3 or 4 different playlists I already have. So I wanted them to be near to be played with a simple click.

I added to the top bar this kind of box where you can enter whatever you want, and I entered my playlists. And what happened? They just opened with Totem! The original playlist opens with audacious, but inside that box it opens with totem.

The same happens if y navigate throug avant-window-navigator file browser applet. If I navigate to my playlists folder and open any of them, it'll open with totem. While navigating through nautilus it opens with audacious.

I've been some hours searching through the forum and through google, but I can't find anything that deals with the problem.

My guess is that somewher there must be like a master file type association list that I cannot find.

Hope someone can help me solve this puzzle. I already eddited /usr/share/applications/defaults.list .

---

### Post by aeiah on 2008-05-13
i think gconf has default applications settings
```
gconf-editor
```

---

### Post by curumbao on 2008-05-14
I already tried that yesterday, with de gconf-editor, but I couldn't find anything usefull. Maybe I didn't notice something.

So, Could you be more specific, please?

---

