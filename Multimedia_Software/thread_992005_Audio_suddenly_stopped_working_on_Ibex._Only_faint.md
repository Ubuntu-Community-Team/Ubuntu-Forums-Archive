---
title: "Audio suddenly stopped working on Ibex. Only faint static now."
date: 2008-11-24
forum: Multimedia Software
---

### Post by ggtsu on 2008-11-24
Yesterday I noticed that audio was no longer playing on my Ibex system. Now all I get is some faint static. I know it's not a hardware issue because sound still works fine when I boot into Vista. I have not made any major changes to my setup. One thing though. Yesterday I had my system shutdown improperly (for what reason, I can't remember) and while shutting down the console seemed to hang on some line which said something about ALSA. Since I wasn't really paying attention at the time, I didn't think anything of it. Now that my audio stopped working, I realized that ALSA has something to do with audio.

So far I have followed the instructions on another [thread]("http://ubuntuforums.org/showthread.php?t=205449&highlight=static+sound") on reinstalling the audio/ALSA components in Ubuntu, but that didn't work. If I go to Preferences->Sound in gnome and switch the playback to OSS, the test sound works. When it's set to ALSA or Autodetect all I get is the static on the test sounds. However, even with OSS selected for playback, I only get static when trying to play any sounds outside of that sound settings page. I really haven't changes anything. My sound's just broke.

---

### Post by psyke83 on 2008-11-24
See: [http://ubuntuforums.org/showpost.php?p=6197637&postcount=3](http://ubuntuforums.org/showpost.php?p=6197637&postcount=3)

Note: you must explicitly define your hardware soundcard when invoking alsamixer:
```
$ alsamixer -Dhw
```

---

### Post by ggtsu on 2008-11-24
Not really sure what that did there, but it seems to have worked.

> **psyke83 said:**
> See: [http://ubuntuforums.org/showpost.php?p=6197637&postcount=3](http://ubuntuforums.org/showpost.php?p=6197637&postcount=3)

Note: you must explicitly define your hardware soundcard when invoking alsamixer:
```
$ alsamixer -Dhw
```

---

### Post by all2ez on 2008-12-06
> **psyke83 said:**
> See: [http://ubuntuforums.org/showpost.php?p=6197637&postcount=3](http://ubuntuforums.org/showpost.php?p=6197637&postcount=3)

Thanks for the link.  I had the same problem which was caused by the PCM volume slider being turned all the way down as described in that post.

---

### Post by vinater on 2008-12-11
Thanks, I had the exact same problem PCM volume at Zero anyone know the cause? I had recently installed ffmpeg and handbrake. Anyone else?

---

