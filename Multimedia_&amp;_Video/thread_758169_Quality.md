---
title: "Quality"
date: 2008-04-17
forum: Multimedia &amp; Video
---

### Post by Dumbestcrayon on 2008-04-17
Ok my main question..
Why is the sound quality not as good as opposed to windows? Im hoping its just some settings or something.

And 

When I open alsamixer I have to turn up the front volume, which is fine, but I have to do it every time I restart. My volume buttons control the master volume. Is there a way to save my settings in alsamixer so that it boots up at those settings?

---

### Post by Whiffle on 2008-04-17
On mine if I turn the PCM value up to 100% it distorts the sound, I keep it at 77.  

you can do:
alsactl store 

To store settings, but I thought ubuntu did this automatically..hmm.

---

### Post by Dumbestcrayon on 2008-04-17
Hey thanks man.
My sound isnt as loud as windows either, even when the levels are all the way up. But that worked to save the settings.

---

### Post by Whiffle on 2008-04-17
What kind of sound card?  Some aren't as well supported as others.  Mine sounds great (turtle beach santa cruz), but it looses alot of functionality in linux like surround sound and use of the versajack.  They won't release the specs for the audio chip on it so the only drivers are pretty much entirely reverse engineered.  I can't complain too much, I only paid $12 for it.

---

