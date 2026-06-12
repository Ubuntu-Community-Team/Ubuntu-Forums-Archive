---
title: "Music Notation Program"
date: 2006-09-20
forum: Multimedia &amp; Video
---

### Post by Corey on 2006-09-20
Does anyone use a music notation programs under Dapper? I can't get *any* of them to work. Rosegarden gives some errors before it opens up but once it finally opens I can't press any of the buttons (+ i don't like qt) Denemo crashes often under totally different circumstances and occasionally does other wierd things like when I press quater note it makes a quarter rest. Noteedit crahses on startup. I installed gscore from their autopackage and it too crashes on startup. What do you guys use?

---

### Post by jpkotta on 2006-09-20
> **Corey said:**
> Does anyone use a music notation programs under Dapper? I can't get *any* of them to work. Rosegarden gives some errors before it opens up but once it finally opens I can't press any of the buttons (+ i don't like qt) Denemo crashes often under totally different circumstances and occasionally does other wierd things like when I press quater note it makes a quarter rest. Noteedit crahses on startup. I installed gscore from their autopackage and it too crashes on startup. What do you guys use?

I've never used it, but I'm very impressed with LaTeX, so I would imagine that Lilypond is good too (but probably hard to learn).

[http://www.lilypond.org/doc/v1.6/Documentation/misc/out-www/interview.html](http://www.lilypond.org/doc/v1.6/Documentation/misc/out-www/interview.html)

---

### Post by Corey on 2006-09-21
Lilypond is a fine format and backend for music notation. But what I need is a graphical frontend for it (that works) Learning the syntax isn't bad but would you get into anything more than a simplistic score it gets more complicated. Its also much easier to edit with a frontend where you can SEE what it is you're editing. Plus scripting manually is a lot more time consuming.

---

### Post by dolson on 2006-09-22
Report a bug about Denemo crashing..

---

### Post by Aliby on 2006-09-22
Have you had a look at Noteedit? [http://noteedit.berlios.de/]("http://noteedit.berlios.de/")

It is a good functional notation program with LaTeX and Guitar Chord integration too (ex KGuitar)

It is being superceded by Canorus [http://canorus.berlios.de/]("http://canorus.berlios.de/") which looks really fantastic. I needed an music score editor (similar to Noteworthy) thats what this is.
:D

---

### Post by dolson on 2006-09-22
> **Aliby said:**
> Have you had a look at Noteedit? [http://noteedit.berlios.de/]("http://noteedit.berlios.de/")

It is a good functional notation program with LaTeX and Guitar Chord integration too (ex KGuitar)

It is being superceded by Canorus [http://canorus.berlios.de/]("http://canorus.berlios.de/") which looks really fantastic. I needed an music score editor (similar to Noteworthy) thats what this is.
:D

[QUOTE=The original poster]Noteedit crahses on startup.[/QUOTE]

I guess that answers it.

Sounds to me like Corey's system is totally f*$#ed up. There is no way every single note-editing application crashes on startup unless something is very wrong.

---

### Post by fuoco on 2006-10-19
Did you find any such program?
I'm in urgent need for notating. I used to do lilypond - but it's just not feasible, it took ages just for a simple string quartet... must use a gui.

---

### Post by Corey on 2006-10-20
Yup I found a program. Finale Notepad on my Windows partition. ](*,)

---

### Post by fuoco on 2006-10-20
I used that once and it wasn't so good for me. I remember I couldn't extract parts from the score and that really sucked. Besides I don't have any windows around....
I can't really stick to paper and pencil, and I don't know how people used to do that for ages! 
:P

---

### Post by goodmanbrown on 2006-10-21
Hey Aliby-- thanks for the tip on Canorus.  I was disappointed with noteedit's apparent stagnation, and am excited to see that it is being superceded.

I hope Canorus development doesn't stall.  I look forward to the day when I can use a score editor as elegant as noteedit, but without all its annoying quirks and bugs.

---

### Post by coder_ on 2006-10-22
I actually prefer editing Lilypond source by hand, 'cos it's more fun.

---

### Post by christhemonkey on 2006-10-22
If your still looking, you can try musescore
[http://mscore.sourceforge.net/](http://mscore.sourceforge.net/)


There is a thread with howto copmile it, on the forums here(you have to read the whole thread im afraid :p):
[http://ubuntuforums.org/showthread.php?t=193848](http://ubuntuforums.org/showthread.php?t=193848)

Also finale works quite well in wine apparently.
As well as Noteworthy Composer that the OP used in windows in that thread.

---

### Post by mssever on 2006-10-23
> **christhemonkey said:**
> Also finale works quite well in wine apparently.
Thanks for the tip. I've installed Finale Notepad 2005a and I have one problem. It sounds like you haven't actually tried Finale, but I'll ask anyway.

When I open or create a file, I get the an error complaining about no MIDIMAP.CFG (see attached screenshot). I haven't been able to find such a file on my XP Pro partition (and Finale Notepad is installed there, too) or on Google. Without this file I can't hear playback.

Does anyone know anything about this file or where I can get it? Or maybe someone can simply send me theirs? If you can't post it here, PM me and I'll give you my email address.

---

### Post by christhemonkey on 2006-10-23
The midimap.cfg is a config file containing all the midi device setups,
It is found in \windows\system\ on a typical windows install.
So i would recommend copying it out of your current windows install as it will differ from pc to pc.

Also make sure you have midi enabled in wine (in the wine config thing)


EDIT: On my windows XP install, i can only find 2 midimap.dll's in C:\windows\system32\
Im not sure how you should proceed im afraid.
It seems that the midimap.cfg should be supplied by the sound card vendor on its driver cd/floppy.

And you dont seem to be the only person with this problem:
[http://crossover.codeweavers.com/pipermail/discuss/2004-September/007236.html](http://crossover.codeweavers.com/pipermail/discuss/2004-September/007236.html)

---

### Post by CaptainSumo on 2006-10-23
I also remember getting the crash in Noteedit on startup. If I remember correctly, it had to to with a module that was missing from the standard startup. I think it was solved with: 
[B]
sudo modprobe snd_seq[/B]

But this was a while ago, so I'm not certain if that was the one. 

I eventually gave up trying to use a GUI for score editing and taught myself the Lilypond syntax. Both Noteedit and Rosegarden were far too dependent on the mouse. Denemo looked promising, but was way too unstable and unpredictable for serious use.

---

### Post by christhemonkey on 2006-10-23
If your using alsa, that would be:
```
sudo modprobe snd-seq 
```


Add it to the end of the file /etc/modules
to have it booted everytime.

---

### Post by mssever on 2006-10-23
> **christhemonkey said:**
> The midimap.cfg is a config file containing all the midi device setups,
It is found in \windows\system\ on a typical windows install.
So i would recommend copying it out of your current windows install as it will differ from pc to pc.
Hmmm... My XP install has no midimap.cfg. My Win98 install (on another machine) has a midimap.cfg that contains a single null byte (\0). It didn't work.
> Also make sure you have midi enabled in wine (in the wine config thing)

EDIT: On my windows XP install, i can only find 2 midimap.dll's in C:\windows\system32\
Im not sure how you should proceed im afraid.OK. I've copied over the midimap.cfg file I mentioned above, I symlinked midimap.dll from my XP install into wine's system32 directory, and ran sudo modprobe snd_seq. This combination stops the error message from appearing. It looks normal when I hit the play button, but I get no sound.

When I tried to check my wine config, I ran into more trouble. Every time I click the audio tab in winecfg, winecfg crashes and prints the following in the terminal window: ```
Creating link /home/scott/.kde/socket-scott-laptop.
can't create mcop directory
```If my memory is correct, mcop is a KDE thing. I run Gnome and don't have KDE installed (though I do have some KDE libs due to having several KDE apps installed). Any ideas about what's going on? Why does wine even care about KDE? Or, is there another way to look at wine's audio settings?

EDIT: I tried winecfg on my desktop, which does have KDE installed--though it's running Gnome. Same error.

EDIT 2: I logged in to KDE on my desktop, and was able to successfully access the audio tab. Is there any way to get the audio tab on my laptop (which I use 90% of the time) without using valuable disk space for a KDE install? Also, isn't OSS the Gnome sound system and ALSA the KDE system?

> It seems that the midimap.cfg should be supplied by the sound card vendor on its driver cd/floppy.I'll look for it on my driver CDs when I get a chance.

> And you dont seem to be the only person with this problem:
[http://crossover.codeweavers.com/pipermail/discuss/2004-September/007236.html](http://crossover.codeweavers.com/pipermail/discuss/2004-September/007236.html)I saw that post, too. Unfortunately, no one answered it.

---

### Post by tubasoldier on 2006-10-28
One thing that is not mentioned in this thread is that Noteworty runs quite well under wine. And if you have a soundcard that can use soundfonts then setting up midi playback is a snap!

---

### Post by LeslieL on 2006-11-02
I've just got Noteworthy running well under Crossover Office, which is a commercial & easier version of wine. I posted some things I learned [here]("http://ubuntuforums.org/showthread.php?t=188888").

---

### Post by dfro on 2006-11-03
Another program to try would be xcircuit.  It is primarily designed for creating electronic schematics, but any symbols can be created from scratch and typeset however you like.  On the home site there is a download section, where you can download a library of music symbols and then import them into xcircuit.  I like the idea of using this program, because you can place each symbol exactly where you want it - just like Gutenberg laying out his letter blocks.  It may be tedious, but it is a WYSIWYG process.  If you are missing a symbol, just make a new one.

   I am going to give this program a try.  Also, you can 'apt-get' it so there are no hassles getting it to work.

---

### Post by dfro on 2006-11-03
Another program to try would be xcircuit.  It is primarily designed for creating electronic schematics, but any symbols can be created from scratch and typeset however you like.  On the home site there is a download section, where you can download a library of music symbols and then import them into xcircuit.  I like the idea of using this program, because you can place each symbol exactly where you want it - just like Gutenberg laying out his letter blocks.  It may be tedious, but it is a WYSIWYG process.  If you are missing a symbol, just make a new one.

   I am going to give this program a try.  Also, you can 'apt-get' it so there are no hassles getting it to work.

---

### Post by LeslieL on 2006-11-04
Good for drawing music on the screen, but you really need to be able to play it back. For that noteedit or Noteworthy Composer are really the only solutions that work.

---

### Post by etilli33 on 2006-12-07
Hey,

is there anybody around who knows if canorus is going to be included into ubuntu (edgy) repositories, or did anybody try the deb from their homepage -- is it working under edgy?

best regards

till

---

### Post by handy on 2006-12-07
My wife & I are just hanging out, waiting for the day that Sibelius is ported over to Linux, or even better if some incredibly motivated people make something even better than Sibelius that is a native Linux app'.

Either way, WOW!

---

### Post by cvmostert on 2006-12-10
i would also wait for sibeius, great program!

---

### Post by nkayesmith on 2007-06-08
Does anyone still have the gscore autopackage? It is no longer available on the gscore website, and I'd like to try it.

---

