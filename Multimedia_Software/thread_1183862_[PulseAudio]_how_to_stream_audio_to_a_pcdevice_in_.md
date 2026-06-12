---
title: "[PulseAudio] how to stream audio to a pc/device in a network"
date: 2009-06-10
forum: Multimedia Software
---

### Post by GehennaNL on 2009-06-10
Hey everyone,

I have a question that I can't seem to find the answer to:

I want pulse audio to send the audio from my linux pc to a another pc in the network. This is pretty easy if you have PA installed on both pc's. 
now the tricky part is that I don't have pulseAudio installed on the other pc (because this pc is just for testing, in the future this pc is actually replaced by a embedded device (which i'm developping) with a line-out)

So what I like to have is that pulseaudio send it's audio to a specific ip (e.g. 10.0.0.200)
so that i can listen (for instance with vlc) to this stream on the other pc (10.0.0.200)

My question is:
Is it possible to set up PulseAudio to send a stream to antother pc (which hasn't got PulseAudio installed), and how do I configure PulseAudio to do so? or is there an easier way to send audio to a specific IP adres?

Regards,

Stefan

---

### Post by GehennaNL on 2009-06-11
anybody?

---

### Post by dtzortzis on 2011-05-10
I just found this here:
[http://www.adriancoroian.com/technical-stream-audio-on-the-web-with-pulseaudio-in-ubuntu-10-10/](http://www.adriancoroian.com/technical-stream-audio-on-the-web-with-pulseaudio-in-ubuntu-10-10/)

If I may ask, what device are you developing? I'm also searching to make some device to send audio over the network :)

---

