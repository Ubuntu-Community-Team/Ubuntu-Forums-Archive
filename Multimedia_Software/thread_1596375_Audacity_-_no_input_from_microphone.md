---
title: "Audacity - no input from microphone"
date: 2010-10-14
forum: Multimedia Software
---

### Post by sanderella on 2010-10-14
I have Ubuntu 10.10. Maybe the sound card does not recognise my microphone. Can anyone suggest where to start? Thanks. (It works on my hubby's windows computer)

---

### Post by cchhrriiss121212 on 2010-10-14
How is this microphone connected? ie USB
Check arecord-l from a terminal window, and check volume levels with alsamixer.

---

### Post by robertsclark on 2010-10-15
Don't know if it will help you, but I had a similar problem on by Acer Aspire One AOA150 under Ubuntu 10.10.

I had to download and install pavucontrol.  When I ran this, the sound  profile is set to Analog Stereo Duplex.  I had to go to the Output tab  and set the volume slider on either the left or right channel to Silence  and then suddenly the microphone would burst into life.

Robert

---

### Post by nuoritoveri on 2012-10-30
I just want to add that I tried to use **pavucontrol** to solve this problem. I changed some microphone settings and my computer began to make **very loud noisy sound**. I'm glad I didn't have **headphones** on and so I warn you not to.

---

