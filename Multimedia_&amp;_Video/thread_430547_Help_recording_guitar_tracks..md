---
title: "Help recording guitar tracks."
date: 2007-05-02
forum: Multimedia &amp; Video
---

### Post by abyssspecter on 2007-05-02
Hey all. 
Please correct me if this is not the right place.
I may sound like a linux noob, but i have a problem. Recently I have been attempting to record guitar tracks to my computer, using audacity. Originally, i tried to use a 1/8-to-1/4 plug. I plugged that to my mic jack, and the other 3 (what looked like) input jacks. nothing worked.

So i attempted to record from my computer mic. all i got was a roar.

any help would be mch appreciated.

The Specter

---

### Post by bakermiller on 2007-05-02
Are you using a mixer or some kind of amp or pre-amp?? Or you just plugged your guitar into the computer using a jack/headphone(1/8th) adapter??

Ideally, if you want to record without hiss and clicks, you should get an external sound card (usually they have 2 midi in/out and jack/headphone/RCA inputs and are shielded from interference) or plug into a mixing board. Unless you want to find a new kind of electro-static experimental sound.

Did you manage to record voice or anything else using that input?

If i understand correctly, you plugged your guitar into the computer. You are probably picking-up all your body's and guitar's static and sending it into the mic.
I have more experience recording from turntables than guitar, but static is static for everyone.

Also, try playing around with your input levels. If your input is too strong, it will saturate the recording track (roar).

Good luck

ps: mic input is usually the red one.

---

### Post by abyssspecter on 2007-05-02
My only preamp, should it be called that, is my Digitech 300A effect processor.

I am operating off of a teenage parents parttime wages. so, an external soundcard, unless one is $50 at most, is out of the question. i bought my jack/headphone cable at $5 from radio shak, and it is shielded.

I did fail to mention, however, that, using my microphone, i checked thatit was working using the basic sound recorder. so, is that a problem in audacity that i may be able to fix?

---

### Post by bakermiller on 2007-05-02
hmmmm.
Did you try recording with your mic using audacity?
Maybe it`s your digitech processor making all that fuzz...
it`s plugged into the wall right?
are you using the jack or xlr output?

Do you have an old stereo amp you could use between your computer and effects processor?
maybe that could clean up the sound and prevent your processor from polluting your mic line.

i have recorded from my mixer using audacity in the past without any special settings. so i would exclude audacity as the problem for now...

...later

---

### Post by abyssspecter on 2007-05-02
its pluged in right. i have 2 out puts from the Digitech. one was going to the computer, the oother to my stereo amp. when that didnt work is when i went to the mic, which i set up in front of my amp (an Ibanez TB25) and then the low frequency roar occured. i turned down all the settings to 0, and moved the mic above it, and the same thing. 

:(

no roar, like i said, in Sound Recorder.

---

### Post by bakermiller on 2007-05-02
Did you try your mic in audacity?

i recorded my voice successfully with a really cheap mic ( you could even plug-in your headphones and talk into them!!) using audacity "out of the box", only i had to show it the way to the proper sound card in >> preferences>>audio I/O>>recording>>device.

Are you planning on playing guitar over another rhythm track or something. because if you are not you could always use the sound recorder to make a guitar track and import it into audacity to edit, add tracks, effects, etc... it's not the proper way, but could keep you moving creation-wise.

One thing is for sure: not using a shielded external sound card will always make a hiss...
But if your noise is more in the low-frequency, it must be your effects box making it or your stereo amp or ibanez amp (does it have lamps inside?).
try putting your headphones into your effects box's output and listen to the ambient noises produced by various electric machines around the house, it's interesting!!!
I've had many bad experiences to realize that. And having all that electro-static generating gear around your computer will  produce parasites in the sound. 

unfortunatelly, home production is not perfect world it's advertised to be in the mac and windows adds.  

Check out lee "scratch" Perry  and his production methods if you need inspiration in terms of getting the best out of what you have at hand. the legend says He built a pool under his drum kit to make it sound deeper and bring the water elements into his music:P. He brought a cow into the studio and recorded it and made great songs. Then he burned down his studio just to watch it burn!!!

good luck again, and don't be afraid to experiment (safely!!)

---

### Post by imdidactic on 2007-05-03
Most people recording in Ubuntu are using the MBox2 from M-Audio.  Without a proper interface your guitar recordings are going to be crap regardless of what Digitech stuff you're running.  Computer sound cards aren't made to handle the kind of sound output that a guitar produces.  I know that musician's don't want to spend any money, but the one thing you have to spend on when you do home recording is a good analog to digital converter.

---

### Post by Jonam on 2007-05-03
I've been using M-Audio Audiophile 2496 and Soundblaster Live! cards to record guitar/ bass into my PC and have had no problems with noise with either. I have a small mixer which I plug my guitar into to bring the signal to line level and that's about it. I have also recorded using a stereo condenser mike in front of my amp. The only noise I get on the recordings is the mains hum from the guitar pickups.

I suspect that you are trying to plug a single guitar cable (mono) into the stereo inputs on your soundcard. This is probably why you aren't getting any sound into your PC. I checked the Digitech site for the manual of your effects unit (RP300A) and its stereo outputs (2 x 1/4" sockets for Left and Right channel) must be combined into a single stereo 1/8" plug to go to your soundcard stereo input. 

You should be able to get a Y-cable or adapter that converts 2 x 1/4" mono plugs to one 1/8" stereo plug. I had a quick look on the RadioShack website but could not find a suitable adapater which means you may have to make up one or try and find something at a guitar shop. Also, soundcards usually have a mic-in and a line-in. You should plug into the Line-in if you are using output from your effects processor.

The roaring sound you are getting from your mike when you place it near the amp I am not sure about. What sort of mike is it? 

I will try out Audacity over the weekend with a computer mike to see what happens. When you are using the basic Sound recorder software, have you tried this with voice only or have you placed the mike near your amp?

Jonam

---

### Post by Jonam on 2007-05-05
Update - tried out Audacity and Sound recorder with the microphone and it worked fine. I just had to make sure I was using the right input and playback devices in Audacity to get it to record the sound.

Jonam

---

### Post by abyssspecter on 2007-05-07
ooh, sorry i havent looked at this.

What i ended up doing was recording myguitar/voice in sound recorder and mixed it down in audacity.

but, i do appreciate all the help that was offered.

---

### Post by trepid666 on 2007-11-28
Hey everyone (hi doctor nick...lol).

This is a cool thread. I've learned some cool things by reading your posts =)

I am looking for some working programs for home recording. I'd like to see this topic keep going =)

I'm trying to find the right setting for my recording device in preferences. by default audacity wants to use /dev/dsp .  I'm not too sure what that is. 

any help would be appreciated. thanx

---

