---
title: "screenshot movie program??"
date: 2007-11-22
forum: Multimedia &amp; Video
---

### Post by rbprogrammer on 2007-11-22
i need a program that will capture my screen output as well as audio.  i have tried "recordmydesktop" but it does not seem to save in any file format except for ogg.  also the audio does not work for me.  i need something that will save to an avi or mp4.  does anyone know of any other program??

---

### Post by rbprogrammer on 2007-11-26
just an update, by reading the post : [http://ubuntuforums.org/showthread.php?t=294605](http://ubuntuforums.org/showthread.php?t=294605) , i got the sound to work but installing [FONT="Courier New"]gnome-alsamixer[/FONT] and when that was installed, i just clicked the checkbox "mix".  and whala! sound now worked with my recordmydesktop application.

but that did not fix the dilemma that it only saves to [.ogg].  but, if i install [FONT="Courier New"]mencoder[/FONT], i can do (from that thread) :
```
mencoder -idx input.ogg -ovc lavc -oac mp3lame -o output.avi
```

---

