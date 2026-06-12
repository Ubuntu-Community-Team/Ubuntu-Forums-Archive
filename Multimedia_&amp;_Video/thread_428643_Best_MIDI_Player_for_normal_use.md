---
title: "Best MIDI Player for normal use?"
date: 2007-04-30
forum: Multimedia &amp; Video
---

### Post by Game_boy on 2007-04-30
Sorry if this sounds stupid, but what's the best and/or easiest way to play MIDI files on Ubuntu?

Is there a built-in application for doing so? If yes, why does it not open MIDIs I download with Firefox?

---

### Post by lluisanunez on 2007-04-30
Timidity. Or, if you're with Kubuntu, Kmid

---

### Post by ajgreeny on 2007-04-30
Go with timidity, I can not get kmid to play any midi files for some reason, though timidity does so without problem.  You may also need timidity-interfaces-extra and freepats for it to work properly, and to get a gui.

---

### Post by modemsutra on 2007-08-12
Remember to load sound font to your wavetable midi soundcard otherwise the card will be empty with no sound when you play your file, timidity uses a software synth that has samples of common instruments however this requires more CPU power the best way it's to use sound font loaded on your sound card by usin: asfxload utility.

If your sound card has a built in synth then you need to configure midi settings in Kplay to drive the sound to the rigth port.

Good Luck, enjoy

Leo

---

### Post by kbar78 on 2007-08-14
xmms has a midi plugin that's based off of timidity, if you don't feel like using a separate player for midi files

---

