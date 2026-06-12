---
title: "Displaying MIDIs"
date: 2008-10-01
forum: Multimedia Software
---

### Post by echo314 on 2008-10-01
How might I go about displaying a midi file. I don't so much care to play it, I just am interested in the notes...

---

### Post by blingo on 2008-10-02
Install NoteEdit from Add/Remove.
There are more related programs there.

---

### Post by echo314 on 2008-10-02
NoteEdit does not seem to work with .midi's, just .not files...

---

### Post by blingo on 2008-10-02
In NoteEdit go to:
File
Import
Import Midi
and select your Midi file.

After importing check Auto-Bar and Auto-Beam, clean-up rests, etc
in the Edit Menu, here's info:
[http://noteedit.berlios.de/doc/modify.html#autobar](http://noteedit.berlios.de/doc/modify.html#autobar)
Using them may help or not.

And you can later export as Midi vie 
File 
Export
Export Midi.

Here is the .doc
[http://noteedit.berlios.de/doc/index.html](http://noteedit.berlios.de/doc/index.html)
might not be the same version you've installed,
But I gauss it'll do.

---

### Post by echo314 on 2008-10-03
Of course you were right the first time, NoteEdit does work with the import option!

Lastly, any way I convert the notes just to letters? Would be way easier for me to play..I know the timings already.

---

### Post by echo314 on 2008-10-06
Still here!  ;)

---

### Post by blingo on 2008-10-09
I saw that Noteedit does have something to do with chords, but I don't
know how it works, so the way I see it is either:
1) try to activate the chords thing on Noteedit.
2) Find another program that can handle chords,
like [http://www.greenhedges.com/mchord2.htm](http://www.greenhedges.com/mchord2.htm)
which does work with Wine.
Or another program,
I'm sure that this option exists in one of the many Linux programs out there (or even inside NoteEdit), just don't have the time to search for it. I assume that analysis of midi to chords is the best way to go,
as there is less noise,
however:
3)
If you have the file in .wav
You can try to use
[http://www.seventhstring.com/xscribe/overview.html](http://www.seventhstring.com/xscribe/overview.html)

You can also use Timidity to convert the .mid to .wav
install Timidity and write in terminal
timidity source.mid -Ow

---

### Post by blingo on 2008-10-09
You can install
Tuxguitar

go to 
File
import
import midi

and after that from the menu above: 
Layout
show Fretboard

It rocks!

:guitar:

---

### Post by echo314 on 2008-10-10
Well this is odd. ```
Setting up java-common (0.28ubuntu3) ...

Setting up fastjar (2:0.95-1) ...

Setting up libgcj8-jar (4.2.3-2ubuntu6) ...
Setting up libgcj8-1-awt (4.2.3-2ubuntu6) ...
Setting up libswt3.2-gtk-jni (3.2.2-5ubuntu2) ...
Setting up libswt3.2-gtk-java (3.2.2-5ubuntu2) ...
Setting up java-gcj-compat (1.0.77-2ubuntu2) ...
Setting up liblog4j1.2-java (1.2.15-2) ...
Setting up libitext-java (1.4.5-3) ...
Setting up tuxguitar (0.9.1-4ubuntu1) ...

Setting up libregexp-java (1.4-4) ...

Setting up libbcel-java (5.2-3ubuntu1) ...
Setting up libmx4j-java (3.0.1-3) ...
Setting up java-gcj-compat-headless (1.0.77-2ubuntu2) ...

ed@linux:~$ tuxguitar
/usr/bin/tuxguitar: 21: /usr/local/opt/java/jre/bin/java: not found

```

Looks like I need a specific java package installed...

---

### Post by blingo on 2008-10-10
I think you didn't had Java before..

Check out
[http://www.tuxguitar.com.ar/forum/4/612/can%27t-open-tuxguitar/](http://www.tuxguitar.com.ar/forum/4/612/can%27t-open-tuxguitar/)

---

### Post by minky311 on 2008-10-10
Open up synaptic package manager and search for **sun-java6-jre** and install it.

Or open up a terminal and do the following
```
sudo apt-get install sun-java6-jre
```

---

### Post by blingo on 2008-10-10
In case you can't open the link (I know I can't..)
try
[http://www.google.co.il/url?sa=t&source=web&ct=clnk&cd=2&url=http%3A%2F%2F64.233.183.104%2Fsearch%3Fq%3Dcache%3ACrgM-hdKz4AJ%3Awww.tuxguitar.com.ar%2Fforum%2F4%2F612%2Fcan%2527t-open-tuxguitar%2F%2B%2Fusr%2Flocal%2Fopt%2Fjava%2Fjre%2Fbin%2Fjava%3A%2Bnot%2Bfound%26hl%3Diw%26ct%3Dclnk%26cd%3D2%26gl%3Dil%26client%3Dfirefox-a&ei=GenuSLPLMoji1wbBmPCyBw&usg=AFQjCNEmyUwZMb8vOk27peOGC77NEcvbRw&sig2=PRKSMoTPDWIQDi1KjWi1hA](http://www.google.co.il/url?sa=t&source=web&ct=clnk&cd=2&url=http%3A%2F%2F64.233.183.104%2Fsearch%3Fq%3Dcache%3ACrgM-hdKz4AJ%3Awww.tuxguitar.com.ar%2Fforum%2F4%2F612%2Fcan%2527t-open-tuxguitar%2F%2B%2Fusr%2Flocal%2Fopt%2Fjava%2Fjre%2Fbin%2Fjava%3A%2Bnot%2Bfound%26hl%3Diw%26ct%3Dclnk%26cd%3D2%26gl%3Dil%26client%3Dfirefox-a&ei=GenuSLPLMoji1wbBmPCyBw&usg=AFQjCNEmyUwZMb8vOk27peOGC77NEcvbRw&sig2=PRKSMoTPDWIQDi1KjWi1hA)

or simply:

someone suggested to use

sudo apt-get install sun-java6-jre 
then 
(making sure Sun java is used vie) using 
sudo update-java-alternatives -s sun-java6-jre.

---

