---
title: "Getting my mic to record"
date: 2009-06-10
forum: Multimedia Software
---

### Post by defaria on 2009-06-10
I wish to use Boxee. In using it I had a number of problems and people told me to remove PulseAudo and instead rely on ALSA. Boxee it better but still has problems.

Meantime I'm trying to get Skype to work. Naturally this means getting a mic and getting it to work. In Linux rarely do such things just work out of the box and true to form the microphone fails to work. I can hear myself talk through the speakers but nothing is recorded when I try to record the mic. If the sound recorder cannot record then I'm sure that people will not be able to hear me if I place a Skype call.

I've searched around - I did. And I tried many things. Of course none of them worked - so I'm asking here - how do I get the mic to record?

Recently, looking at [Getting Line Input to work]("https://help.ubuntu.com/community/SoundTroubleshooting#Getting%20Line%20Input%20to%20work%20(Microphone,%20etc)") it states to run pavumeter --record. But I have no PulseAudio anymore so that won't work. Instead I run aslamixer and follow the rest of the directions but nothing works.

Then I tried to run gnome-alsamixer and noticed not one but two toggles named "Input Source" and they are toggled off. Thinking that that might be the problem I toggled them on and received the following interesting message:

** (gnome-alsamixer:28832): WARNING **: gam_toggle_set_state (). No idea what to do for mixer element "Input Source"!

How do I get my mic to record?

Oh, and extra credit - on my Jaunty 64 bit machine it used do pay attention to my volume wheel on the keyboard to raise and lower the volume. When doing so I would see one of the Jaunty notification popups showing me the volume going up or down. It still does that but the volume doesn't go up nor down. I suspect this is because that thing was connected to PulseAudio in some way. How can I fix this so that my volume wheel actually changes the volume!??

Thanks.

---

### Post by defaria on 2009-06-17
Bump! Anybody?????

---

