---
title: "Power Tab"
date: 2007-06-20
forum: Multimedia &amp; Video
---

### Post by liquidfunk on 2007-06-20
My band has been using Powertab for a while just to tab out our songs onto our computers. 

 Is there a Linux equivalent or some kind of software that will read and display the Powertab format file 'ptb'.

 Any ideas?
 
 Or has anyone got it working with Wine. 

 Native is preferred.

---

### Post by oooooops on 2007-06-20
I'm not sure what PowerTab is exactly (i'm  a new and trying to learn guitarist) but I've been using [http://www.tuxguitar.com.ar/home.html](http://www.tuxguitar.com.ar/home.html)  Tux Guitar

---

### Post by texas8112 on 2008-01-07
i did a search in the synaptic for the word 'guitar' and it came up with a couple tab viewers/editor

---

### Post by infomissing123 on 2008-03-12
I got several solutions for this (I outlined them all here: [http://ubuntuforums.org/showthread.php?t=707870&highlight=powertab]("http://ubuntuforums.org/showthread.php?t=707870&highlight=powertab")
None are perfect but they get me by in the mean time.

---

### Post by rekado on 2008-05-14
I just made Powertab work in Ubuntu 8.04.
In my case I just had to copy one DLL into the system32 folder of Wine (msvcirt.dll).

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=2784](http://appdb.winehq.org/objectManager.php?sClass=version&iId=2784)

I use Timidity for MIDI output.
There are still some bugs but it is usable and you can playback the files.

---

### Post by DreamTrooper on 2008-05-14
I have found a great Tab Program, i'm not quite sure if it reads .PTB files, but i DO know it reads Guitar Pro Files (.gp3/.gp4/.gp5) which is what i use mostly. All you have to do is type:

```
Sudo apt-get install tuxguitar
```

into Terminal, follow the instructions, and your good. You'll find the icon under Applications>Sound&Video> Tuxguitar.

Cheers :guitar:

---

### Post by infomissing123 on 2008-05-17
> **rekado said:**
> I just made Powertab work in Ubuntu 8.04.
In my case I just had to copy one DLL into the system32 folder of Wine (msvcirt.dll).

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=2784](http://appdb.winehq.org/objectManager.php?sClass=version&iId=2784)

I use Timidity for MIDI output.
There are still some bugs but it is usable and you can playback the files.

Same here.  Whatever the wine team did fixed the issues I was having and it runs now.  It's not perfect but I have editing and playback.  Playback is a little choppy, especially on busy tabs but it's usable.

I also got guitar pro 5.2 working.

---

