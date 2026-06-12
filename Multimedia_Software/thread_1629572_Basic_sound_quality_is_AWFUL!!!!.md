---
title: "Basic sound quality is AWFUL!!!!"
date: 2010-11-23
forum: Multimedia Software
---

### Post by RoyT on 2010-11-23
I have used several versions of ubuntu starting with 8.whatever now I am using 10.4 and this problem has not improved. The sound is full of static like sounds which are very loud and vary as I vary the volume control. I can only get somewhat clear sound by sliding the volume control until I find a spot where the static disappears. All sound is corrupted whether played via Rhythmbox or from a web site. It is impossible to set a low volume that is clear.

I am using an old DELL 8200 Dimension with a Sound Fusion card:

[511]$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: CS46xx [Sound Fusion CS46xx], device 0: CS46xx [CS46xx]
...

It certainly seems like there should be an easy solution for this problem!

Thanks for any help.

---

### Post by oboedad55 on 2010-11-23
> **RoyT said:**
> I have used several versions of ubuntu starting with 8.whatever now I am using 10.4 and this problem has not improved. The sound is full of static like sounds which are very loud and vary as I vary the volume control. I can only get somewhat clear sound by sliding the volume control until I find a spot where the static disappears. All sound is corrupted whether played via Rhythmbox or from a web site. It is impossible to set a low volume that is clear.

I am using an old DELL 8200 Dimension with a Sound Fusion card:

[511]$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: CS46xx [Sound Fusion CS46xx], device 0: CS46xx [CS46xx]
...

It certainly seems like there should be an easy solution for this problem!

Thanks for any help.

Did you search the forums? I'm pretty sure I've seen this discussed here.

---

### Post by RoyT on 2010-11-24
Yes, I did a search but did not turn up anything relevant. Posts have to do with specific problems. Mine affects all audio out regardless of source or app.

---

### Post by oboedad55 on 2010-11-24
> **RoyT said:**
> Yes, I did a search but did not turn up anything relevant. Posts have to do with specific problems. Mine affects all audio out regardless of source or app.

Bummer. I found this Googing your problem; [https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/622548](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/622548)

---

### Post by RoyT on 2010-11-26
Thanks. I will look at that. I also found that I could use alsamixer and alsactl to reduce the master volume and the buzzing disappeared. This does reduce the volume somewhat, but at least I can get listenable sound.

---

