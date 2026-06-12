---
title: "Use MIDI master keyboard"
date: 2007-05-19
forum: Multimedia Production
---

### Post by higor on 2007-05-19
Hi,

I have bought a master keyboard midi and would want to be able to use it on linux. What programs I must to use and how i can configure it for simply being able to hear notes while I press the keys in the keyboard?

Thanks
Igor

---

### Post by stijngysemans on 2007-05-19
How do you connect your keyboard to your pc?

---

### Post by lyall on 2007-05-20
Try Mixxx
you can us 1/8" stereo plugs cable
If the midi has usb, use usb cable

good luck

---

### Post by ricrac on 2007-05-21
General midi overview, I'm looking for an up to date howto or I'll write up something when time permits.
Here's a good site for info..  [http://linuxrockstar.blogspot.com/](http://linuxrockstar.blogspot.com/)

This pertains to midi on linux.
Alsa supplies the midi "driver" for your soundcard.  Alsa needs to set up correctly for midi.
If you had a keyboard that produced sound, it would be easier. Once alsa is setup generally defaults will work (first midi device, midi channel 1) in sequencers like Rosegarden, Muse, etc.

Since your keyboard does not produce sound, you will need or want a softsynth to hear anything, (you could record and edit midi without sound) Timidity, Fluidsynth, Spiralsynth, many others.

Advanced sound requires a sound server to patch/route channels, usually this is jackd.

To review:
configure alsa - one time per card installed
configure jack - at least one time per card installed, but most people tweak this all the time
start softsynth(s) - not required if you have midi out and an external midi device, could be a single midi keyboard (that produces sound)
route alsa - once per session, sessions setups can be saved and reloaded
route jack - once per session, sessions setups can be saved and reloaded
route midi - once per session, sessions setups can be saved and reloaded, defaults may work
start sequencer

This LJ article (I've posted too many times) has a good overview, look for section Four4Fons 
[http://www.linuxjournal.com/node/1000224](http://www.linuxjournal.com/node/1000224)
He uses dosemu and sequencerGold but that could be replaced with Rosegarden or Muse and the setup remains the same.

Other music distros can get you a little closer faster for now, Ubuntu studio should hopefully catch up soon...

And if you think this looks daunting, realize that you end up with a much more powerful, lower latency, better synced midi system than is generally possible on windows/mac.
Many musicians will still prefer to use win/mac because of music application software and hardware driver availability and the effort involved in hardware config.

---

### Post by higor on 2007-05-21
Thanks for the suggestion, i will try soon. I have a mute midi keyboard with midi to game port cable. I think i need a softsynth. If i record something in rosegarden i see the note recorded but i don't hear any sound  neither when record neither when I play my tracks.

thanks

---

### Post by eric71 on 2007-05-22
Try searching for dssi in synaptic.  Install one of the dssi synth plugins listed. Xsynth would be a good start. Start jack (best done with Qjackctl), start rosegarden and select the  synth plugin istrument for a track. Now it should make sound.

---

### Post by kayosiii on 2007-05-24
The simplest thing would be something along the lines of zynsubaddfx....

You will need some sort of midi connection program to do this. If you already have jack set up and running patchage works really well. 

Otherwise you might try something like aconnect gui.

With patchage at least it is like physically wiring you need to connect your soundcards midi input to to the midi input of zynaddsubfx

That should be enough to hear a sound. another easy synth to set up is amsynth.

---

