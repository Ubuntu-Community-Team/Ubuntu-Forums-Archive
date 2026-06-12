---
title: "audio issues"
date: 2011-11-13
forum: Multimedia Software
---

### Post by spezticle on 2011-11-13
I'm using google voice to make a phone call. whenever the person on the other end of the line talks, my microphone picks it up. I'm using headphones for audio output, so it is impossible for the microphone to actually be picking up audio from speakers output.


somehow it seems to be a software or configuration error.

how do i diagnose this problem and fix it.

---

### Post by VictorMature on 2011-11-13
I use Google voice and I have to play with the sound settings.  Maybe drop the sensitivity of the microphone.  I find it easiest to use alsamixer from a terminal.  I also find it handy to use audacity to check my microphone since Google does not have a test call service like Skype.

---

### Post by spezticle on 2011-11-13
I was testing with different volume levels and there was no echo unless i had the microphone all the way off.
It seems like the input and output channels are bleeding together for some reason.

Audacity reflects the same thing. Whenever audio outputs the microphone input levels are also receiving that signal

---

