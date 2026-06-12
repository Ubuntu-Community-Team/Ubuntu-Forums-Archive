---
title: "Laptop as a PA-System"
date: 2016-03-31
forum: Multimedia Software
---

### Post by asearle on 2016-03-31
Hallo Everyone,

I will be using my laptop for a presentation with some audio content.  That works fine.

However, if it turns out that there is a larger number of guests, then I would maybe also like to use a microphone and the laptop's audio (connected to reasonably powerful external speakers) to amplify my own voice (i.e. DIY public-address system).

My question is whether there is a simple way to do this?  Maybe settings in one or other audio-program?

Any tips or links to HOWTOs would be greatly appreciated.

Many thanks,
Alan Searle
Cologne, Germany

---

### Post by Bucky Ball on 2016-03-31
Pulseaudio Volume Control. Install (if it isn't installed already), plug in a mic, launch it, experiment. Any questions, just ask.

How are you attaching to these 'reasonably powerful external speakers'? Via the headphone jack?

---

### Post by asearle on 2016-03-31
Hi Bucky Ball,

Yes, that looks very promising but it's not quite working yet:  I have opened the Pulse Audio Volume-Control and can see my spoken microphone input being registered (the monitor moves).  I can also play audio through the speakers (attached to the headphone jack) but I can't seem to combine the two and get my voice to come out of the speakers.

Is there a switch that I should flick or a setting that needs changing?

Many thanks for any tips that you can give me.

This'll be great, if I get it working  :-)

Many thanks,
Alan

---

### Post by Bucky Ball on 2016-03-31
Go to the Output or Recording tab and change the port for your mic to the headphone output. As I say, you may need to experiment.

---

### Post by asearle on 2016-03-31
Hallo again,

I've been checking all the options under Output and Recording and can only see ...

Show:  All Streams, Applications and Virtual Streams

When I am on Record (under any of these options) I see only a message: No applications to record

When I am on Output I see only "System Sounds" (with a volume slider).

Is there some extra add-on or plugin that is needed?

I hope I/we can figure it out.

Many thanks,
Alan

---

### Post by Bucky Ball on 2016-03-31
Yea, doh! Why it didn't occur to me earlier ... you would need to be running it through an audio app and do it that way. Try installing Audacity and get the mic working there, then when you look in PAVControl you'll see an Audacity audio stream. Try adjusting the port on that. (You should see something for it in Playback and you can adjust the port to the headphones there perhaps).

It will be a specific config because it is not something users regularly want to do and can cause massive problems with feedback through laptop speakers (and others so be careful and start each test with the volume down on the external speakers if possible). Probably why it's not obvious and easily done accidentally. :-k

In the config tab, what do you have set there? A duplex something?

BTW, how many people does the room hold?

---

### Post by asearle on 2016-04-01
Many thanks for your patience here.

Yes, I think I understand it better now and, indeed, when Audacity is playing, I see that as a Playback option. Excellent.

But now I am having trouble getting my microphone recognised in Audacity: I have the options "default" or "Pulse" but under both the microphone slider remains greyed out.

I'll keep experimenting and am sure I will work it out.

Cheers and many thanks,
Alan

---

### Post by Bucky Ball on 2016-04-01
Yes, you'll probably land on the right combination of settings by accident! 

Have you tried tweaking with alsamixer? I think Audacity goes through that then to Pulse, just to make things more confusing, so you may need to tweak a setting in alsamixer. Pay to do a bit of research on that. I've used Audacity for a million and one things but not for a mic. Although I did help my father-in-law set up Audacity to use a mic a few years ago. How we eventually did it is lost in the mist now, though, unfortunately. :|

[Here's something]("https://help.ubuntu.com/community/AudioCapture#Audacity"), though not much. It may give clues for further exploration though ...

You might want to scan that whole page. Sound Recorder is another possibility, although I'm not at all familiar with that. It may be capable of doing the same. If you can get Audacity going, though, better option as way more powerful and flexible once you're across it. :D

* PS: If you want to get more involved you could start looking in to [JACK]("https://help.ubuntu.com/community/What%20is%20JACK"), but that is probably overkill.

---

