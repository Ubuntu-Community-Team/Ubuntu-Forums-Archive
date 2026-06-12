---
title: "Seeking Linux/Python resources for audio programming"
date: 2012-07-21
forum: Multimedia Software
---

### Post by ladasky on 2012-07-21
Hello everyone,

I'm an amateur programmer, musician, and composer on the side.  I am seeking Linux resources which will allow me to send audio data to my sound card.  I am not interested in MIDI at this time, I have raw audio waveforms that I want to hear.  It does not have to be real-time, I can queue up a snippet and play it back.

What does the audio interface in a modern PC look like?  And how do I talk to it?  If this can be accomplished within Python, that would be my ideal choice.

Thanks for any advice!

---

### Post by Rodney9 on 2012-07-21
Audio python

[http://wiki.python.org/moin/Audio/](http://wiki.python.org/moin/Audio/)

AVLinux for Musicians

[http://www.bandshed.net/AVLinux.html](http://www.bandshed.net/AVLinux.html)

The engine of AV Linux is a customized i686 3.0.16  Linux Kernel featuring many performance and tuning enhancements to effectively maximize operating efficiency. The most notable feature is the IRQ threading and rtirq-init functions of the Kernel being activated dy default which creates an optimal low latency audio production environment.

---

### Post by ladasky on 2012-07-21
> **Rodney9 said:**
> Audio python

[http://wiki.python.org/moin/Audio/](http://wiki.python.org/moin/Audio/)


Thank you Rodney9, I visited that page once before and drew a blank.  I thought that sending a raw audio stream to the audio interface would be part of the Python standard library.  We can do anything we might want to do with graphics using Python, so why not sound?  

Anyway, I read the "Beyond the default modules" section this time.  It looks like PyAudio ([http://people.csail.mit.edu/hubert/pyaudio/](http://people.csail.mit.edu/hubert/pyaudio/)) or PyALSA ([http://pyalsaaudio.sourceforge.net/](http://pyalsaaudio.sourceforge.net/)) will do what I want.

AVLinux for Musicians is complete overkill for me at this time, but I'll certainly keep it in mind if I ever need to do multi-track recording.  Thanks!

---

