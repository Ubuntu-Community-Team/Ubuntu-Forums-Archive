---
title: "Record audio output"
date: 2007-05-30
forum: Multimedia &amp; Video
---

### Post by hammadr89 on 2007-05-30
Is there any program that I can use which will allow me to record whatever I'm listening to to a separate audio file? Or something that will allow me to record the audio in a video file to a separate audio file? I tried using sound recorder, but can't get it to work.

---

### Post by Sandsound on 2007-06-04
You can record in Ardour via Jack.

First you start Jack-ctl and Ardour, Ardour will ask you where to create your project.
In Ardour just create a new audiotrack, select it for recording hit record and play.

Simple as that :-)

---

### Post by hammadr89 on 2007-06-04
Alright, thanks

---

### Post by Sandsound on 2007-06-04
You're welcome :-)

---

### Post by PRAEst76 on 2007-06-11
> **Sandsound said:**
> You can record in Ardour via Jack.

First you start Jack-ctl and Ardour, Ardour will ask you where to create your project.
In Ardour just create a new audiotrack, select it for recording hit record and play.

Simple as that :-)

Ardour complains about having no input connections, it also seems a bit overkill for the requirement. Is there no way to do this with audacity or a basic sound recorder?

---

### Post by Sandsound on 2007-06-11
> **PRAEst76 said:**
> Ardour complains about having no input connections, it also seems a bit overkill for the requirement. Is there no way to do this with audacity or a basic sound recorder?

I guess you can use ReZound or something, dont know about Audacity thou... I have never used it, but I don't think it has jack-support ?

I have'nt been able to provoke the error you get from Ardour. what soundcard do you use, and does your Jack run as it should ?

---

### Post by hammadr89 on 2007-06-12
Well, I figured out how to do it using the sound recorder that comes built in. You use the capture option from the sources box, and once you're done recording, you need to click "save as" and save the file as a .mp3 or .ogg or whatever. It doesn't do that directly with "save". That was my problem I guess. If It helps anyone....

---

### Post by gsoundsgood on 2008-05-05
unfortunately this is not working for me in ubuntu 8.04...actually, the standard sound recorder that comes with ubuntu hardly works...on my laptop, it cannot even reproduce what it records...does anyone have an easy solution?

---

