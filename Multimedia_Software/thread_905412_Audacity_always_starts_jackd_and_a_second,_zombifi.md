---
title: "Audacity always starts jackd and a second, zombified instance."
date: 2008-08-30
forum: Multimedia Software
---

### Post by scotty64 on 2008-08-30
I cannot get Audacity to work properly on Hardy. The oddest thing is that it ALWAYS starts jackd and initiates a second, zombified instance of Audacity. Nothing (recording / playback) works until I kill this jackd manually. It does not matter if I configure Audacity to use ALSA or OSS, I even deleted the .audacity* directories from my home - it is always starting jackd and the Zombie process.
My question is: where does audacity start jackd and how can I disable that (without uninstalling jackd, because I need it)?
I have reverted to Audacity 1.2.6 for now...

---

### Post by TheMusicGuy on 2008-10-17
I've been having this exact same problem. Apparently it arises from JACK swiping access to the sound system for itself before Audacity gets a chance, resulting in Audacity scratching its head trying to figure out what to do.

As you said, removing Jackd is not really an option since so many things need it. I suggest telling Audacity to use JACK for both input and output via the preferences menu. If that does not work at first (i.e. Audacity says it can't connect or sound output is really bad) you may need to fool around with JACK options using qjackctl. Use ```
sudo apt-get install qjackctl
``` to install that if you don't have it already. Start it with ```
qjackctl
``` on the command line. It should not require root privelages.

I wanted to point you to the tutorial that helped me solve this problem but I can't find it...what I have above is from memory. It's very possible that I've forgotten something, but try it anyway.

---

### Post by markbuntu on 2008-10-17
Or you can just use ardour which is fully integrated into jack. It was written by the same people.

---

