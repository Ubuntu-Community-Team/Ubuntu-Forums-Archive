---
title: "MIDI on Ubuntu - players don't play or crash"
date: 2010-02-20
forum: Multimedia Software
---

### Post by The Bright Side on 2010-02-20
Hey guys!

I have a problem playing MIDI files on my system: I tried opening two MIDI files in Audacious, VLC, Aqualung and Rhythmbox, and Rhythmbox is the only one that will play them:

- Audacious crashes when clicking on the file in the playlist (immediately disappears)
- Aqualung doesn't add them to its playlist
- VLC produces an error msg saying it can't play MIDI
- Rhythmbox plays a MIDI file and immediately crashes at its end

Would you know what's wrong? Anything missing? I'm on Ubuntu Karmic 64 and have timidity installed.

Thanks!

---

### Post by frt975 on 2010-02-20
Try my guide: [Here]("http://ubuntuforums.org/showthread.php?t=1384661")

---

### Post by The Bright Side on 2010-02-20
Unfortunately, I receive this answer:

> aptitude: unrecognized option '--with-suggests'

---

### Post by frt975 on 2010-02-20
OK, I fixed my guide. Try again

---

### Post by andrew.46 on 2010-02-20
Hi Bright,

> **The Bright Side said:**
> 
- VLC produces an error msg saying it can't play MIDI


vlc *can* play midi files perfectly well *if* it has been compiled against libfluidsynth and has access to some sound fonts. Unfortunately this is not the case with the repository vlc...

Andrew

---

### Post by clyderino on 2010-05-15
I have the same problem with Rhythmbox crashing after playing a midi file in Lucid Lynx. Any work around for this? Thanks!

---

### Post by gilbeRt_fox on 2010-06-30
> **clyderino said:**
> I have the same problem with Rhythmbox crashing after playing a midi file in Lucid Lynx. Any work around for this? Thanks!

same around here! :S

---

### Post by frt975 on 2010-07-01
Run rhythmbox from the terminal and paste what you get after the crash

---

