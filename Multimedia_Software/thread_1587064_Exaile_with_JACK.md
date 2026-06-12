---
title: "Exaile with JACK"
date: 2010-10-02
forum: Multimedia Software
---

### Post by Edu Camargo on 2010-10-02
Hello guys,

Trying to run Exaile and play music with it through Jack and I get this message: 'The autoaudiosink is missing'. What should I do?

Thanks in advance for all the directions.

Regards,

Edu Camargo.

---

### Post by Pablo_F on 2010-10-03
Hi Edu, 

Run "gstreamer-properties". In the Audio tab, Default Output, select the Custom plugin and enter "jackaudiosink" (no quotes) in the Pipeline field. 

In Exaile, Edit -> Preferences -> Playback. Make sure that "Audio Sink" is JACK.

Cheers! Pablo

---

### Post by Edu Camargo on 2010-10-16
Sorry for the delay. Worked properly, although I've noticed that  via JACK some GStreamer-based applications, gapless playback works but not 100%. In some track transitions, some clicks and pops occur, something that does not happen with pulse or ALSA. But thanks for the given directions.

Now I've just found a way to make Pulse recognize the Delta Audiophile 24/96's analog outputs, then use it for music playback. It works, although Totem seems to have some issues with DVD playback. Yeah, when I thought I was through, there was something left to look at. But I'm willing to solve it.

Again, thanks for your reply.

Peace,

Edu Camargo.

---

