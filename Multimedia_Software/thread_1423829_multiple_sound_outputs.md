---
title: "multiple sound outputs"
date: 2010-03-07
forum: Multimedia Software
---

### Post by dingo17 on 2010-03-07
I am not really sure how to explain this. Normally when you play some music on laptop it is played through internal speaker and when you plug headphones in it is played through them. 

What I want to do is to add something somewhere so that I would be able to specify one application, output of which would be directed only through the built-in speaker even when headphones are pluged in and other apps would play normally the way they do now.
Is it possible to do?

---

### Post by kostkon on 2010-03-07
If you mean USB headphones, yes, it's possible, if you use the PulseAudio volume control.

Thus, you'll need to install the *PulseAudio Device Chooser* utility that'll allow you to easily access the PulseAudio volume control from your tray.

---

### Post by dingo17 on 2010-03-07
This PulseAudio Device Chooser is the thing I need but there is a little problem. What I want is one output to be played through the speaker only, even when the headphones are pluged in.

---

### Post by kostkon on 2010-03-07
> **dingo17 said:**
> This PulseAudio Device Chooser is the thing I need but there is a little problem. What I want is one output to be played through the speaker only, even when the headphones are pluged in.
Yes, you can do it. Just open the Pulseaudio volume control, find the stream you want to move and then send it to your sound card (i.e. speakers).

---

### Post by dingo17 on 2010-03-07
but when I plug the headphones in, it automatically turns the speaker off and all sound streams are played through headphones. I want one stream to be played through speakers all the time and other one to be played through headphones

---

### Post by kostkon on 2010-03-07
> **dingo17 said:**
> but when I plug the headphones in, it automatically turns the speaker off and all sound streams are played through headphones. I want one stream to be played through speakers all the time and other one to be played through headphones
Are you talking about USB headphones or about headphones that you connect to your computer's audio jack?

---

### Post by dingo17 on 2010-03-07
headphones with jack

---

