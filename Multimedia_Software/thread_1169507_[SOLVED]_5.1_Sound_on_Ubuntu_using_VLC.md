---
title: "[SOLVED] 5.1 Sound on Ubuntu using VLC"
date: 2009-05-25
forum: Multimedia Software
---

### Post by kdlp313 on 2009-05-25
**Here's how I got 5.1 channels of audio out of my Ubuntu Hardy** (8.04.2) **PC using VLC** (0.8.6e Janus)**.**

First off, I'm running a **SoundBlaster Audigy 2** sound card (which replaced my original card after I gave up trying to troubleshoot it).

So, after much Googling, sifting through forum after useless forum, and even more trial-and-error, I finally stumbled upon a solution that worked.  (Honestly, those forums... :roll: To all the people out there who have had this issue and received not a single response or straight answer from anyone, *I feel your pain!*)

[B]Anyway, here it is:
1.  [/B]As mentioned earlier, I installed a new sound card that was instantly recognized by Ubuntu, God bless it.  I didn't have to fuss about with drivers or packages...
**2.  **I fired up the computer and the sound system.
**3.  **Opening up VLC, I went to **_S_ettings-->****Preference_s_...** and expanded the **Audio** option on the left-hand column.  Then I highlighted **Output modules **and checked the **Advanced options** checkbox on the lower right-hand corner.
**4.  **With Advanced options activated, I was then able to see the **Audio output module** pulldown menu.  I chose **ALSA audio output** and clicked **Save**.
**5.  **I loaded up my video (in this case a DVD).
**6.  **Under _**A**_**udio-->Audio Devices**, I selected **5.1** and lo and behold, Let There Be Sound!*

*Note: When playing a commercial DVD movie, wait for the main feature to start before completing step 6.  Most standard DVD menus and trailers are only encoded in 2 channel stereo, not 5.1, thus the 6 channel (5.1) option won't yet be available.

One last thing: I can't seem to get VLC to remember these settings after I close the program, so I'm forced to go through these steps every time I load it up.  Does anyone have a fix for this?

Cheers,
-Kp

---

