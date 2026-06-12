---
title: "Add music to play queue from Nautilus?"
date: 2007-11-18
forum: Multimedia &amp; Video
---

### Post by isecore on 2007-11-18
So, I'm trying to figure out a way to do this: 

Double-click a file in nautilus and have it added to the play-queue of Rhythmbox. I've found two threads who both ask for the same thing, yet there's no replies there either.

Essentially I want to be able to browse my library in Nautilus and just simply doubleclick mp3's to add them to my playlist. Is this even possible?

The other two (dead) threads I found was [here]("http://ubuntuforums.org/showthread.php?t=448727") ([http://ubuntuforums.org/showthread.php?t=448727](http://ubuntuforums.org/showthread.php?t=448727)) and [here]("http://ubuntuforums.org/showthread.php?t=201441") ([http://ubuntuforums.org/showthread.php?t=201441](http://ubuntuforums.org/showthread.php?t=201441))

---

### Post by LuserName on 2007-11-27
I'd like an answer to this too.  I highlighted like 20 mp3s once and was really surprised when they all opened in separate instances of VLC.

So if anyone has a way to do this, I'd appreciate it too.  :)

---

### Post by Octagonal on 2007-11-27
+1, I'd like to know if this is possible too.

---

### Post by erginemr on 2007-11-27
Hello,

I believe you can do that with the "Nautilus Actions", a plugin / extension that allows adding extra items to the Nautilus right-click menu.

Its web site is:
[http://www.grumz.net/index.php?q=taxonomy/term/2/9](http://www.grumz.net/index.php?q=taxonomy/term/2/9)

and you can install it simply with:
sudo aptitude install nautilus-actions

from the console. I have it installed in my system already, but did not use it so far. So, I need to play with it first to say more.

---

### Post by erginemr on 2007-11-27
OK. Here is a little howto. The attached screenshots will specak for themselves.

There, first I have installed the package "nautilus-actions" and found its configuration dialog in the 
main menu. I used this dialog to add an option to "*.ogg" files to enqueue them to Totem playlist.

Beforehand, I learned that totem had a parameter "--enqueue" by referring to Totem's man page: "man 
totem". I am not sure with vlc, but you can learn a lot more by checking "man vlc" just as I did for 
totem.

I "added" a new nautilus action, filled in the blanks, added the command to run and its parameters. The 
button that says "Legend" tells me to use %M to indicate multiple files with their paths. 

Finally, on the "Conditions" tab, I have specified the "ogg" extension (but you may extend the selection 
to say, all audio files my using mimetypes, I don't know how though). The important thing here is 
selecting the check mark for "multiple files selection". This, along with %M above will allow you to 
mass-process audio files, instead of right-clicking on them one by one.

This was just an example, but the options are virtually endless. And while it may sound complicated first, adding new actions is really simple and fun.

---

