---
title: "[SOLVED] Rhythmbox pauses between tracks"
date: 2008-08-01
forum: Multimedia Software
---

### Post by Epistaxis on 2008-08-01
In Rhythmbox, whenever I'm playing a queue of audio files in which each one is supposed to run immediately into the next without a pause (this is very common with tracks on classical music CDs), there's a slight hesitation at the end of the track; presumably Rhythmbox waits until the first file is done playing before it opens the second file. Is there a way to configure it so there isn't any pause? Winamp doesn't seem to have this problem on my computer; perhaps it preloads the second file before the first finishes. If not, is there another GNOME media player that does this, but still has a "media library" system?

---

### Post by kostkon on 2008-08-01
> **Epistaxis said:**
> In Rhythmbox, whenever I'm playing a queue of audio files in which each one is supposed to run immediately into the next without a pause (this is very common with tracks on classical music CDs), there's a slight hesitation at the end of the track; presumably Rhythmbox waits until the first file is done playing before it opens the second file. Is there a way to configure it so there isn't any pause? Winamp doesn't seem to have this problem on my computer; perhaps it preloads the second file before the first finishes. If not, is there another GNOME media player that does this, but still has a "media library" system?
You mean gapless playback. I think you can do it by going to *Preferences -> Playback*, enabling the *Use Crossfading Backend* option and setting the length to zero.

---

### Post by Epistaxis on 2008-08-02
> **kostkon said:**
> You mean gapless playback. I think you can do it by going to *Preferences -> Playback*, enabling the *Use Crossfading Backend* option and setting the length to zero.

Thanks, that's exactly what I was looking for, and it works perfectly.

---

### Post by kostkon on 2008-08-02
> **Epistaxis said:**
> Thanks, that's exactly what I was looking for, and it works perfectly.
:):):):):):)

---

