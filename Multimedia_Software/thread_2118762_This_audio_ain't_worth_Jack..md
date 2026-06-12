---
title: "This audio ain't worth Jack."
date: 2013-02-22
forum: Multimedia Software
---

### Post by mwynko on 2013-02-22
So, I've been trying for about a week now to fix a pulseaudio/jack disagreement in 12.10. I hardly know anything about Ubuntu, so any explanation of a potential fix goes right over my head.

Here's an example of my problem:

Say I'm watching a youtube video tutorial about Ardour. When I start Ardour, the audio from the video disappears. Not just that, but all audio except audio from Ardour. I can exit out of Ardour, and stop Jack with qjackctl, but the audio still won't play until I reboot.

This is terribly inconvenient, and if I can't resolve it soon, I'll probably just go back to Windows. I like Ubuntu well enough, but it doesn't really make sense to me how this problem even exists. How can I fix this?

---

### Post by coldraven on 2013-02-22
I'm not sure because I don't have Jack installed at the moment.(and I'm a Jack noob!)
Can you use Jack to patch the capture to **both **the input of  Ardour and directly to the system outputs?
I took me a while to figure out that you need to create a new connection with an alias in qjackctrl to do this sort of thing.
Hopefully some sound guru will come along and help you out.

---

### Post by mwynko on 2013-03-07
I've figured some of it out. The problem is that Pulseaudio and Jack really don't get along. It's like Jack slept with Pulseaudio's sister and never called her back, and now they're both at a mutual friend's house for a party but they're not talking and making everyone else uncomfortable, so there's just this big awkward silence. That awkward silence is now my laptop.

---

### Post by cortman on 2013-03-07
Except for the slightly nsfw allusion, your analogy is pretty good. :D
I don't use Jack- I've had best experience with Pulseaudio or alsa. Install pavucontrol and mess around with it.

---

