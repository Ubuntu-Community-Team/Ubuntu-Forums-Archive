---
title: "How to select the microphone?"
date: 2010-01-05
forum: Multimedia Software
---

### Post by Sunsawe on 2010-01-05
Hi,

I am running ubuntu 9.04 on a laptop. It is equiped with two embedded microphones and on input plug for an external one.

The issue for me is that I can not find the way to activate the external microphone.

In alsamixer, I can select two inputs, "mic" or "front mic", but it does not change anything, it is always the embedded ones wich are used. :confused:
How could I get the external one to be set by default? or even better to be given the choice in softwares like skype (as it is for the webcams)?

Thank you

---

### Post by Jenkins1 on 2010-01-05
If you go to the speaker in the top right (if you are running gnome) right click it and go preferences. Then go to the input tab and change the input "connector" to one that works.

---

### Post by Sunsawe on 2010-01-06
Thank you for the answer.
Following your instructions, right click -> preferences opens a window with a drop down box with 5 options:
HDA Intel (alsa mixer)
SigmaTel STAC9228 (oss mixer)
Playback: HDA Intel - STAC92xx Analog ( pulseaudio mixer)
Capture: Monitor of HDA Intel - STAC92xx ( pulseaudio mixer)
Capture: HDA Intel - STAC92xx ( pulseaudio mixer)

The last 3 only propose one option "Master" and I didn't find any "connector" in the others.

Can you be more specific?

---

### Post by mocoloco on 2010-01-06
The sound preferences have changed in 9.10 and I don't have 9.04 handy, but I believe there are options in the menus to show additional controls, actually tons of them, because I had to do it on my laptop to find the second headphone input volume slider.  I think there's a preferences pane or something.  Just enable them all and test to find out which it is, it might have a generic name like aux1 or something.

---

### Post by Jenkins1 on 2010-01-06
Sorry I some how missed reading you were running 9.04. I also don't have a copy available. if you install pavucontrol from synaptic it then appears under the Applications > sound & video > PulseAudio Volume Control. you get loads of options to change it. Look at the input tab and change the "port" drop down box. hope this helps more than before.

---

### Post by markbuntu on 2010-01-06
> **Sunsawe said:**
> Hi,

I am running ubuntu 9.04 on a laptop. It is equiped with two embedded microphones and on input plug for an external one.

The issue for me is that I can not find the way to activate the external microphone.

In alsamixer, I can select two inputs, "mic" or "front mic", but it does not change anything, it is always the embedded ones wich are used. :confused:
How could I get the external one to be set by default? or even better to be given the choice in softwares like skype (as it is for the webcams)?

Thank you

Mic switching is part of the alsa driver and getting it working can be problematic due to the zillion different hardware configurations that laptop manufacturers use. Some can be fixed and some cannot yet but people are working on it. If you go to this link you may be able to find a solution for your particular machine

[http://ubuntuforums.org/showthread.php?t=1043568](http://ubuntuforums.org/showthread.php?t=1043568)

---

### Post by mocoloco on 2010-01-06
I decided to fire up a 9.04 live CD to see if I'm crazy ;).  Turns out I'm not.  In the volume control there's a preferences button, and under that it will show the possible "tracks" as it calls them that you can control.  Enable them all and you can play with them to find the right one.

Get to the volume control by right-clicking the volume icon in the panel.

---

### Post by Sunsawe on 2010-01-09
Following your advises, I finally got it to work.
I activated all possible options in the sound config and a "Digital Input Source" option.
If I set it to "Analog Inputs" along with "Input Source" set at "Front Mic", it works!

Thank you all!

---

