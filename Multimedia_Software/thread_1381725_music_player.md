---
title: "music player"
date: 2010-01-15
forum: Multimedia Software
---

### Post by Virtueofselfishness on 2010-01-15
i recently downloaded a cd 
when i tried playing it on rhythmbox it wont play but it does play on movie player lol
but some of my other music doesant play on movie player but it does on rhythmbox

i was wondering what does the community recomend me 
i want something flexible like winamp

thank you :)

---

### Post by fancypiper on 2010-01-15
Audacity2 is similar to winamp.

Exaile is a nice music player IMHO

---

### Post by Virtueofselfishness on 2010-01-15
i forgot to add something

i want it to be ipod compatible

---

### Post by kahlil88 on 2010-01-15
Your out-of-the-box system will only handle free/libre formats like Ogg Vorbis, but it's possible to get non-free formats like MP3 and AAC to play by installing the right GStreamer decoders. I also recommend Exaile, which does support iPods (probably not the Touch or Shuffle).

---

### Post by fancypiper on 2010-01-15
Would exaile with exaile-plugin-ipod do the job for you?

sudo apt-get install exaile exaile-plugin-ipod

---

### Post by ajgreeny on 2010-01-15
What is the file type of the downloaded CD?  If it plays in totem (Movie player) it should also play in rhythmbox, I think.

This sounds like a codecs problem of some sort, or perhaps you need to make sure you have all the gstreamer bad and ugly packages installed for rhythmbox and movie layer to do their jobs properly.

---

### Post by fancypiper on 2010-01-15
[Comprehensive Multimedia & Video Howto](http://ubuntuforums.org/showthread.php?t=766683)

---

### Post by Virtueofselfishness on 2010-01-15
by the looks of it im going with Exaile


will the touch be compatible with Exaile anytime soon?

---

### Post by houseworkshy on 2010-01-15
If you go to System>Administration>Synaptic Package Manager, put in your password when prompted, then click settings then repositories and make sure all but the source code boxes are ticked on the first tab,on the second tab (3rd party software) make sure that all the boxes are checked, then close that and click reload , as prompted if you had to change anything, then use the search and look for ubuntu restricted-extras then check the box next to it, then click apply you will install the non free codecs mentioned above.  There will be prompts and agreements during the process for some.  Non free does not mean you have to pay for them, simply that the source code is not feely available so can only be maintained by the providers.

---

