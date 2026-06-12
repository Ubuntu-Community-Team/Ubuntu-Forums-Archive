---
title: "Weird Sound Issue"
date: 2008-11-17
forum: Multimedia Software
---

### Post by 3rdear on 2008-11-17
I was following some of the other threads trying to get sound support under wine and in so doing messed up my sound.

The boot up & shut down sounds are dead and KDE games don't seem to have any sound. Testing for sound under the system settings yields nothing.

Some apps and games like Skype, Opena Arena, Chromium, Kaffiene, Amarok, Hydrogen, JACK seem to be fine, but games in DOSBox and again the standard KDE games are silent as are all my games in XMame, lbreakout, etc.

Anyone have a clue to help out a fairly savvy, but relatively lost Kubuntu user here? I tried purging the alsa-base stuff and reinstalling. No use.

Can't believe I have to deal with this now -- all because I just wanted to hear some freekin sound while playing TIE fighter. :-(

FWIW, I'm using an M-Audio Delta 1010 LT and EVERYTHING was fine until I started following instructions on getting sound in wine. I'm running Kubuntu Hardy.

Finally, I can't seem to locate envy24control in the Adept Package manager. I already have it installed, but if I'm somehow missing a repository or if it's part of some other package, I'd like to be able to locate and update it, if necessary.


Thanks!

---

### Post by 3rdear on 2008-11-18
> **3rdear said:**
> 
Finally, I can't seem to locate envy24control in the Adept Package manager. I already have it installed, but if I'm somehow missing a repository or if it's part of some other package, I'd like to be able to locate and update it, if necessary.
Thanks!

Okay, I managed to find envy24control in the alsa-tools-gui package. So that part is solved. If anyone has any suggestions to address the main problem in my original post, that would be great.

Meantime, I'll see what else I can find here on getting this fixed.

---

### Post by 3rdear on 2008-11-19
Thanks to the 10,000 page reference a simple removal of a single line in my asoundrc file fixed the problem.

---

### Post by mrvvill on 2008-12-23
I have this problem now! I was wondering if you are able to give me a solution for this!

---

