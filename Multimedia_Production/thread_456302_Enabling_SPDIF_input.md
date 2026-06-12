---
title: "Enabling S/PDIF input"
date: 2007-05-27
forum: Multimedia Production
---

### Post by corrosive_h20 on 2007-05-27
Hello,

I've gotten my Presonus Firebox to work with Ubuntu Studio after a little bit of JACK tweaking, but I'm not sure how to tell the soundcard to use the S/PDIF input. In windows, I had to tell it to use an external clock source and then it would work, but I'm not sure how to do this in Linux. I'm assuming it's a call to freebob, but any input on this would be appreciated.

Also, I get an error message when starting JACK about not being able to enable MIDI and that the MIDI patchbay will not be available. How does MIDI work in Ubuntu Studio? I've heard JACK doesn't do MIDI and that it has to run through ALSA but I'm still very new to Linux audio so any clarification would be appreciated.

Thanks for creating Ubuntu Studio. An operating system tweaked for maximum audio performance is something I have wished for for several years. You're all doing an outstanding job. ;)

---

### Post by kayosiii on 2007-05-27
Ffado (used to be freebob) is the project that creates drivers for firewire cards including for the presonus firebox (I own one too)...

My understanding is that S/PDIF support isn't in the drivers yet. It hasn't been a requested feature until recently. If you were to join the mailing list on this page [http://www.ffado.org/?q=contact](http://www.ffado.org/?q=contact) or ask a question you might be able to find out wether S/PDIF is supported yet and what the timeframe for support is if it is not.

Good luck.
         Danni

---

### Post by corrosive_h20 on 2007-05-28
What about MIDI? How does that integrate itself with JACK?

---

### Post by kayosiii on 2007-05-28
Midi works just fine
It uses Alsa. 

Be careful with the breakout cable though
Mine was quite delicate I would lie it on a flat surface. The weight of the midi cable was enough to kill the wiring in mine.
Possibly mine was a faulty unit. Anyway they gave me a circuit diagram that I requested of the breakout cable so I was able to make my own replacement. 
Which to me was a much better than sending the unit back for a replacement

---

