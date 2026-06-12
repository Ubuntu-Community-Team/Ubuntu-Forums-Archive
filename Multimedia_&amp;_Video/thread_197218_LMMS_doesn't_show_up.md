---
title: "LMMS doesn't show up?"
date: 2006-06-15
forum: Multimedia &amp; Video
---

### Post by Arathorn on 2006-06-15
Hi, I've just installed LMMS with Adept on Kubuntu Dapper 64, but it doesn't show up anywhere in the start menu (or whatever that's called in KDE), or in the Studio Launcher tool. Adapt says everything was installed, and I even reinstalled both LMMS and the Studio Launcher. What's going wrong here?

---

### Post by zettberlin on 2006-06-15
Maybe it is because lmms is no jackd-aware programm yet. That is, it cannot connect to the other progs of ubuntustudio. 

To start lmms try this:

open a console-window (from Konqueror - extras- konsole)
type:

#lmms

---

### Post by Arathorn on 2006-06-15
Nothing seems to happen ater entering #lmms in Konsole.

---

### Post by dolson on 2006-06-15
Ubuntu Studio Launcher does not list applications that do not have proper .desktop files in their packages, installed to /usr/share/applications.

Create a launcher and put it there and it will show up both in your menu and in USL.

---

### Post by slugkilla on 2006-06-16
Not to insult your intelligence, (I have no clue what your skill level is in linux) but don't type "#lmms" in the command line. When the command line window comes up, type 
lmms 
just like that. If you need too, type 
sudo lmms
and then your password. I hope this helps.

---

### Post by dolson on 2006-06-17
There is no need to run an app like LMMS as root...

---

### Post by Arathorn on 2006-06-18
I have very little Linux experience, but I'm learning. ;)
I have added Lmms to the start menu, thank you for your help.

---

### Post by Arathorn on 2006-06-19
I have another LMMS question. I just downloaded the Titanic soundfont, but how do I use it with LMMS? There appears to be no documentation at all about LMMS available (I guess the app is pretty new) and my lack of experience with both Linux and digital music making isn't helping.

---

### Post by dolson on 2006-06-19
We are all trying to figure out various software. :)

Documentation is very bad for Linux apps (usually).

Sorry I can't help, but I share your sentiments. Ardour has old and spotty documentation.

---

### Post by Arathorn on 2006-06-20
The joy of open source software is the community forum that usually comes with them. Unfortunately LMMS only has a mailing list, which is hard to search. Guess I'll have to mess around on my own. ;)

---

### Post by kellogs on 2006-06-24
[QUOTE=Arathorn]I have another LMMS question. I just downloaded the Titanic soundfont, but how do I use it with LMMS? There appears to be no documentation at all about LMMS available (I guess the app is pretty new) and my lack of experience with both Linux and digital music making isn't helping.[/QUOTE]

Hi, I dont think Lmms supports plugins like Qsynth... (a wrapper for fluidsynth were you can load SF2 files).

ATM Lmms is very very beta and only does support some audio importing, a tiny little synth and some drum/percussion step sequencer.

I come from windows, there I used to use FL Studio. The nearest thing I found in dapper is Rosegarden4, where you can connect almost every synth available in linux throught Jack. For example you can connect Zynnadsubfx or Qsynth or any midi equiptment you have, It does work very well and pretty stable here.

For soundfonts right now Im experimenting with Qsynth... but it seems it works even better than soundfont player in Fl studio... It looks like you have multitimbral capabilities...(1-16 soundfont programs per track).

check rosegarden you wont regret, and dont forget Hydrogen, very similar to fruity FPC drum machine.

cheers.

---

### Post by Arathorn on 2006-06-25
I've tried Rosegarden, but it crashes after a little while, before I've been able to experiment with it's functions. I will try Hydrogen and see what it can do.

---

### Post by kellogs on 2006-06-25
im afraid you will need to configure your dapper for realtime and for Jack. Did you follow the instructions in the ubuntu studio wiki? I did it with a fresh dapper install and all was ok. 

Configure JACK and when you have it working with 0 xruns and the lowest lag you can  get you will be ready for rosegarden, muse, jack, etc. There is a description of Jack settings in the wiki.

---

### Post by Arathorn on 2006-06-25
I haven't messed with the XRuns yet because I'm new at making music and wanted to focus on the programs first. Could it be that the XRuns make Rosegarden crash?

---

