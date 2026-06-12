---
title: "No Sound after install Ubuntu 9.04"
date: 2009-06-27
forum: Multimedia Software
---

### Post by Lupgaru on 2009-06-27
I just installed 9.04 on a Dell Dimension 2350. Sound worked great with XP but I've tried all the ALSA configs and several other post solutions to no avail. This desktop has a Audigy Soundblaster card installed. I get a loud noise when I select the OSS-Open Sound System and test it on my speakers (Sound Preferences) but my Speaker Icon shows Analog Center/LFE: 100%.

I don't get it, I've installed different versions of Ubuntu on at least 10 computers and have never had a sound problem.

Does anyone have any ideas?

---

### Post by ratcheer on 2009-06-27
There is a bug in 9.04. Try giving membership to your userid and root to the three pa* groups.

Tim

---

### Post by Lupgaru on 2009-06-27
> **ratcheer said:**
> There is a bug in 9.04. Try giving membership to your userid and root to the three pa* groups.

Tim
Thanks Tim
    How do I do that?

---

### Post by kostkon on 2009-06-28
Try this:

right-click on your speaker icon in the system tray and select *Open Volume Control* and then select the *Switches* tab. Make sure that the *Analog/Digital* switch is disabled.

---

### Post by goog64 on 2009-06-28
I've been looking for sound for 5 days. I don't have a "switches" tab. I noticed in two other threads that other people with no sound also have no switches tab! How can I get a switches tab?

---

### Post by Lupgaru on 2009-06-28
> **kostkon said:**
> Try this:

right-click on your speaker icon in the system tray and select *Open Volume Control* and then select the *Switches* tab. Make sure that the *Analog/Digital* switch is disabled.

:popcorn:It WORKED!!! Thank You ever so much. Now I have to set this as Solved.

Hope You have a Great Day!

---

### Post by Lupgaru on 2009-06-28
> **goog64 said:**
> I've been looking for sound for 5 days. I don't have a "switches" tab. I noticed in two other threads that other people with no sound also have no switches tab! How can I get a switches tab?

When I started I used the Sticky in Multimedia Solutions  [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)
It found my sound card and other things and got me going. I'm new at this but it might work for you.
Regards
Stephen
The Lupgaru

---

### Post by goog64 on 2009-06-28
Yeah, I 've been through that - thanks anyway.
I'd still like to know why I don't have a "Switches" tab in volume control. It seems to fix a lot of people's sound problems
I have Ubuntu 9.04 but I just downloaded Ubuntu 8.04 and ran it from Live CD. It had no sound and no switches tab either. 
Anyone?

---

### Post by kostkon on 2009-06-29
> **goog64 said:**
> Yeah, I 've been through that - thanks anyway.
I'd still like to know why I don't have a "Switches" tab in volume control. It seems to fix a lot of people's sound problems
I have Ubuntu 9.04 but I just downloaded Ubuntu 8.04 and ran it from Live CD. It had no sound and no switches tab either. 
Anyone?
This solution applies only to Audigy cards, as far as I know. 

The ALSA driver for this card offers this switch which, I think, controls a hardware switch on the card that changes the output mode of some of its ports from analog to digital and vice versa.

---

### Post by goog64 on 2009-06-29
Thanks for the info kostkon - at least I can eliminate the switch search.
Now to just hear the slightest sound would be wonderful....

---

### Post by goog64 on 2009-06-29
My solution! Yippeeee:

double click on the volume control, click on Edit/Preferences, then check External amplifier to be visible. The switches tab then appears. Uncheck External amplifier in that tab.

---

