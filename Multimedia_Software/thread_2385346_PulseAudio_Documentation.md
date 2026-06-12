---
title: "PulseAudio Documentation"
date: 2018-02-19
forum: Multimedia Software
---

### Post by muddpup64 on 2018-02-19
Hello guys!

Does anybody have recommendations on documentation on how to manipulate PulseAudio?

My intent is to use Pulse in a way similar to that of Jack, without the repercussions of Jack interfering with my sound system.
I've dealt with Jack before and it's a big pain in the butt.

Thank you,
   -Matt

---

### Post by tlwest on 2018-02-20
A the risk of being excessively obvious, [https://wiki.ubuntu.com/PulseAudio](https://wiki.ubuntu.com/PulseAudio).

But my understanding is that the whole point of PulseAudio was to NOT manipulate it, it is supposed to "just work".

Jack has improved greatly in the last couple of years in that it generally just works, but provides the ability to fine tune the sound routing before handing off to PulseAudio or alsa and thence to the hardware..

Can you explain a bit more of what you want to do?

---

### Post by muddpup64 on 2018-02-20
> **tlwest said:**
> A the risk of being excessively obvious, [https://wiki.ubuntu.com/PulseAudio](https://wiki.ubuntu.com/PulseAudio).

But my understanding is that the whole point of PulseAudio was to NOT manipulate it, it is supposed to "just work".

Jack has improved greatly in the last couple of years in that it generally just works, but provides the ability to fine tune the sound routing before handing off to PulseAudio or alsa and thence to the hardware..

Can you explain a bit more of what you want to do?

Hmmm, most of this is what I already knew. I wonder if I'm asking thew wrong questions.

---

### Post by Yellow Pasque on 2018-02-21
[https://gavv.github.io/blog/pulseaudio-under-the-hood/](https://gavv.github.io/blog/pulseaudio-under-the-hood/)

> **muddpup64 said:**
> I wonder if I'm asking the wrong questions.

Pulseaudio is not meant to replace JACK. They have different goals:
[http://jackaudio.org/faq/pulseaudio_and_jack.html](http://jackaudio.org/faq/pulseaudio_and_jack.html)

Instead of trying to eliminate JACK, a better question might be how to stop JACK from interfering (and be more specific about how it's interfering).

---

