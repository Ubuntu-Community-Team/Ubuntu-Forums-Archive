---
title: "[SOLVED] Banshee doesn't release audio device"
date: 2008-08-31
forum: Multimedia Software
---

### Post by shingalated on 2008-08-31
I have the new Banshee 1.2 and I love it, but if a friend sends me a youtube video or something and I pause my music to view it, it plays without sound.  In order for the sound to play, I have to exit Banshee, and Firefox and get back in to Firefox.  Is there a way to somehow make Banshee release the audio device as soon as it pauses?
Also...I am using flash player 10

---

### Post by lovinglinux on 2008-08-31
I have the same problem pausing a YouTube video and trying to open a local video with any player. If I close the YouTube page the audio device is released.

---

### Post by minky311 on 2008-08-31
Could both of you press alt F2 type in gstreamer-properties and tell me what it says next to pipeline under default output?

---

### Post by Dysphoria on 2008-08-31
I have the same issues with many combinations of sound and video, not just the banshee / YouTube example. Default Output Pipeline says "alsasink".

---

### Post by lovinglinux on 2008-08-31
> **minky311 said:**
> Could both of you press alt F2 type in gstreamer-properties and tell me what it says next to pipeline under default output?

autoaudiosink

---

### Post by minky311 on 2008-08-31
Press Alt and F2 type in gstreamer-properties and then press run.
For default output change plugin to alsa and for the devices try each one at a time and test it by trying to open two different programs up at the same time.

---

### Post by shingalated on 2008-09-01
I changed plugin from auto to ALSA, it didn't help. Pipeline is alsasink.

---

### Post by minky311 on 2008-09-01
Could you play something in banshee and then pause it, open up firefox in the terminal by going to Applications->Accessories->Terminal and typing in firefox and if there are any errors that appear in the terminal when you visit a website that uses flash like youtube could you post the errors here.

---

### Post by shingalated on 2008-09-02
I changed the Device from auto to something...digital and it now works perfect :-D

---

### Post by lovinglinux on 2008-09-02
> **shingalated said:**
> I changed the Device from auto to something...digital and it now works perfect :-D

Were did you do that?

---

### Post by minky311 on 2008-09-02
I'm pretty sure he pressed alt f2 typed in gstreamer-properties and changed the device there under Default Output.

---

### Post by lovinglinux on 2008-09-02
Still doesn't work for me.

---

### Post by minky311 on 2008-09-02
I would make sure everything is set to Alsa in System->preferences->sound and then going to gstreamer-properties and trying different devices.

---

### Post by Salomonis on 2008-09-03
I'm having the same problems.  What is it suppose to say in preferences-sound?
in gstreamer-properties it's under ALSA but the device is unsupported and the pipeline is autoaudiosink.  the test works.

---

### Post by Salomonis on 2008-09-03
I take that back.  the test works under properties/sound but not under gstreamer- properties.  maybe I need more gstreamer codecs?

---

### Post by Salomonis on 2008-09-03
Ignore my posts got it to work by switching everything to ALSA under properties

---

