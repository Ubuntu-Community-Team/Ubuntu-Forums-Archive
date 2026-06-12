---
title: "convert ogg to mp3"
date: 2010-05-16
forum: Multimedia Software
---

### Post by abecrab on 2010-05-16
There is an oldish thread for building sox to include mp3:

[http://ubuntuforums.org/showthread.php?t=17272](http://ubuntuforums.org/showthread.php?t=17272)

I want to convert ogg to mp3.

I folowed the steps carefully.

In the rules file I remove:

--without-lame 
from
DEB_CONFIGURE_EXTRA_FLAGS
leaving
--with-distro="Debian GNU/Linux" --with-dyn-default --without-amrwb --without-amrnb

I always get something like:

FAIL formats: can't open output file `/tmp/t.mp3': SoX was compiled without MP3 encoding support

mp3 not working.

Anyone know how to do this, or know of a different way of converting ogg to mp3?

Thanks a bundle

---

### Post by cascade9 on 2010-05-16
Easier to convert using soundconverter (gtk, gnome etc) or soundkonverter (qt, KDE)

---

### Post by abecrab on 2010-05-18
That works a treat - thanks a bundle.
I also found I could ogg123 them to wav, then reencode with lame; I used a shell script.
But soundconverter looks much niftier.
Thanks again,
Abe

---

### Post by cascade9 on 2010-05-19
They are both great little programs, I use them to convert .flac to .mp3 for my media player. Which will actually play .flac, but there isnt quite enough space to fit the amount of music I want on there. 

Glad it helped ;)

---

