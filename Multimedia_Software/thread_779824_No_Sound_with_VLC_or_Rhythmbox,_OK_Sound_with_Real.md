---
title: "No Sound with VLC or Rhythmbox, OK Sound with Realplayer"
date: 2008-05-03
forum: Multimedia Software
---

### Post by jackn on 2008-05-03
Until I upgraded to Heron, be it the cause or not, VLC used to work a treat for me.

Ever since the upgrade, however, VLC will go through the motions, the cursor on the play bar will move and the clock will run, but no sound can be heard...

Rhythmbox also fails to produce any sound. Its cursor and clock do not even budge, however. I have no experience with it, so I'm less sure that I'm doing things right than I am with VLC.

Realplayer and NPR's own browser-integrated player, on the other hand, play properly.

I don't know whether this has to do with the conflicting sound management systems in Linux.

Sorry, but I don't know where to look for error messages.

Leads?

---

### Post by jackn on 2008-05-04
```
sudo aptitude install vlc-plugin-pulse
``` did the job. 
VLC has now recovered sound...

---

### Post by UnWarierMage224 on 2008-05-05
I just tried this to get sound to work with downloaded FLV files, playing back in VLC. No joy. 
The command worked fine, but it didn't install anything. 

What am I missing?

-'Mage

EDIT: Now I only have MONO sound as well.... not stereo. All sound options are set to their defaults. 
help!

EDIT 2: Nevermind. Fixed.

---

