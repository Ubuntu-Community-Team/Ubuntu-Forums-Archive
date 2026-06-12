---
title: "MIDI program change"
date: 2008-04-17
forum: Multimedia Production
---

### Post by PCChris on 2008-04-17
What is the easiest way (if any) to map different programs on my MIDI keyboard to different soft synths?  I am using ALSA & JACK under Ubunto Studio-Gutsy on a laptop with dual core AMD 64 processor.  Thanks in advance!

---

### Post by sanus|art on 2008-04-18
[http://64studio.com/howto_vst](http://64studio.com/howto_vst)

---

### Post by PCChris on 2008-04-18
Unless I'm not seeing something, I'm afraid this is not what I am looking for.  To clarify the problem:  I have a MIDI keyboard connected to the computer, and this shows up fine in Jack.  However, I want to be able to change the program on the keyboard in order to change the soft synth on the computer that the keyboard is controlling.  i.e. Program 1 on keyboard goes to ZynAddSubFX, Program 2 goes to qSynth, etc.  I thought there may have been a way to set this up through Rosegarden though I'm not sure.  Thanks again.

---

### Post by sanus|art on 2008-04-18
Sorry, by reading "soft synths" i assumed  you're talking about VST. As far as I know - rosegarden is able to configure any plugged midi controller through jack=>ALSA by CC messages.
I might be wrong though... 
Also I have no ubuntu-studio packages installed right now, but I'm pretty sure that there was midi patcher/mapper of some kind among the installed programs.

---

### Post by Stochastic on 2008-04-18
I'm not a real MIDI head so there may be a more elegant way of doing this, but I think that you could get this done in PureData (though I'm not 100% sure you can get multiple MIDI output channels).  A switcher would be quite easy to program (provided you can get patchage or qjackctl to see multiple MIDI outputs from PD?), simply take a midiin object, send the program data to a router switch as the controlling number, send the midiin data to the input of the router switch, and the corresponding outs of the switch should be set to various midiout objects.  Then go into patchage (probably better as you'll be able to save your config) and route your midi signals to the wanted apps.

---

### Post by PCChris on 2008-04-18
Thank you, the help is greatly appreciated!  Now all I need to do is figure out how to use PureData (I'll also need to make sure PD works when I get home-Csound may have been the only thing I ran into problems with trying to run).

---

