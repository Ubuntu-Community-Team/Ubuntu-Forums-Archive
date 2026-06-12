---
title: "Custom MIDI CC controller"
date: 2006-08-09
forum: Multimedia &amp; Video
---

### Post by philipacamaniac on 2006-08-09
Does anybody know of any software where I can design a custom MIDI CC (continuous control) controller?

Sonar/Cakewalk had this ability, as StudioPanels. You could create interfaces to any of your MIDI hardware. I'm in desperate need for a PODxt controller, and this is this easiest and recommended way, since the MIDI CC controls are documented.

I also would love to be able to reverse engineer those l6t tones from Line6 Edit, but that's another story.

---

### Post by dolson on 2006-08-09
> **philipacamaniac said:**
> Does anybody know of any software where I can design a custom MIDI CC (continuous control) controller?

Sonar/Cakewalk had this ability, as StudioPanels. You could create interfaces to any of your MIDI hardware. I'm in desperate need for a PODxt controller, and this is this easiest and recommended way, since the MIDI CC controls are documented.

I also would love to be able to reverse engineer those l6t tones from Line6 Edit, but that's another story.

About MIDI:
[http://www.tanzband-scream.at/line6/driverdocs.pdf](http://www.tanzband-scream.at/line6/driverdocs.pdf)

I can't recall if qmidicontrol will do what you want or not.. But maybe seach on Google for it. If it sounds good, it's in the repositories.

About the L6T file format... The reverse-engineering has mostly already been done:
[http://www.ubuntustudio.com/uploads/l6t-file-format.pdf](http://www.ubuntustudio.com/uploads/l6t-file-format.pdf)

---

### Post by philipacamaniac on 2006-08-09
I've tried qmidicontrol, but that's not exactly what I was looking for. I'm looking for something similar to JSynthLib, but that directly interfaces with MIDI ports (so no extra drivers required), sends and receives MIDI CC messages, and is fairly easy to design an interface for any particular device.

StudioWare Panels were amazing. See here at [http://www.cakewalknet.com/index.php?option=com_content&task=view&id=22&Itemid=48](http://www.cakewalknet.com/index.php?option=com_content&task=view&id=22&Itemid=48)

I've never had the chance to try the PODxt StudioWare panel; it's seems to have vanished from the web. Otherwise WINE would be my next route.

Thanks for the info on the l6t format. I wonder what still needs to be documented for the newer types of patches.

---

### Post by dolson on 2006-08-10
What is wrong with JSynthLib? It works fine for me... If you are boycotting Java, then perhaps Linux isn't for your music studio needs, since we can't be too picky at this point.

You aren't going to find anything easier than JSynthLib right now, unless you code it all yourself, and I don't consider that easier.

---

### Post by philipacamaniac on 2006-08-11
Hmm, didn't say JSynthLib was bad, it just actually seemed to be more work than starting something from scratch. So you're saying that writing a driver and patch editor for the PODxt for JSynthLib is my best bet. I'll take that as a recommendation and roll with it.

I got an email from Chris Coutlee (PODMAN), with some detailed issues about how Line 6 Edit version 3 changed the file format significantly, and that means that the possibility of that happening frequently is a real problem.

---

### Post by dolson on 2006-08-11
That's what I think.. It's a very nice system that has framework in place. You should be able to even use the POD 2.0 JSynthLib thing as a base to start from for the XT.

About the file format... I hate Line6. They use Java for their software, but they won't use the standard MIDI stuff so that it would work in Linux.. They have to use their own custom crap. Too bad.

---

