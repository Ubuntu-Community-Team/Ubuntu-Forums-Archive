---
title: "No sound from one runned application of 2"
date: 2009-02-09
forum: Multimedia Software
---

### Post by rado3105 on 2009-02-09
Hi, when I listen to music and also I want to see some video on youtube...There is no sound from the other application. I have ubuntu 8.04, can you help how to solve it?

---

### Post by wolfen69 on 2009-02-09
i punched in
> sound more than one application ubuntu
in google, and found many answers. google is your friend. get to know it.

---

### Post by kostkon on 2009-02-09
Firstly, follow [this guide]("http://ubuntuforums.org/showthread.php?t=789578") to better setup *PulseAudio* in your 8.04.


Afterwards, you'll need to remove *Flash 9* and install *Flash 10* (which works OK with *PulseAudio*).

Thus, go to *System &#8594; Administration &#8594; Software Sources* and make sure that in the *Third-Party Applications* tab the *Partner* repository is enabled. If not, then enable it. Press *Close*.

Then open *Synaptic* and search for the *flashplugin-nonfree* (this is *Flash 9*) package and remove it completely (i.e. select the *Complete Removal* option). Then, search for the *adobe-flashplugin* (this is *Flash 10*) and install it.

After doing the above, you should be fine.

---

