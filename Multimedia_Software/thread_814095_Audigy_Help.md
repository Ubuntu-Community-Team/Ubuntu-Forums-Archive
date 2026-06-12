---
title: "Audigy Help"
date: 2008-05-31
forum: Multimedia Software
---

### Post by White_Panther on 2008-05-31
Hello I am trying to use skype on my desktop which has a audiogy card.  I am trying to use the front jacks for headphones and mic, but have had no luck.  the front connectors are not part of the audiogy sound car, but instead part of the on board car.  The PC is Dell dimension E520.  I had the same problem on my laptop but after compiling alsa the problem was solved.  That did not work on the desktop.  I am willing to remove and uninstall the Audiogy card, but don't know how to either.

lspci:
```
03:02.0 Multimedia audio controller: Creative Labs SB Audigy (rev 04)
03:02.1 Input device controller: Creative Labs SB Audigy Game Port (rev 04)
03:02.2 FireWire (IEEE 1394): Creative Labs SB Audigy FireWire Port (rev 04)

```

---

### Post by White_Panther on 2008-05-31
bump

---

### Post by cariboo on 2008-05-31
There is usually a cable from the front jacks to a connector on the motherboard. Not sure about Dell, but if there is, there should be a connector on your sound card that you can plug this cable into.

Jim

---

### Post by AliTabuger7 on 2008-06-02
I don't think it's him forgetting to connect it. I have an Audigy 2 (silver?) and I don't think I ever actually got the front panel to work. It works fine in WinXP.

There are a couple of things i discovered though. A bunch of the stuff that I actually might have wanted to use were muted. 
To check this, right click on your volume control button in the gnome panel and click "open volume control".
From there, click on edit > preferences.
There is a bunch of stuff that is unchecked. I'm not sure which one you're looking for but Aux, Aux2, and Aux2 Capture are some good guesses.
You will notice that you have more controls on the main window. Make sure that the recording or playback that you are looking for is not muted.

---

