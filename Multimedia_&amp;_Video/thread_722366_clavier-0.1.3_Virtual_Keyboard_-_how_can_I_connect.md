---
title: "clavier-0.1.3 Virtual Keyboard - how can I connect it to Jack?"
date: 2008-03-12
forum: Multimedia &amp; Video
---

### Post by Boneless on 2008-03-12
Hi,

I downloaded and compiled clavier-0.1.3 ( [http://helgo.net/simon/clavier/](http://helgo.net/simon/clavier/) ) because the virtual keyboard in ZynAddSubFx is not very stable but tends to repeat notes during the same keypress (this doesn't happen with vkeybd, but as a virtual keyboard it's useless since it only has an octave mapped to the keyboard). The problem is that I try starting it up as explained in the README file:

```
clavier -o /dev/midi
```

but /dev/midi doesn't exist. After searching on the Web I figured out I should be using /dev/sequencer instead, but it doesn't work. Same for /dev/snd/seq . ZynAddSubFx is correctly configured (the OSS sequencer correctly matches the device I'm using) but it doesn't receive anything from clavier. Furthermore, using qjackctl, in the log window it shows "MIDI connection graph change" whenever I start clavier pointing its output to either /dev/sequencer or /dev/snd/seq, but in the "Connect" window, under the MIDI tab nothing shows up.

I've seen someone using clavier with a textfile and then configuring RTSynth for receiving MIDI input from this file... just to make myself clear:

```
clavier -o ~/midififo
rtsynth < ~/midififo
```

but I don't think ZynAddSubFx can receive MIDI info this way. Is there some way to point clavier (which I suppose uses OSS) to Jack?

---

