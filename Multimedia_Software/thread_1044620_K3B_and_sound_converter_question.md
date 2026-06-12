---
title: "K3B and sound converter question"
date: 2009-01-19
forum: Multimedia Software
---

### Post by ghostofzuul on 2009-01-19
Hi. New to ubuntu.

Got the "sound converter" package (the one with the c not the k) to convert mp3 to .wav and then tried to upload those .wav files to K3B for burning. K3B didn't recognize the files as "true" .wav files and subsequently they wouldn't burn.

I've read about this issue in other forums that it's hard to convert to true .wav files that K3B will recognize. Anyone know of a (the) program to use successfully? 

K3B copies great but to have to convert everything first either to .wav or mp4 (for vcd's) is kind of a pain in the butt.

thanks!

---

### Post by logos34 on 2009-01-19
all you have to do is click 'create audio cd' in K3b and select/drag in the mp3s you want to burn--it'll convert them for you

---

### Post by ghostofzuul on 2009-01-19
> **logos34 said:**
> all you have to do is click 'create audio cd' in K3b and select/drag in the mp3s you want to burn--it'll convert them for you

when i add mp3's or even .wav files converted using sound converter i get this error msg:

Unable to handle the following files due to an unsupported format:
You may manually convert these audio files to wave using another application supporting the audio format and then add the wave files to the K3b project.

---

### Post by logos34 on 2009-01-19
not sure about the .wav errors (which may be related to a gstreamer bug I've heard about in 8.10, iirc), but as far as mp3 goes, do you have the k3b suggested pkgs installed?  you need the mp3 plugin

sudo apt-get install libk3b2-extracodecs

---

### Post by ghostofzuul on 2009-01-20
> **logos34 said:**
> not sure about the .wav errors (which may be related to a gstreamer bug I've heard about in 8.10, iirc), but as far as mp3 goes, do you have the k3b suggested pkgs installed?  you need the mp3 plugin

sudo apt-get install libk3b2-extracodecs

installed and i'm going to give it a run through....

also... for those of us who are command line challenged such as myself you can also access the codecs by going to 

system>synaptic pakage manager>(scroll down to)libk3b2-extracodecs

which is what i did...

thanks!

---

### Post by zohar995 on 2009-02-21
Thanks It helped me as well.:KS

---

