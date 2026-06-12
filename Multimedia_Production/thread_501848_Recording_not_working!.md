---
title: "Recording not working!"
date: 2007-07-15
forum: Multimedia Production
---

### Post by DJ Wings on 2007-07-15
Any time I try to record sound with any of 5 programs (Ardour, Audacity, Rezound, GNUSound, GNOME Sound Recorder), they invariably crash. I'm running Xubuntu 7.04 on an uncustomized (read: entry-level) Dell E1505N.

---

### Post by fredj on 2007-07-15
Have you setup, configured and started the jack audio server program correctly before you run any of these
other programs?

---

### Post by DJ Wings on 2007-07-16
My weapon of choice is Audacity, which doesn't support Jack (at least the copy that comes with Ubuntu Studio). Maybe Ubustu has something to do with it; I've heard that it caused issues with recoring for other people.

---

### Post by DJ Wings on 2007-07-16
I used jacklaunch to run Audacity (crashed immediately) and gnome-sound-recorder (which crashed where it did before). Ardour refuses to record at all. All this with jackd running.

---

### Post by dabl on 2007-07-16
Prolly ALSA and/or OSS aren't quite right -- I'd make sure those are fully functional before suspecting the app, especially since it seems to affect all apps that you've tried. :)

---

### Post by DJ Wings on 2007-07-16
And how would I do that? ALSAconfig?

---

### Post by dabl on 2007-07-16
Yep.

```
sudo alsa-conf
``` should get you where you need to be. :)

---

### Post by DJ Wings on 2007-07-16
Don't have it, and it command-not-found doesn't recognize it.

---

### Post by skipkent on 2007-07-16
This brings up a good general Linux troubleshooting question:

Where can we find log output for these sorts of errors if the apps in question are not kicked off at the console (but rather from a menu or desktop icon)?  /var/log/messages doesn't seem to ever have what I'm looking for.

In any case, try kicking off Audacity or whatever from the command line and see if you get some output there after the crash that we can pick through.

---

