---
title: "fluidsynth not making any sound"
date: 2011-06-26
forum: Multimedia Software
---

### Post by limescout on 2011-06-26
Hello all!  I'm trying to get my midi controller keyboard to play through fluidsynth for live sound.  My ultimate goal is to be able to do this, as well as sending midi data to MuseScore, and have MuseScore send midi data to fluidsynth so I can hear what I'm writing.  Everything is routed using JACK, per Ubuntu documentation online.
     Here is my problem.  I have my keyboard routed to fluidsynth fine (the midi data light in qsynth blinks when I play notes), but fluidsynth isn't producing any sound.  The audio section of my jack connections kit looks like this:

Output           Input
qsynth----\
                 |----system
system---/

(qsynth and system are connected to system)

I am fairly new to Ubuntu's midi functionality, does anyone know what I should do?

---

### Post by BicyclerBoy on 2011-06-26
sound fonts package ?

fluidsynth does not make any midi sounds without sound fonts package, it only makes synthesised pure notes/tones.

Can not comment on the wiring as my helper figured that out..

---

### Post by cchhrriiss121212 on 2011-06-26
Yes, you need to load a soundfont with qsynth. To do so, click "setup" then load your sf2 file under the "soundfonts" tab, give each one a separate offset value so the sounds will appear in separate sound banks. 
Then open the "channels" window and double click on a channel to select your sound. 

If you don't have any soundfonts, squidfont is a good orchestra selection which you should find via google.

As for wiring, I would recommend you use a program called patchage (you will find it in software centre). It does the same job as qjackctl connect window, but is is easier to work with: the blue boxes are audio and the green boxes are MIDI.

---

### Post by BicyclerBoy on 2011-06-26
A basic soundfonts package is in the ubuntu repositories..
A fact I only discovered after the painful process of converting from some windows files..

---

### Post by limescout on 2011-06-27
Ok, I installed patchage (which does look a lot clearer, I must say).  Using patchage, I realized the problem.  qsynth is sending its output to the on-board sound chip, not to the PCI sound card i have installed.  I switched the speaker cables from the sound card's outputs to the motherboard's outputs, and, sure enough, I got sound from qsynth.

This is strange, because all of my other sound comes out of the sound card like its supposed to.  In patchage, there are no other system outputs, only the on-board stuff.  Is there any way to get patchage or qsynth to recognize my sound card?

---

### Post by cchhrriiss121212 on 2011-06-28
Patchage will display the devices defined by jack, which will only use one device at a time. By default, jack will use the first device listed by ALSA, which in most cases, is the motherboard audio chipset.

What you need to do is open qjackctl and in the "setup" window, select your PCI card as the "interface".

---

### Post by limescout on 2011-06-30
Cool!  Now I can get sound from my preferred sound card with fluidsynth, thank you very much.

---

