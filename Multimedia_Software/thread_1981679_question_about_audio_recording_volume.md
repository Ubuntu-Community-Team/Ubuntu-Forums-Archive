---
title: "question about audio recording volume"
date: 2012-05-17
forum: Multimedia Software
---

### Post by Chiel92 on 2012-05-17
Hi,

I have a question regarding the volume of the tracks I record.
I use ubuntu 10.04, Jack and ardour to record songs on my acoustic guitar.
 :guitar:
Everything works well, but the volume of my tracks is a bit low. 
It should somehow be amplified.
My question: 
should I do this by setting the output volume of my preamplifier to maximum, 
or should I amplify the audio data afterwards on my pc using specific software (I believe ardour has some functionality for it).

Thanks in advance for any reply!

---

### Post by enigma32 on 2012-05-17
You should always try to get the level set appropriately going *into* the recording software. If you adjust it afterword, you will be adding noise into the resulting audio file.

I would check that:
1) Your input signal to the computer isn't too low (try just turning this up. Listen to the recording though-- if it gets "crunchy" sounding at loud moments you're probably overloading the computer's sound card, or "clipping", and should turn it back down a bit.)
2) If you tried #1 and starting getting bad sounds, find the recording level of that input on the computer and turning it up. You don't want the level to be >= 100%, and you don't want it to be 1%. Try and get to a place where you can leave that control at 30-60% (or if the control goes above 100% -- say, to 400%-- set it at 100%).

Have a look here for more information about how to set your levels:
[http://www.recordingreview.com/articles/articles/181/1/The-Basics-Of-Setting-Gain-Structure/Page1.html](http://www.recordingreview.com/articles/articles/181/1/The-Basics-Of-Setting-Gain-Structure/Page1.html)
I found that page with a quick google search, but at a glance it seems to explain the basics, and even specifically mentions acoustic guitars.

Hope this helps,
Matt

---

### Post by Chiel92 on 2012-05-19
Thanks for your tips!
I will look into it.

---

