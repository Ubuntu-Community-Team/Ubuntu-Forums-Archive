---
title: "Searching for PCM"
date: 2007-11-18
forum: Multimedia &amp; Video
---

### Post by Vivaldi Gloria on 2007-11-18
In my Gutsy I can choose among

  Mic - Front Mic - Line - CD

as an input for sound recording. But I want to record PCM. Why, oh why, PCM is not among the choices?

---

### Post by Yellow Pasque on 2007-11-18
What kind of sound card do you have?

lspci | grep "audio" if you're unsure.

---

### Post by Vivaldi Gloria on 2007-11-18
Thanks for answering. My motherboard is the following one:

[www.gigabyte.co.nz/Products/Motherboard/Products_Overview.aspx?ProductID=2455](www.gigabyte.co.nz/Products/Motherboard/Products_Overview.aspx?ProductID=2455)

It has onboard sound. The specs chart say "Realtek ALC888 8 Channel Audio Codec ".

lspci | grep "audio" comes back empty.

---

### Post by Vivaldi Gloria on 2007-11-18
lspci | grep "Audio"
gives

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)

I forgot that things are case sensitive. It worked with "Audio" instead of "audio".

---

### Post by Vivaldi Gloria on 2007-11-19
Temüjin? Anybody?

---

### Post by Yellow Pasque on 2007-11-19
Hmm, I guess I don't understand what you're trying to do. are you recording an instrument or something from a microphone?

---

### Post by Vivaldi Gloria on 2007-11-19
I can record mic in sound recorder without a problem. But I cannot record the output of programs, for example BBC radios (firefox) etc. In XP the way to do this is to choose "Stereo Mix" as the recording input. How can I do that with Ubuntu?

I have attached a picture in case it helps.

---

### Post by Ramaddan on 2008-05-16
Hi,

That is the exact question that I have been asking myself for a while, and until now, no real answer.

Sorry to bring this topic back to life, but I thought that with the introduction of PulseAudio to Hardy, maybe more options are available now.

Does anyone have an answer to this question:
"Is there a way to record PCM? Or any sound coming out from programs, videos, etc...?"

---

