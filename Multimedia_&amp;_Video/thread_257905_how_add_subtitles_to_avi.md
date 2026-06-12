---
title: "how: add subtitles to avi?"
date: 2006-09-15
forum: Multimedia &amp; Video
---

### Post by stevieb on 2006-09-15
anyone know of any software that will allow me to add subtitles to an .avi file?

thanks,
-steve

---

### Post by mtron on 2006-09-15
hi steve! 

you will need the subtitles in .srt format, in the same directory, with the same filename (except the .srt ;) )

than mplayer will pick it up automatically

cheers mtron

---

### Post by stevieb on 2006-09-15
ok, a stupid question:

how do i get the text into the appropriate format?  is there a program for generating .srt files?

thanks,

-steve

---

### Post by mtron on 2006-09-15
nope, there are many sites for this. eg.

[http://subscene.com/](http://subscene.com/)
[http://divxstation.com/softwarecat.asp?category=6](http://divxstation.com/softwarecat.asp?category=6)

use google!

---

### Post by stevieb on 2006-09-15
These sites won't have the subtitles I wrote; I haven't put them in anything yet.  These sites seem designed to import subtitles that already exist.  I have a text file that consists of a translation of a german film that was not released with english subtitles; i want to add subtitles to the .avi file.

-steve

---

### Post by mtron on 2006-09-17
Ah, sorry, didn't know what you wanted to do. there's the layout for a srt subtitle file. There are some helper apps for creating them more at [doom9.org ]("http://forum.doom9.org/showthread.php?t=18474")

1
00:00:43,677 --> 00:00:46,578
Was läuft hier ab?
Und wieso bin ich hier?


2
00:00:52,386 --> 00:00:55,082
Woher kommen wir?
Was bewirkt Quantenphysik?

3
00:00:55,188 --> 00:00:58,214
Immense quantenmechanische Isotopen.
Physik der Möglichkeiten.

4
00:00:58,325 --> 00:01:01,089
Quantenmechanik ermöglicht den...

5
00:01:04,865 --> 00:01:06,924
höchstmöglichen Verstand.


[B]Running Number
timestamp subtitle begin - timestamp sub end
Text displayed in Line 1 
Text displayed in Line 2
[/B]

Quite easy in theory, but shitloads of work. Hope this helps.

---

### Post by stevieb on 2006-09-17
actually, I found a program in the repositories called Ksubtile (yes, that's how it's spelled) that does the trick!

thanks!
-steve

---

