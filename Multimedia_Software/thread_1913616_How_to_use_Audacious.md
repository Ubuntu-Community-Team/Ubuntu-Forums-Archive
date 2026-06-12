---
title: "How to use Audacious?"
date: 2012-01-22
forum: Multimedia Software
---

### Post by neu5eeCh on 2012-01-22
I was just trying play some .mid fles. Audacious popped up, but when I tried to play the files I got the following error message:

"You have not selected any sequencer ports for MIDI playback.  You can do so in the MIDI plugin preferences."

This means absolutely nothing to me; and googling for information on this error message leads to more meaningless gibberish. I can't find anything under Audacious preferences that sounds remotely like "sequencer ports" or "MIDI plugin preferences". There's probably a simple solution to this. Can anyone help?

---

### Post by Toz on 2012-01-22
Parole plays midi files for me. If you want to use audacious, this might help: [http://linuxtechie.wordpress.com/2008/01/22/how-to-ubuntu-midi-playback-with-audacious/]("http://linuxtechie.wordpress.com/2008/01/22/how-to-ubuntu-midi-playback-with-audacious/").

---

### Post by neu5eeCh on 2012-01-22
Thanks Toz, I saw that post, but it's from 2008. The information didn't jibe. I'll try Parole.

---

### Post by MoreOrLess on 2012-01-23
Here's a screenshot from the latest audacious. Maybe that will help.

---

### Post by andrew.46 on 2012-01-23
Certainly works here as well. I compiled against libfluidsynth and selected this in the options plus put the path in for a sound font. Hopsfully this is clear in the screenshot I have attached...

---

### Post by neu5eeCh on 2012-01-23
Thanks MoreOrLess & andrew, your images were a help and I verified that my setup is ostensibly like yours, though using a different sound card & mixer, but I still get the same error. In the meantime, parole is working beautifully. Not sure whether to mark this thread solved or not, but as long as parole is working...

---

### Post by gradinaruvasile on 2012-01-23
Ummm.. Did you try ticking that checkbox? Or changing the output plugin (alsa or fluidsynth)?

---

### Post by andrew.46 on 2012-01-24
> **Toz said:**
> Parole plays midi files for me.

At the risk of hijacking this thread can I ask what parole is built against to enable midi playback? My own does not play midi although I was immensely pleased to see that goom is supported :).

---

### Post by Toz on 2012-01-24
@andrew.46, parole is a front-end to gstreamer. The gstreamer midi plugin is located in the gstreamer0.10-plugins-bad package. Looks like it uses wildmidi ([http://wildmidi.sourceforge.net/]("http://wildmidi.sourceforge.net/"))

---

