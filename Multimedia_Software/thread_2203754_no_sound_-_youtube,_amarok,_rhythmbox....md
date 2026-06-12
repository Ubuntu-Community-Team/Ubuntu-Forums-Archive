---
title: "no sound - youtube, amarok, rhythmbox..."
date: 2014-02-04
forum: Multimedia Software
---

### Post by P3n6uin on 2014-02-04
I replaced my audio card yesterday with the M-Audio 2496 card and only checked for sound with VLC and it worked (and also today it works) fine.
This evening I find there is no sound with youtube videos, amarok won't play nor rhythmbox same for exaile, xine, movie player and there is no sound from my Synology NAS software.

VLC is the only thing I've found so far that will play audio files.

What could be the cause of this and where do I start to find the problem?

thanks

---

### Post by P3n6uin on 2014-02-05
Well I  have a clue.
When I log in as guest instead of my user you tube works.

Seems it may be permission related?

---

### Post by P3n6uin on 2014-02-05
It seems the problem is that under my user account the sound card does not show up under the 'Ouput' section of sounds settings but it is under 'Input' while it does show up there under the guest account.

It is listed under hardware in both.

How to get it recognized by ...pulse? under my user account??
aplay -l lists the card and VLC sees it.

---

### Post by P3n6uin on 2014-02-05
Logging into the guest account again the card no longer shows up in sound settings under "Output" only under 'Input'  'Hardware'.

Enough for tonight.

---

### Post by P3n6uin on 2014-02-05
This morning I logged into the Gnome session rather than Gnome Classic and all sound was working normally.

---

