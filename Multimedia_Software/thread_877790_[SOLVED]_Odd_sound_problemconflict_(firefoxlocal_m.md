---
title: "[SOLVED] Odd sound problem/conflict (firefox/local movies)"
date: 2008-08-02
forum: Multimedia Software
---

### Post by Midnightsun on 2008-08-02
Hi Guys,

Have recently developed a fairly odd problem with my sound in Ubuntu.  If I spend some time viewing flash videos on the web (firefox 3) and then attempt to play a movie from my HDD the local video will have no sound.  Web videos will continue to play as normal.

Alternatively, if I have spent some time watching movies on my local HDD and then attempt to watch something on the web, the opposite occurs.  Local movies play fine, web ones without sound.

The only way I have been able to restore sound is to log out/login.  This will temporarily restore sound to both types of media, however after a while of watching either one of the other, the same problem will occur.

Any advice will be greatly appreciated.

---

### Post by kostkon on 2008-08-02
Go to *Synaptic* (*System -> Adminstration -> Synaptic*), search for the *libflashsupport* package and install it. After that, your problems should be over.

[COLOR="Red"]For the record: my 1000th post, yayyy!![/COLOR]

---

### Post by mathtick on 2008-08-02
This seems to have fixed my problem, at least I haven't managed to reproduce it so far.  

I thought I should also note that, on my system, viewing videos on youtube in firefox seemed to kill all other sound (vlc - no sound, rhythmbox - no sound, amarok - no sound + crash, songbird - no sound).  Previously I could fix it by quitting firefox and the other sound application and then reopening.

---

### Post by kostkon on 2008-08-02
> **mathtick said:**
> This seems to have fixed my problem, at least I haven't managed to reproduce it so far.  

I thought I should also note that, on my system, viewing videos on youtube in firefox seemed to kill all other sound (vlc - no sound, rhythmbox - no sound, amarok - no sound + crash, songbird - no sound).  Previously I could fix it by quitting firefox and the other sound application and then reopening.
Yes, this was happening because *Flash* was locking the sound card and it did not allow other applications to use the sound.

*libflashsupport* makes *Flash* to send its sound to *PulseAudio* and not directly to *Alsa*.

---

### Post by shufflemoomin on 2008-08-02
Thanks for posting this guys. I had this exact problem and couldn't understand what was going on and what was the culprit. Thanks for clearing this up for me too.

---

### Post by Midnightsun on 2008-08-06
Thanks mate!  That sorted it out.

Unfortunately, that created a new set of problems (the notorious flash crashing firefox bug) but I seem to have worked around that with "killall pulseaudio"

Cheers!

---

