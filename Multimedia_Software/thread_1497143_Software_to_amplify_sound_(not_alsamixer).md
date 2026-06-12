---
title: "Software to amplify sound (not alsamixer)?"
date: 2010-05-30
forum: Multimedia Software
---

### Post by sundol on 2010-05-30
At Ubuntu 10.04, I amplified sound maximally using alsamixer and volume icon on the menu bar but I want to amplify further.

VLC can amplify sound upto 400% but only inside VLC.

Are there any such program to amplify sound in general at Ubuntu 10.04?

---

### Post by nothingspecial on 2010-05-30
I`m supprised you have the [[COLOR="Magenta"]audacity[/COLOR]]("http://audacity.sourceforge.net/") to ask ;)

---

### Post by sundol on 2010-05-30
Thank you for reply. 

My question maybe was not good enough. 
I want to amplify the sound of a network streaming.
I looked up audacity but it looks like a software only for an offline audio file.

Are audacity able to amplify a network streaming? or any other suggestion?

---

### Post by cchhrriiss121212 on 2010-05-30
[Jackd]("http://jackaudio.org/") can stream audio [over a network]("http://netjack.sourceforge.net/") but I have not attempted to set this up myself. It will give you complete control of where the audio stream goes, so you could start jackd and then use a simple lapsda amplification plugin, or just run the sounds through vlc and out to an external source.

---

### Post by benerivo on 2010-05-30
Have you tried raising the preamp in vlc's own graphic equalizer?

---

