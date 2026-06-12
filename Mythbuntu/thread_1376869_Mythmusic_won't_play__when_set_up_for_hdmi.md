---
title: "Mythmusic won't play  when set up for hdmi"
date: 2010-01-09
forum: Mythbuntu
---

### Post by benlyboy on 2010-01-09
Hi all

I had a problem getting my hdmi audio working, but I now have that working great.

My new problem is that now mythmusic isn't working. When I go into music, the play list comes up and it looks as if its about to start playing but never does.

If I go into "setup/general/audio system" and change the "Audio output device" from "ALSA:hdmi" to "ALSA:default then mythmusic plays just fine.  

Of course this mean I lose my HDMI, any ideas?

---

### Post by Neon Dusk on 2010-01-10
If you've got a properly set-up asound.conf then 'audio output device' can be left at 'ALSA:default'

So at the moment mythmusic plays over HDMI when set to 'ALSA:default' but tv/video doesn't?

Can you post your asound.conf file?

It sound be something like
```

pcm.!default {
       type hw
       card 0
       device 3
   }

```

or if that doesn't work try
```

pcm.!default {
     type plug
     slave.pcm "hdmi"
  }

```

---

### Post by benlyboy on 2010-01-10
Thanks Neon Dusk

That was the problem. I had a good asound.conf file but it had a typo in the name I had used "," instead of "." fixed that and all is good.

Thanks for the help

---

### Post by respond2vikas on 2011-02-01
I am new to Ubuntu and facing problem with no sound when i connect ubuntu laptop to LCD. Please help me understand this solution? What ALSA and how to configure it?

---

