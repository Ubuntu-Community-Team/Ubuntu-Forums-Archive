---
title: "stereo and 5.1"
date: 2007-09-04
forum: Multimedia &amp; Video
---

### Post by nzadLithium on 2007-09-04
Hey

If i have 2.0 audio files how can i get it to send that info to the back as well and mix the two channels to get a center?

I found this which you put in the asound file:

pcm.ch51dup {
    type route
    slave.pcm surround51
    slave.channels 6
    ttable.0.0 1
    ttable.1.1 1
    ttable.0.2 1
    ttable.1.3 1
    ttable.0.4 0.5
    ttable.1.4 0.5
    ttable.0.5 0.5
    ttable.1.5 0.5
}

came from [http://alsa.opensrc.org/index.php/Playing_stereo_on_surround_sound_setup_%28Howto%29](http://alsa.opensrc.org/index.php/Playing_stereo_on_surround_sound_setup_%28Howto%29)

This will do what i want it to do but i'm wondering how this will effect any 5.1 movies i play. Will this mess up 5.1 sound?

---

