---
title: "EasyTAG encoding issues"
date: 2006-10-28
forum: Multimedia &amp; Video
---

### Post by uziel on 2006-10-28
Few days ago I installed Dapper (after messing my Breezy installation too much) and now I'm concerned with strange behaviour of newer versions of software I used.

A problem I can't fix is about my mp3 files. I prefer tags written in iso-latin2 charset (which btw is my locale and the charset of the disk my files are on), and old Rhythmbox did interpret the tags properly. The new (0.9.3.1) doesn't, it displays the chars as if they were in iso-latin1.

But this post ain't about Rhythmbox.

I decided to give Unicode a try. I selected "always save in UNICODE character set" in my EasyTAG (version 1.99.11) and tagged the files. And there was problem with one character: "ó" (oddly enough this is the only Polish symbol present in iso-latin1 charset). Both Rhythmbox and EasyTAG recognise it as "&#65523;". I am puzzled - EasyTAG can't properly read information it had created itself.

Tagtool isn't a good solution, it interprets the tags even worse.

What to do?!

---

### Post by sup on 2006-10-29
I wrote a [Howto]("http://ubuntuforums.org/showthread.php?t=287811&highlight=easytag") about solving the problem:

---

