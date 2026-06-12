---
title: "No sound from Amarok"
date: 2012-05-01
forum: Multimedia Software
---

### Post by sieve on 2012-05-01
After upgrading from 11.10 to 12.04, songs (.mp3 format) played in Amarok (2.5) have no sound.

I had this trouble in the past with upgrades, and it had to do with PulseAudio overriding all working settings. I was able to easily fix by running alsamixer through terminal, selecting my soundcard (Creative Xfi) and unmuting the relevant channels. For some reason, I can't get to alsamixer through terminal anymore (not part of 12.04?) I can still get to alsamixer GUI, but that version never worked to solve the problem and still doesn't.

Strangely, if I do a sound test in Amarok's settings, it produces valid test sounds.

The system is still correctly set up to recognize the external sound card before the internal one.

Any ideas what the conflict(s) might be that are now preventing Amarok from generating sound when playing the .mp3 files?

---

### Post by xc3RnbFO8P on 2012-05-01
Have you tried: 
Settings > Configure Amarok > Playback > Configure Phonon

---

### Post by sieve on 2012-05-02
> **Ringi said:**
> Have you tried: 
Settings > Configure Amarok > Playback > Configure Phonon

Yes, that is where I verified that the correct sound card was selected and I was able to do the speaker test.

---

### Post by copasetiq on 2012-05-02
I'm having the same issue, 12.04 + Amarok 2.5.0. Was working fine in 11.10 until the update. Phonon test in Amarok settings works, Playback does not.

Tried a couple of other players (Audacious, VLC, Totem, Kaffeine), all working.

---

### Post by sieve on 2012-05-02
> **copasetiq said:**
> Tried a couple of other players (Audacious, VLC, Totem, Kaffeine), all working.

Same here.  Rhythmbox, clementine.  Cued up and played the same files/songs that Amarok (used to) play.

---

### Post by mellis0 on 2012-05-02
Yep I'm suffering from a similar problem after upgrading from 11.10 to 12.04, no sound in Amarok.

I'm running Amarok under Unity.

All other applications like web browser, wine, audacious work fine.

I noticed that KDE phonon system sound settings keep returning to a sound card not connected to anything ie my HDMI card.

My sound card connected to my speakers and headphone is the Creative Xfi.

Doh!

I played around making my Xfi the default Alsa card which it now is, but KDE is reverting to the HDMI card.

Regards
Mark

---

### Post by copasetiq on 2012-05-07
FYI - as a workaround (don't think I'd clasify this as a "fix", but I'm also not sure we're dealing with a bug here...), I installed phonon-backend-gstreamer and set Phonon to use that in the Amarok settings - Playback was working again after that.

---

### Post by mellis0 on 2012-05-07
Hi copasetiq

:D 

Your suggested workaround of phonon-backend-gstreamer and set Phonon to use that in the Amarok settings worked for me as well

I had to restart Amarok for the phonon-backend-gstreamer to take affect.

Many thanks, not a fix but a welcome work around.

Regards
Mark

---

### Post by sieve on 2012-05-07
Worked for me also.
Thanks!

---

### Post by Yellow Pasque on 2012-05-08
So what backend was Phonon using before you set it to gstreamer?

---

### Post by sieve on 2012-05-08
> **Temüjin said:**
> So what backend was Phonon using before you set it to gstreamer?

Xine

---

### Post by sieve on 2012-05-08
Just read that Phonon also recommends removing the file ~/.xine/catalog.cache

---

### Post by Yellow Pasque on 2012-05-08
xine backend is deprecated/removed in precise, so installing gstreamer backend is actually the real fix (although it should have happened automatically)

[https://bugs.launchpad.net/ubuntu/+source/phonon-backend-xine/+bug/994654](https://bugs.launchpad.net/ubuntu/+source/phonon-backend-xine/+bug/994654)

---

### Post by mellis0 on 2012-05-08
I was using Xine as phonon back end that didn't work
I tried VLC as another phonon backend but that played corrupted sound.

Regards
Mark

---

