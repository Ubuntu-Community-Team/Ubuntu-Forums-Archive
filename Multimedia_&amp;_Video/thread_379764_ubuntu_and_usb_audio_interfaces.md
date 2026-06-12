---
title: "ubuntu and usb audio interfaces?"
date: 2007-03-08
forum: Multimedia &amp; Video
---

### Post by [censored] on 2007-03-08
I been doing some multi track audio recording, using my mixing desk plugged directly into my sound card. I hear this isn't the way to do it though, and that most serious home recording enthusiasts use a USB audio interface like the ones on this site:

[https://www.billyhydemusic.com.au/shop/index.cfm?action=browse&id=46](https://www.billyhydemusic.com.au/shop/index.cfm?action=browse&id=46)

I note that most of these come with Windows software. Can you easily get any of these devices to work in ubuntu?

---

### Post by 23meg on 2007-03-08
See if the interface you want is supported by ALSA:

[http://www.alsa-project.org](http://www.alsa-project.org)


Also do a web search ("brand model +linux") to find out others' experiences with it, how it performs with JACK, etc. , and look the device up in hardware compatibility lists. The linux-audio-user and linux-audio-dev mailing list archives may also be helpful; you may also post to linux-audio-user to ask for advice.

My M-Audio Quattro USB works with four channel playback, but I haven't got it to work with JACK. I've seen success reports though, so it must be possible.

---

### Post by [censored] on 2007-03-09
Thanks. I see on the ALSA site that there's a few usb interfaces that are reported as compatible.

In my experience with linux, that often means that they can be made compatible if you have the expertise to tweak your system exactly.

I was hoping someone could recommend a basic usb interface that they know works easily, out of the box, or can be made to work by reading just one simple howto.

---

### Post by 23meg on 2007-03-10
If you search linux-audio-user, chances are you'll find many such recommendations.

---

