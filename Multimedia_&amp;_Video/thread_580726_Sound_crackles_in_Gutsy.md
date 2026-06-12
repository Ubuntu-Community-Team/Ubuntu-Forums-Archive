---
title: "Sound crackles in Gutsy"
date: 2007-10-19
forum: Multimedia &amp; Video
---

### Post by Explodinglemur on 2007-10-19
Upgraded to Gutsy on my Asus A8Jm laptop and decided to install a few games (ManiaDrive, TuxCart for a few examples).  I found that sound within the games crackles quite a bit.  I also found that now when I adjust my volume, the speakers pop while dragging the volume slider or hitting the laptop's volume up/down keys.  However, listening to music through Totem or Rhythmbox is fine, no crackling problems.  Tried toggling esd in Gnome, that had no effect on the crackling in the games or the popping during volume level changes.

lspci says my audio controller is:
```
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
```

/proc/interrupts shows the audio device on its very own interrupt, so no interrupt sharing issues there.

No errors in dmesg output.

Any other config file contents that might help or other steps to try?

---

### Post by Explodinglemur on 2007-10-19
Huh.  My bad, this is not Gutsy-specific.  I tried a few games on my desktop machine, which is still running Feisty, and ran into the same issues.  Sound within the game crackles, and after leaving, I get the speaker-popping when adjusting volume levels.  After playing an audio or video file with Totem, the speaker popping problem goes away.  Could it be some kind of ALSA/OSS compatibility problem?  I tried installing the alsa-oss wrapper package and ran the game again, but still had the same problem...

---

### Post by Explodinglemur on 2007-10-20
Solved with the second option in this post: [http://ubuntuforums.org/showpost.php?p=3152472&postcount=8](http://ubuntuforums.org/showpost.php?p=3152472&postcount=8)

---

### Post by Explodinglemur on 2007-10-20
Hm, or not.  Tried these options in /etc/openalrc:
```
(define devices '(esd))
(define alsa-out-device "default")
```

```
(define alsa-device "default")
(define devices '(alsa native))
```

```
(define devices '(alsa native))
```

What are the appropriate settings to use in my openalrc config?

---

### Post by Explodinglemur on 2007-10-20
If I use esd or oss in my openalrc config file, audio starts out sounding good, but will break up frequently with periods of horribly distorted sound.

Using alsa, the sound is crackly and choppy all the time.

Playing audio via totem, rhythmbox, and amarok sounds fine.

Sound within Nexuiz sounds fine, it uses SDL and not OpenAL.  Problem appears to be OpenAL specific.

---

### Post by sstusick on 2007-10-20
I, too experience that crackly sound. The Linux drivers pale in comparison to the Windows one's :( The sound is excellent in Winblows. Wonder if there is a way to use the Windows drivers in Linux?

---

### Post by linuxlizard on 2007-10-21
I just used gedit to make .openalrc with the following line
 (define devices '(native))
saved it in my home directory as .openalrc and it works great. No more crackles!

---

