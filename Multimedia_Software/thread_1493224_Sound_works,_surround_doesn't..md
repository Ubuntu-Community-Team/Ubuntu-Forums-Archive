---
title: "Sound works, surround doesn't."
date: 2010-05-25
forum: Multimedia Software
---

### Post by uylug on 2010-05-25
Hi everyone. I have a 5.1 Logitech surround speakers. They work great under Linux. I can listen to music without problems.

The problem is that I can't enable surround. If I set players to use surround sound I completely lose some channels. For example, I can hear most effects but can't hear people's voices. I made sure my channels weren't muted but still couldn't get it to work.

I used speaker-test to test my channels, it was outputting audio through the wrong channels so I adjusted that manually in my .asoundrc. Still no luck. speaker-test would work great but apps still wouldn't play some channels.

My audio device didn't work out of the box, its a CM6501 USB audio, so I had to create a asoundrc to get it to work for the first time.

So I was wondering whether you had any tips to get this issue solved or whether you found some threads to be useful. None of the threads I've found seemed to solve my problem, hence why I'm starting this new thread.


Thanks in advance.

---

### Post by uylug on 2010-05-25
Also, I noticed that a certain channel isn't outputting anything.

> ttable.2.2 1
ttable.3.2 1
ttable.4.2 1
ttable.0.2 1
ttable.1.2 1
ttable.5.2 1

I redirect all the output to CH 2 but I get no sound. Stereo makes all of the speakers output sound.

---

### Post by jmate24 on 2010-05-25
+1
i have a surround sound laptop and i experience the same thing when i use windows 7 but not in ubuntu...

i have a: Lenovo y510 and i have found out that most intel chipset soundcards are supported by (K)(X)Ubuntu.

you may have better luck when you make sure the chipset is intel.

---

