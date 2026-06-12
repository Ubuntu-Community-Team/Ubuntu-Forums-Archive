---
title: "Flash audio skipping"
date: 2008-03-06
forum: Multimedia &amp; Video
---

### Post by LadyGodiva on 2008-03-06
I am running Gutsy and I don't have a problem with audio (using MPlayer). My problem is that YouTube sound in FireFox is ALWAYS skipping. It keeps skipping until I close FF. I downloaded flash plugin and I desperately need help for this problem.

Please help! I posted 3 threads about my various audio problems and nobody replied. I am getting really frustrated. :confused:

---

### Post by gandaran on 2008-03-06
> **LadyGodiva said:**
> I am running Gutsy and I don't have a problem with audio (using MPlayer). My problem is that YouTube sound in FireFox is ALWAYS skipping. It keeps skipping until I close FF. I downloaded flash plugin and I desperately need help for this problem.

Please help! I posted 3 threads about my various audio problems and nobody replied. I am getting really frustrated. :confused:

there are many post's with the same problem as yours, if you do a search you will find this a very difficult issue to fix.
two questions, exactly what flash did you install and where is it installed? (which folder), your ubuntu is 32-bit or 64-bit?
I suggest you try another browser, opera or seamonkey, this only to rule out any firefox problem.
if the problem continues even with other browsers (maybe a hardware problem), you could try install libflashsupport and also pulseaudio, some people did solve this by installing one of these.

---

### Post by LadyGodiva on 2008-03-06
My Ubuntu is  i686 so I think that means it's 32-bit. (got this after running uname -a in terminal.)

The flash plugin I have installed is in Home >>.mozilla >> Plugins and it is 'libflashplayer'. 

I installed Pulse Audio complete with all its components, no progress. 

I think I should note that sometimes playing a YouTube video makes sound completely disappear and if I try to run MPlayer after that I get the error 'Could not open/initialize audio device - no sound' and sound is gone until I restart.

Thank you for replying by the way :D

---

### Post by gandaran on 2008-03-06
I think you must set up pulseaudio as your system sound.
try the opera browser, download the 9.50b ([http://www.opera.com/download/?ver=9.50b](http://www.opera.com/download/?ver=9.50b)).
for opera flash just copy the home .mozilla plugins folder and paste on home .opera folder.

---

