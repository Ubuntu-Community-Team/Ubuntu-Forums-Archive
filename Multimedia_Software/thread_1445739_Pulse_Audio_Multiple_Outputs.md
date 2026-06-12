---
title: "Pulse Audio Multiple Outputs"
date: 2010-04-03
forum: Multimedia Software
---

### Post by dartmusic on 2010-04-03
I've searched and searched and can't find a straight answer about this.  I want to sent the same signal out of the digital output and one of the analog outputs on the soundcard (Intel HDA) on my motherboard.  

I'm using ALSA and Pulse Audio.  Any ideas?

Thanks!

---

### Post by lidex on 2010-04-03
What are you getting now?

---

### Post by dartmusic on 2010-04-03
> **lidex said:**
> What are you getting now?

I can get audio from the front/main analog outputs OR the digital output, but not both at the same time.  I want to use the digital output to send to my receiver and also use the front/main analog to send signal to a wireless transmitter.

---

### Post by lidex on 2010-04-03
If not installed, install gnome-alsamixer. With that open, select "Edit>Soundcard Properties" and make sure all elements are checked/selected. On the soundcard mixer pane select the IEC* entries.

---

### Post by dartmusic on 2010-04-04
> **lidex said:**
> If not installed, install gnome-alsamixer. With that open, select "Edit>Soundcard Properties" and make sure all elements are checked/selected. On the soundcard mixer pane select the IEC* entries.

All elements are selected, but I have no options anywhere to choose any output in Pulse other than the digital out.

---

### Post by dartmusic on 2010-04-06
bump?

---

