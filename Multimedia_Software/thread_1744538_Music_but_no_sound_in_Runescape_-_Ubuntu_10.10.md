---
title: "Music but no sound in Runescape - Ubuntu 10.10"
date: 2011-04-30
forum: Multimedia Software
---

### Post by Kendrone on 2011-04-30
I have had this problem a long time but I am unsure on how to solve. I am using ubuntu 10.10

When playing the Java based Game "Runescape", I am able to get the game music, but absolutely no sound effects or scenery sound. I have checked that all are at maximum volume, my sound works for everything else I do in total - this includes skype, youtube and minecraft - but not for the sounds in runescape.

I should note, I am a complete newbie when it comes to dealing with this. I can copy and paste into a terminal, but that is about it.

Please help.

---

### Post by Strebenherz on 2011-05-09
Sorry for your difficulties.  I've tried playing Runescape on Ubuntu as well, but run into different difficulties sometimes..  If I may please ask, what browser are you using?  Is Java updated?  Either update manager or going to the site.  Here's the link for Java.  There's a link that lets you check if you have the current 
[http://www.java.com/en/](http://www.java.com/en/)
Hoping that helps.  I went through the "Check your edition of Java" and it said mine was a tad out of date.  o.O
Oddly, I use firefox and the game loads, sounds function, but there are occasional weirdness areas.

---

### Post by Kendrone on 2011-05-10
Got a dual solution off the runescape forums.
 
One part which was runescape music blocking out all other sound, or not starting if another program was using sound (such as youtube) is fixed by the command ```
padsp <browser name> 
```
Where <browser name> is replaced such as google-chrome or fiefox.
 
The second part, getting all sound tracks in runescape to play, was simply to switch to google-chrome. For some reason, Chrome is able to play both (in mono only for some users) whilst firefox is limited to just BGM.
 
THIS IS NOW SOLVED.

---

