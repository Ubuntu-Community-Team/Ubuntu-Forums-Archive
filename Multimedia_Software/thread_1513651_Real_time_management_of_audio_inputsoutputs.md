---
title: "Real time management of audio inputs/outputs?"
date: 2010-06-19
forum: Multimedia Software
---

### Post by beastrace91 on 2010-06-19
Howdy There,

I was wondering if there is an application for Ubuntu (FOSS or otherwise) that would allow me real time management of all of my audio inputs and outputs.

Essentially I have multiple microphones attached to my computer and multiple audio outputs. What I am looking to do is to be able to assign each different input to it's own audio output. A touch screen interface is a plus for the program but not necessary.

Anyone know of software that does what I am describing?

Regards,
~Jeff

---

### Post by cchhrriiss121212 on 2010-06-20
You need jackd (the best sound server on linux designed for audio work) plus patchage, which will do exactly what you want (minus the touchscreen). Your success with it may depend on what you want to use it with, as not all programs are jack compatible. But you can get ALSA to put all system sounds through jack.

---

### Post by beastrace91 on 2010-06-21
Maybe I am just not understanding the GUI/documentation (only glazed over it, going to read more of it later). But is Jackd for managing application's sound output only or is there a way I can capture audio input and control where/how it pipes back out of my system?

~Jeff

---

### Post by kostkon on 2010-06-21
If you are using Ubuntu, then the app you want is called *PulseAudio Device Chooser*.

Hope that helps.

---

### Post by cchhrriiss121212 on 2010-06-22
> **beastrace91 said:**
> Maybe I am just not understanding the GUI/documentation (only glazed over it, going to read more of it later). But is Jackd for managing application's sound output only or is there a way I can capture audio input and control where/how it pipes back out of my system?

~Jeff
It does both as it is designed for music production. Here is a screenshot of patchage which is the app that gives visual representation of what jack does:
[IMG]http://www.kalasmusicstudio.com/images/Patchage_MIDI_Record_Rosegarden.jpg[/IMG]

---

### Post by AutoStatic on 2010-06-22
> **kostkon said:**
> If you are using Ubuntu, then the app you want is called *PulseAudio Device Chooser*.PulseAudio works with latencies up to 2 seconds. I would also suggest using JACK, unless I misinterpreted the real time part. If I reread the initial post than JACK is exactly what you're looking for because that is one of the things JACK is good at, real time management of audio input and output ports. So not only output ports, also input ports.

---

