---
title: "microSD card in Sansa Fuze no longer recognized"
date: 2010-04-06
forum: Multimedia Software
---

### Post by richardq on 2010-04-06
I've had a Sansa Fuze for several months now and it has been working great on both my Karmic laptop and desktop... up until now. ;)

I have a 4GB microSD card in the Fuze as well. I use it in MSC mode. 

In the laptop, as always, when I plug it in I get two windows popping up, one for the onboard storage, and one for the microSD card. However on the desktop as of this morning, it's only bringing up the onboard, and doesn't seem to find the microSD storage. I tried my card reader on the desktop machine (using a SD adapter for the microSD card) and it read it no problem. It only seems to be a problem when I plug the Fuze itself in.

I've also tried MTP on the desktop and while that did open two Fuze devices, and did show the microSD card folders, it didn't do it correctly (the overall capacity was incorrect and just mimiced the onboard capacity and it showed no files in the folders). Like I said, I've been happily using MSC mode with this device on this desktop up until now.

I've checked that both laptop and desktop are fully upgraded, and rebooted both, but I can't figure out what the problem might be. Any ideas?

---

### Post by byStanderone on 2010-04-06
not sure about this, but do take a look at your synaptic manager, particularly at the 'not installed (residual config) portion...an update might have dump something that your fuze needs.

---

### Post by Rhubarb on 2010-04-06
I've found that sometimes (quite rarely) my mp3 players get corrupted memory.
If you've already got the music backed up somewhere else, then I advise the best thing for you to do is to tell your fuze to format the uSD card.  Then it might be ok.

Alternatively you could run gparted and see what the partition on the uSD card is like - and optionally fixit or create a new one.

You can find gparted in the repositories within synaptic.

---

### Post by lohren michael on 2010-11-16
ubuntu 9.10 can't read micro sd? tried to read it using a card reader usb or sort of but it doesn't seem to be recognize... if ubuntu 9.10 can read micro sd using a usb card reader or something, how?

---

### Post by Chronon on 2010-11-16
SD isn't a problem.  I use them all the time and have since Hardy Heron.  

I haven't used 9.10 for a while, but maybe it's just not auto-mounting the volume for some reason.  You can always do it manually.  

Does it appear in Nautilus at all?

---

