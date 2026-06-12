---
title: "audacity audio i/o layer fail."
date: 2006-01-15
forum: Multimedia &amp; Video
---

### Post by Chris Tucker on 2006-01-15
When i start audacity i get an error initializing audio. "There was an error initializing the audio i/o layer. You will not be able to play or record audio. Error: Host error."
i can edit files just fine, but its a pain because i love audacity for recording. 
the prefs window shows nothind under sound device dropdowns.
any ideas?

---

### Post by Kace on 2006-01-17
Go to "system->preferences->sound", and disable sound for events.

hope that helps.
PeaCe,
KaCe

---

### Post by amig76 on 2006-01-19
didn't work for me... :(
still searching for a solution.

---

### Post by amig76 on 2006-01-19
did it.. but I had to disable all the sounds
10x

---

### Post by pjbgravely on 2006-01-30
It didn't work for me either until I tried the Hoary trick.
[http://www.ubuntuguide.org/#configuresoundproperly](http://www.ubuntuguide.org/#configuresoundproperly)

Now disabling sound events lets Audacity use the sound card. I am assuming that the sound when you click to start the program causes Audacity to see the sound card as busy. I wonder if there is a way to put a delay in the menu so that doesn't happen. This is why it runs fine from a terminal and not the menu.

Paul Benkovitz

---

