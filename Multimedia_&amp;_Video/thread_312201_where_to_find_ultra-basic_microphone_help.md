---
title: "where to find ultra-basic microphone help?"
date: 2006-12-04
forum: Multimedia &amp; Video
---

### Post by goodmanbrown on 2006-12-04
I just got some new hardware for my Edgy box:  an m-audio Audiophile 2496.  I also got one of the tiny little Behringer Eurorack mixers and a Nady SP-1 microphone.  I hooked it up tonight and am immediately running into the limits of my knowledge.

I'd like to be able to record my voice, a female voice, electric bass, and accordion.  (One at a time, obviously.)  So far, I've only tried the accordion and, for experiment's sake, a tin whistle.

Both instruments seem to be far too loud for the mic.  If I record them anywhere near the microphone, I get a choppy gurgle sort of noise when I play it back.  With the tin whistle, the choppy gurgly tones that play back seem to be shifted down the register-- the notes that play back are lower than the notes the tin whistle can generate.

With the accordion, I could only get an un-distorted sound if I point the mic away from me, into the seat of a plush chair, stand on the opposite side of the room, and play with my back to the mic.  But then the sound that records is horribly muddy.

I used envy24control to set the levels for alsa, and audacity to do the recording.  Audacity shows no clipping, so I assume the problem with the distortion must be before the signal hits the soundcard.  But the mixer seems fairly straightforward, and I don't know what I could be doing wrong.

This is a long-winded way of asking:  does anyone know of a good intro-level tutorial for how to record in linux using a microphone and a mixer?

---

### Post by auricle on 2006-12-04
Hi,

Sound recording is a very fine balancing act. You need to get the loudest sound possible without distortion. I won't go into details here but the louder the signal put onto the recording medium the less you have to boost the signal thus increasing noise when you mix in other instruments. This isn't as relevent as it was when we all recorded onto tape but a lot of equipment (especially budget) introduces some level of noise.

Unfortunately, you are experiencing distortion - which is what happens when the signal overloads the circuitry. There isn't just one level you need to worry about. You need to check:

1) A good level into the mixer. This is controlled with the 'gain' knob on the mixer. It is important that you get this right or else you get distortion created within the mixer's microphone pre-amplifier section. I don't know the Eurorack but usually there is a 'pre-fade listen' or an individual channel level meter to make sure you get a healthy level of signal into the mixer without distorting it. Check the manual of your mixer to find out how to do this.

Also, real life sounds are very dynamic - they can go from very quiet to very loud incredibly quickly. This is the bane of recording, you need to control this somehow. You could find that you get a good level, start recording and the musician sings or plays a louder note half way through the recording and destroying the track because of distortion.

There are ways around this. Experienced recording musicians usually have good microphone technique and know how to control their dynamics. 

The other way is to buy a compressor. This device automatically reduces the volume of the microphone over a set level. A lot of sound engineers use a little bit of compression to control the recording of microphones to prevent distortion. They start at a relatively cheap price. You can usually buy an all in one 'mic processor' unit which has a microphone input plus compressor and other goodies. You basically plug the mic in the input and the output goes to the soundcard or your mixer's line input.

2) The output from the mixer to the soundcard. Too loud a signal here and you will distort your soundcard input stage. Set up your meters in your recording application or set up some meter to monitor your input from within Jack (install meterbridge - a very good metering application). Make sure that the output from the mixer is not too loud otherwise you will distort either the mixer's output stage or the soundcard's input stage (despite the level you set within the soundcard's software).

3) Levels within the computer. At all stages - processing and mixing, can create distortion if you go too loud. You can have a very quiet instrument but if you add equalisation and increase the 500Hz frequency for example, you could create distortion. Check levels at all times.

4) Final output. Make sure that your final stereo out does not overload the input stage of you monitoring equipment, whether it is your amplifier, headphones or another mixer. The meter on the 'main out' or similarly named faders of your mixing software does not go into the 'red'.

Seems like a lot but after some experimentation it will seem like second nature. One thing to remember is microphone placement. The Nady microphone you have is a 'dynamic' model which is designed to be used fairly close to the instrument - otherwise it will sound muddy! Try different positions of the mic to get the best sound.

I hope that helps! I know that it is not ultra-basic but it is something you need to think about. Imagine the life of the instrument signal - right from the voice or instrument itself, to your headphones or speakers has to go through many different stages. Each stage's volume must be controlled separately. Practice is the key, after a few sessions you won't even worry about it.

---

### Post by falkenberg_cph on 2006-12-04
A good place to start is [www.homerecording.com](www.homerecording.com)
They have a good forum with many enthusiasts

/Carsten

---

### Post by goodmanbrown on 2006-12-05
Hey auricle, thanks for the help and the mention of meterbridge.  I was able to determine quickly that I had the gain on my mixing board set way too high.

Still a long, long way to go before I can do anything useful, but at least I can now get sound into my computer.

---

### Post by auricle on 2006-12-06
No problem Goodmanbrown. Keep at it!

---

