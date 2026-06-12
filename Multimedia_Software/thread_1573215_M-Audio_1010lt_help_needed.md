---
title: "M-Audio 1010lt help needed"
date: 2010-09-12
forum: Multimedia Software
---

### Post by joebob213 on 2010-09-12
Hello all.

I have been using Ubuntu on and off since Gutsy and have always had the same problem...

I can get playback to work just fine on my sound card, M-Audio 1010LT, but I have NEVER... in all these years... been able to hear anything I run through the inputs.

I'm a guitar player.  At this time my rig is a Fractal Audio Axe-FX.  I run it direct into the sound card in Windows and that's how I play at home.

In Ubuntu, or any linux distro for that matter, I can't hear what's plugged into any of the inputs of the card.  Can't even get meters to jump in Envy24control.

This is a complete dealbreaker!!!  I spend more time playing guitar through my computer than I do browsing the internet or anything else so... I've always resorted back to windows for playing guitar.  

I LOVE everything else about Ubuntu and want to use it all the time!

At the moment I have 8.04 studio and standard 10.04.

Please help!

---

### Post by cchhrriiss121212 on 2010-09-12
The inputs are set to zero by default, what are yours set to? They are labeled ADC in the analogue volume tab of envy24.

---

### Post by joebob213 on 2010-09-12
> **cchhrriiss121212 said:**
> The inputs are set to zero by default, what are yours set to? They are labeled ADC in the analogue volume tab of envy24.

That did it!  Thank you, bro. 

Wow, seriously it's been five years of research and frustration and that's been starting me in the face all this time...

Next question lol.  Jack only recognizes my midi connections, no audio.  How do I get that set up?

---

### Post by cchhrriiss121212 on 2010-09-13
What is your interface set as in the jack setup window?
A screenshot of that setup page would help as well, or just post the output of:
cat ~/.jackdrc

---

### Post by joebob213 on 2010-09-15
> **cchhrriiss121212 said:**
> What is your interface set as in the jack setup window?
A screenshot of that setup page would help as well, or just post the output of:
cat ~/.jackdrc

.jackdrc: No such file or directory

:(

---

### Post by cchhrriiss121212 on 2010-09-16
Try it when jack is open.

---

### Post by joebob213 on 2010-09-16
I did. 

Here's a screen shot of my setup.

---

### Post by cchhrriiss121212 on 2010-09-16
When you press start does it run successfully? Then you should see audio ports available in the audio tab.

---

### Post by joebob213 on 2010-09-16
It fails and stops every time I press start :(

---

### Post by cchhrriiss121212 on 2010-09-16
Could you post what the message window says?

---

### Post by joebob213 on 2010-09-16
Here ya go!  I REALLY appreciate all your help BTW!

---

### Post by joebob213 on 2010-09-16
Duh... Ok so I added myself to the audio group and I think all is well :)  Now I just gotta learn how to use it!

---

