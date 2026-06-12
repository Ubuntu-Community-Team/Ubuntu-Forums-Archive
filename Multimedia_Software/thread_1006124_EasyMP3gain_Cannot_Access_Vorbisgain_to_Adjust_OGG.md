---
title: "EasyMP3gain Cannot Access Vorbisgain to Adjust OGG/OGA Files"
date: 2008-12-09
forum: Multimedia Software
---

### Post by OzzyFrank on 2008-12-09
Hi. I've posted a bug report about this, but thought I better post here too, in case someone has found a fix or workaround. Basically, I have **mp3gain** and **vorbisgain** installed properly, but **[COLOR="DarkRed"]easymp3gain[/COLOR]** cannot access **vorbisgain**, even though it is installed and works fine from the command line. Apparently, [COLOR="#8b0000"]**easymp3gain**[/COLOR] should be able to now work with **.ogg** files (and **.oga** files), but it comes up with "**[COLOR="Blue"]Error: Cannot start vorbisgain. Install...[/COLOR]**" (and then I can't see any more in the status bar, but I am assuming it goes on to tell me to install **vorbisgain**, which is already installed). Any ideas? (Besides telling me to use the terminal... the question is how to get the **mp3gain** frontend to also work successfully as the **vorbisgain** frontend). Cheers. Frank

---

### Post by Giantics on 2008-12-10
Hello Frank,

can easyMP3Gain acess to mp3gain? If this problem only concerns vorbisgain it sound quite strange. Have you checked the vorbisgain command-line 
("Options"->"Advanced"->"VorbisGain backend")? Please test it with the full path to the binary.

Greetings
Thomas

---

### Post by OzzyFrank on 2008-12-13
Yes, it accesses **mp3gain** just fine, **vorbisgain** is the backend in Options (and works via the terminal), but I will stick the full path in Options and see if that makes a difference. Nup, now the error also includes the path to vorbisgain, but no other difference than that.

I should also add that I first noticed this at a friend's place, as he is the one who actually has his collection as .ogg files (mine is in .mp3 format). I wanted to see if it could be duplicated on my system and sure enough, same problem here. So as far as I've personally seen, it has a 100% failure rate with vorbis files, hehe.

---

### Post by Giantics on 2008-12-15
OK, as this seems to be a real Ubuntu bug lets continue this discussion in the launchpad bug report.

---

### Post by OzzyFrank on 2008-12-18
Some interesting info: Now when I open a folder of .oggs (as opposed to opening files) I can edit the gain (?!?!???). I can assure you it wasn't the case before, but the last few times I experimented it was opening an individual file... then tried again on a whole folder and it worked. But on my friends PC opening folders still does nothing but give an error.

PS: I logged into Launchpad, but unlike the KDE bug reporting site, I can't find a way to access bug reports I started (at the KDE site all are easily accessible through a My Bugs link). Any info on this would be appreciated.

---

