---
title: "surround sound not working in xine"
date: 2008-08-02
forum: Multimedia Software
---

### Post by piratebill on 2008-08-02
Up until very recently, surround has worked perfectly in xine.  Now I can only get stero sound.  I have the configuration set to "Master of the known Universe" (kind of ironic given the current situation) but the option to select the speaker arrangement is missing.  if I type "speaker-test -Dplug:surround40 -c4 -twav" in the terminal, it plays a sound on each speaker individually, so I know the OS does detect the surround sound setup.  

I also tried to change xine's config file by hand.  the file is supposed have a line like this: audio.output.speaker_arrangement:Surround 4.0
but there wasn't even a line for the speaker arrangement.  I added it but it still is not working.  I even ran apt-get remove --purge xine-ui but still it doesn't work.  Does anyone know where I should go from here?  Thanks in advance.

---

### Post by piratebill on 2008-08-03
.....------.........
bump^

---

### Post by piratebill on 2008-12-05
I found a solution to the issue.  Disable pulseaudio

```
killall pulseaudio
```

---

