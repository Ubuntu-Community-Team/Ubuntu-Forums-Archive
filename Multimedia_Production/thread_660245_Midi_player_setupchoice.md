---
title: "Midi player setup/choice"
date: 2008-01-06
forum: Multimedia Production
---

### Post by Holonet on 2008-01-06
I have been trying to select a setup to play MIDI files with a specified soundfont file.  I managed to setup Qsynth, but I'm not sure how to make it communicate with whatever MIDI player I choose.

I have tried Timidity, but after some confusion, uninstalling and reinstalling, for some reason, I don't see any .cfg file for it anywhere.  I've even cleaned out packages and such, installed again, but whenever I read about using it, I run into the .cfg file, which is in neither of the specified directories.  I'd really like to know where I can find the default .cfg file.

I have also looked at pmidi...and there is a frontend for it here [http://www.mellowood.ca/xpmidi/index.html](http://www.mellowood.ca/xpmidi/index.html)
but I, in my relative newness to Linux, have no idea how to install this .py file.  I have python and all, and I've done the compile, make, make install routine, but how does this work?  It says to copy it to a directory, which of course I can do, but then refers to needing to "do that by hand"...which tells me jack...

Speaking of jack..jackd is another issue here...  Qsynth requires it, as does Rosegarden...but it has to be started manually everytime before those programs, and it won't do it if I happen to be playing an mp3 or something.  It doesn't seem logical to me that I have to start jackd, Qsynth, THEN a MIDI player just to play a MIDI file with my soundfont....or at least is there a way to have the necessary junk start up automatically?  I also would like to know if there's a way around the fact that with command-line programs like jackd, I have to open a terminal, then leave it open in order to keep jackd open, cluttering up my desktop with a complete mess just to play a simple MIDI file ](*,).  My confidence in the quality and efficiency of Linux tells me I'm missing something...someone please validate this :mrgreen:

Oh and P.S....anyone recommend a good notation plugin for Rosegarden?  I know Finale 2008 works in wine, but the playback...clearly does not...which is fine for notation, but crap for composition...at least with my ear.

---

### Post by warbread on 2008-01-11
First of all, you want to run qjackctl.  It's a front end for Jack and it makes things much easier.  You also want to make sure you have patchage installed.  This makes things nice and graphical.  Get Jack running, then open up Patchage and you'll see lots of inputs and outputs.  Click and drag to connect a green box to another green box and you've got a connection!  This should apply to software and hardware devices.  

It does mean that you'll have to start it up every time you want to play with MIDI, but the flexibility you get with this setup makes it worth the little bit of extra effort.  Are you using an external device or a software controller?

---

### Post by Holonet on 2008-01-20
Thanks for replying.  I would have put something back sooner, I had just given up for a spell to recoup my wits on the subject.

I am not currently using an external device.  Mind you, I've got a nice Kurzweil stage piano that I would eventually like to hook up, but for now, I'm simply trying to accomplish playback with a sf2 file at the moment, and eventually I'd like to create those sf2 files in Linux.  I never got into this like I wanted to, so I'm green to it, but essentially, I need to get a little better grasp on how all this stuff talking to each other works...and why.

I had Vienna when I was in Windows...and equivalent in Linux would be my next step.

---

