---
title: "Skype Webcam Mic Support"
date: 2006-09-17
forum: Multimedia &amp; Video
---

### Post by dreyguy on 2006-09-17
I know that skype for ubuntu does not support video, but the integrated mic in the webcam is also not recognized. Do I need some better drivers or maybe I should just go out and buy a mic?

---

### Post by morgengenuss on 2006-09-17
well, i think the easiest is if you just get a mic (you can get one for $7 or so)...

but regarding the webcam: does it work with other applications in linux (incl mic)? (e.g. can you record your voice in audacity with your webcam-mic?)

---

### Post by motin on 2006-09-20
Take a look at [http://195.38.3.142:6502/skype/](http://195.38.3.142:6502/skype/)

I do not know for how long the link will be available, but most what's in it is quoted here - and the latest file is attached to this post:

> Skype DSP hijacker + patch for separate devices
Counting 7094 unique downloads so far.

This is the original skype_dsp_hijacker, from [http://suedpol.dyndns.org/skype/](http://suedpol.dyndns.org/skype/), patched to make Skype use separate devices for sound input and output. Originally the patch was written to make Skype useable with a separate USB webcam microphone.

Known problems:

Under AMD64, there has been problems with getting the library to work. Compiling with -m32 seems to fix it. Credits to Dominique Schaefer for first mentioning the problem, and providing a fix.

Suggestions and further patches are welcome - send them to: [email]skype@oscs.se[/email]. Please include the word 'skype' in the subject.

Usage example (Using 2nd sound card microphone & 1st sound card speakers):

skype_dsp_hijacker --mic2nd

Changelog

Latest version: (No patching needed):

2006-03-12 - Version 0.7
Download version 0.7

Romano Giannetti <romano at dea dot icai dot upcomillas dot es>
* If the speaker is not opened for, for example, EBUSY, skype need to know
   it, otherwise it will blindly try to write to it and spewing write failed
   error. That way, if for example there is a realplay running and taking
   over /dev/dsp, Skype will say "problem with sound device".

Jan Slupski <jslupski at juljas dot net>
* Set permissions when installing library & script
* Changed debug printing from stdout to stderr. Otherwise opening URLs from
   chat (and other web pages from menu) does not work.
* Add AMD64 compilation README (thanks to Danyel Ceccaldi, )
* output some (compile time) configuration options on runtime


Hope it helps!

---

