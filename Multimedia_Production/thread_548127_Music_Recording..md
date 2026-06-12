---
title: "Music Recording."
date: 2007-09-10
forum: Multimedia Production
---

### Post by CapitanYochua on 2007-09-10
I have ubuntu studio and need overall help recording music. I got a microkorg synth and a 1/8'' adapter to connect it to my computer. I hear the music playing through the cmputer speakers too. I know I can use Ardour to record ( which is what I would prefer). I need to know all the inputs and outputs I need to connect, and basically the configuration of Jack and Ardour to allow me to record my synth. I pretty much know nothing. Any help is appreciated.

---

### Post by kayosiii on 2007-09-13
I like to use patchage for routing so I reccomend installing it.
You will need to add a track to ardour (stereo if you are going to record in stereo).
This will create one or two new inputs for ardour - now route these to the inputs on the soundcard you will be actually using.

---

### Post by CapitanYochua on 2007-09-13
How do I know all the details of the inputs and soundcards to route with patchage?

---

### Post by darsu on 2007-09-16
I use QJACKCtl to control JACK and signal routing. The "Connections" dialog in it will show all available JACK ports in running programs. How I set up to record a stereo track:

1. Start JACK via QJACKCtl.

2. Start Ardour.
2a. Create session via Session->New
2b. Create a track via Session->Add Track/Bus, and make it stereo.

3. In QJACKCtl click "Connect" to show the patch window.
3a. patch output from whatever in the left side list looks like your soundcard's pcm left/right channel ports (on my system they're alsa_pcm:capture_1 and capture_2) to ardour:Audio 1/in 1 and Audio 1/in 2 (the left and right channel of the track created in 2b respectively) in the right side list.
3b. patch output from ardour:Audio 1/out 1 and Audio 1/out 2 in the left side list to ardour:master/in 1 and master/in 2 in the right side list.
3c. patch output from ardour:master/out 1 and master/out 2 in the left side list to whatever looks like your soundcard's left/right channel pcm output ports (on my system they're alsa_pcm:playback_1 and playback_2) in the right side list.

---

### Post by CapitanYochua on 2007-09-18
Did all that and it isn't working.

---

