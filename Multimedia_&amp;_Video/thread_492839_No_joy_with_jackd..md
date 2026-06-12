---
title: "No joy with jackd."
date: 2007-07-05
forum: Multimedia &amp; Video
---

### Post by davemar on 2007-07-05
I am trying to set up things with jackd, rosegarden and fluidsynth, but hitting a brickwall. I'm trying to start off by getting jackd to work properly.

So far I've installed the realtime kernel (7.04), and set up a username under the audio group which I also setup.

I use qjackctl to start jackd and have set the realtime setting. I've tried various different frames sizes, but none seem to work. Currently I'm trying to play out from audacity through jackd (as I know audacity produces sound direct to the soundcard on its own OK, and should be a simple starting point for jackd). All I get from jackd is lots of "delay of XXXX usecs exceeds estimated spare time of YYYY; restart" errors cycling past and no sound. No matter what settings I use on qjackctl along with the realtime flag set I get these errors. If I turn off realtime in jack I don't get these errors, but no sound either. I've set jack into playback only mode thinking that this will reduce the processing it requires (as I'm not inputting sound to the soundcard) so making things easier. Are there any other setting I really ought to deal with?

As for getting fluidsynth (using qsynth) and rosegarden working with jackd... that's a distant dream at the moment. I've even tried pmidi->qsynth->qjackctl without a success. I've managed to get sound out of pmidi->qsynth (using alsa to go to the soundcard) without to much trouble (still needs a largish framesize in qsynth) albeit a bit choppy. I assume jackd needs to be pointed to pmidi somehow though it doesn't show in the connections part, but qsynth is.

I'm getting really frustrated with all this, I can't believe getting sound + MIDI can be that hard.

---

### Post by eivind on 2007-07-05
Hm. As far as I know, it shouldn't be neccessary to set up a special audio user or group in order to use jackd. Sorry if I seem patronizing in the following paragraphs, but I don't know what you've already tried. 

OK. Here goes. Assuming that you are trying to run jackd as a normal user:

1. Are you sure your soundcard is detected properly by jackd? You should be able to see this quite clearly in the jackd setup (I am referring to qjackctl). Under Setup, look where it says "Interface". I have an internal soundcard and an external USB one, they show up as hw:0 and hw:1 respectively. Clicking the arrow next to the drop-down list, you should be able to see a bit more info on each detected soundcard.

2. And by the way, which soundcard are you using? Knowing what hardware causes problems would be a good start in resolving them.

All the best,

Eivind

---

### Post by davemar on 2007-07-06
Thanks for answering Eivind. You're not being patronizing at all, it's always good to ask the obvious questions first. To answer:

1. The interface option is set to hw:0 and when I click the ">" symbol it displays "hw:0  C-Media PCI CMI8738-MC6" which is the selected option. There are also three other options here, "hw:0,0", "hw:0,1", "hw:0,2" with different C-Media settings (DAC/ADC, etc.).

2. It appears the chipset for this soundcard is the C-Media PCI CMI8738-MC6 I assume! It's a Trust 5.1 channel PCI soundcard. Not sure of it's exact name without opening up the PC.

It seems fine producing sound with audacity alone, or with Rhythmbox.

---

