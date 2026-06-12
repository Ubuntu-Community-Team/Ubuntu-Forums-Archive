---
title: "Glitches and noises with Edirol UA-25"
date: 2007-05-22
forum: Multimedia &amp; Video
---

### Post by eivind on 2007-05-22
Hi there,

I have a problem with crackling/whining noises in my Edirol UA-25. This, for the uninitiated, is a USB 1 2-in, 2-out soundcard, very convenient and with decent quality built-in mic preamps. I should mention that I have researched the matter with noisy UA-25's already - but no net resources seem to give the answer to my problems. Here goes:

When I connect earphones to my UA-25, everything is perfect, and the card works well (except for the occasional xrun, and the fact that qjackctrl won't let me use the card in real-time mode). 
However, when I connect anything to the line outputs, I hear a constant pulsating high-pitch noise. I have tried both the jack and phono outs - and the noise level is lowest using balanced TRS jack outputs, with balanced XLRs in the other end, but it's still audible and after a short while annoying.
It's a bit difficult to describe the noise - it sounds like something in between SMPTE code and mobile phone interference, run through a low-cut filter and heavily gated. Also, and this may be important, I hear a noise pulse whenever something changes on my laptop screen (like maximizing or minimizing a window).

I hear no noise on recordings, and no noise using headphones. It is only present when I use any of the line outs, and it's most prominent in the left channel.

I have tried switching the phantom power on and off, using a different USB port on my laptop, and generally turning every knob up and down. I have not yet tried switching the USB cable, partly because the manual swears I must use the supplied cable. 

Any ideas would be welcome.

Thank you,

Eivind

---

### Post by eivind on 2007-06-09
A note to myself and others who may be in the same situation:

It seems that ground loops can cause a lot of noise in the UA-25. An advice I've seen is to isolate the ground plug of your PC or other connected equipment. Do so at your own risk, of course.

Regarding the xrun problems: I have had no problems since bringing the buffers way up to 3x 4096. That makes for non-satisfactory latency, but as I use the direct monitor feature on the UA-25, I don't need software monitoring when multitracking. In other words, the 1/4-second latency is no problem.

---

### Post by jimrp on 2008-06-19
Hi there, I know this post is old but did you ever solve the problem?  I've found a simple cure... run the laptop on battery only!  Laptop PSUs are horribly noisy in the AF range for some reason, desktops aren't!

---

