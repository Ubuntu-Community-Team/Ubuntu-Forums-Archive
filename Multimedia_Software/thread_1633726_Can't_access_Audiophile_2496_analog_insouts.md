---
title: "Can't access Audiophile 2496 analog ins/outs"
date: 2010-11-29
forum: Multimedia Software
---

### Post by Rocket J Squirrel on 2010-11-29
I just installed an M-Audio Audiophile 2496 card, which has been said to be supported under Ubuntu (10.04 here). 

System > Preferences > Sound correctly identifies the card as an ICE1712 (envy) card but only lists it as "1 output digital stereo duplex." I need to use its analog I/O connections. 

See attached screenshot "SoundPreferences1.png"

The "Profiles" dropdown does not list any analog options at all, only digital ones. 

I am feeding a 2v rms 1kHz sine wave into the analog inputs and the Input Level shows no signal, which makes sense if it's only looking for a digital signal. See attached screenshot "SoundPreferences2.png"

AlsaMixer . . . well, I don't know how to read what it says. See ALSAMIXER.png

So . . . how do I turn on the card's analog features?

---

### Post by Rocket J Squirrel on 2010-11-29
Okay, I'm getting frustrated. After having received recommendations here that this sound card works fine under Ubuntu, I've found that turning on the analog ins and outs is not at all easy. Studying all the comments at [https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/178442/?comments=all](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/178442/?comments=all) has led me to modifying all sorts of pulseaudio's files, but the best I can achieve is to turn on "multichannel" inputs and outputs, but no apparent way to map the only two (stereo) analog inputs successfully so that the level indicator in Sound Preferences sees the signal present at the input jacks. 

I know the card is capable of multichannel analog stuff, but all I want are to map the two (2) analog inputs to input level control that Sound Preferences shows, and to map your standard two (2) right and left outputs to the analog output connectors on the card.

---

### Post by cchhrriiss121212 on 2010-11-30
Could you try this:
[http://ubuntuforums.org/showpost.php?p=9317203&postcount=2](http://ubuntuforums.org/showpost.php?p=9317203&postcount=2)

---

