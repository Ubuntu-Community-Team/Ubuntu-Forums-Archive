---
title: "[SOLVED] Conflict Between Embedded Flash and Local Music Files?"
date: 2008-05-11
forum: Multimedia Software
---

### Post by Bridger987 on 2008-05-11
Quick question...  I have had a problem (just since I updated to Hardy/8.04) that involves embedded flash files in Firefox not playing at all if a music player (namely Rhythmbox, Songbird, Amarok, VLC, and the built-in "Movie Player") is playing music.  Also, if I am viewing something in Firefox that involves a flash video with sound (Youtube, for example), and I attempt to hit 'Play' in Rhythmbox, it will not do anything.  The song will stay at "0:00", and nothing will sound.

Is there something conflicting with a sound server (ALSA, etc... I'm not sure what I'm using to tell you the truth), or is there some more complicated problem?

Thanks.  :)

 
Edit :

**[COLOR="Red"]SOLVED with help from people on the IRC chat.[/COLOR]**

1.)  System > Preferences > Sound
2.)  Change everything to ALSA.

Simple as that.  (For me, anyhow.)

---

### Post by evolutionx on 2008-05-12
> **Bridger987 said:**
> Quick question...  I have had a problem (just since I updated to Hardy/8.04) that involves embedded flash files in Firefox not playing at all if a music player (namely Rhythmbox, Songbird, Amarok, VLC, and the built-in "Movie Player") is playing music.  Also, if I am viewing something in Firefox that involves a flash video with sound (Youtube, for example), and I attempt to hit 'Play' in Rhythmbox, it will not do anything.  The song will stay at "0:00", and nothing will sound.

Is there something conflicting with a sound server (ALSA, etc... I'm not sure what I'm using to tell you the truth), or is there some more complicated problem?

Thanks.  :)

 
Edit :

**[COLOR="Red"]SOLVED with help from people on the IRC chat.[/COLOR]**

1.)  System > Preferences > Sound
2.)  Change everything to ALSA.

Simple as that.  (For me, anyhow.)


I had the exact same issues since reinstalling to the new Ubuntu version.  It appears something was causing the sound card to come back with device busy errors.

This issue should be collated into a stick post somewhere I reckon.

---

### Post by trigsenior on 2008-06-16
i know it an old post but this worked for me in hardy =) 
thanxs

---

