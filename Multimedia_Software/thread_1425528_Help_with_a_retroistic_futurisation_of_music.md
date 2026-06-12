---
title: "Help with a retroistic futurisation of music"
date: 2010-03-09
forum: Multimedia Software
---

### Post by WeAmLegend on 2010-03-09
Hi,
 
What is the best way to setup Jack connections for a UA-1EX, just to get sound playing though it? Do I need any special drivers for the UA-1EX or Casio DG-20? Y'see I know nothing. :)
 
I'm new hear and have only just got into Ubuntu, so please understand my stoopidity and help it grow into knowledges. ;)
Also I apologise if this post is in the wrong place.
I've installed Ubuntu Studio onto my netbook (asus eeepc 1000 thing) so I can use it purely as a synthesizer of epic proportions. I have an Edirol UA-1EX USB sound card to use with it and a Casio DG-20 that I want to use as a midi input device.
What I want to do is be able to play the Ubuntu Studio synths using the DG-20, with the output coming from the UA-1EX, but all this talk of configuring Jack and various Ubuntu things isn't very easy for me to get my head around.
Currently I use Cubase SX 3, Ableton Live 8, Reason 3, VSTs etc... on my PC to produce music (for those interested there's some fun sounds here [http://www.myspace.com/betamaxisbest](http://www.myspace.com/betamaxisbest)), but I want to start doing something weird and electronic Live. So the DG-20 will be my playing surface and ubuntu studio my synth machine!
Just can't seem to get the DG-20 or UA-1EX working and need help or suggestions from you good people on what I need to do/where I'm going wrong.
The DG-20 is connected with a midi to USB cable, and eventually I'd like to have it operate in a multi midi channel stylee whereby each string plucked goes to a different synth or sound. But first I want to get it playing a synth, any synth!
 
Many thanks in advance
 
For We am Legends....

---

### Post by cchhrriiss121212 on 2010-03-09
Jack does not work without a few changes to a file called limits.conf which is in /etc/security/. Put this in a terminal:
```
sudo adduser <your username> audio 
```
then this ```
sudo gedit /etc/security/limits.conf
``` and paste the following text at the bottom:
@audio - rtprio 99
@audio - memlock unlimited
@audio - nice &#8722;10

Open jack from the applications>sound menu. In setup select the ua-1ex as the device, set intervals to 3 and leave the rest as it is. Press start and post any errors if it does not run.

It's possible that your dg-20 will not work well as a usb input, if so you will have better results with a sound card that has a built in midi connection. To see if it is recognized, open up patchage and look for it in a green box.

---

