---
title: "Turn off mic boost in Ubuntu"
date: 2011-09-27
forum: Multimedia Software
---

### Post by siddharthshetty on 2011-09-27
I make ubuntu tutorials but the quality of the audio is always bad.
There is always some amount of noise which my microphone pics up.

Btw you can see the tutorials that i make on [http://www.youtube.com/sidhartRON](http://www.youtube.com/sidhartRON)
you can see what i mean about the audio.

I am currently running ubuntu 11.04 and 

YES I HAVE TRIED REDUCING MIC BOOST TO 0 IN ALSAMIXER
but that makes the input volume to 0 aswell . so alsamixer and pavucontrol both don't look like they work. I always believed that it was the microphone's problem . Until i installed win 7 on the same computer and i got a new microphone. so win 7 has the option of turning of the mic boost but to keep the mic volume at 100%
which gives amazing clarity and voice quality.
My microphone is inbuilt on my headphone and connected to my computer via a 3.5mm jack.

when i use a separate microphone to do my vlogs . i get very good quality in win 7 but i ubuntu i just can't record videos.
I wan't to prove to the world that good quality videos can be made on linux. but i can't do that without good audio.

btw i make vlogs on [http://wwww.youtube.com/siddharthsvlogs](http://wwww.youtube.com/siddharthsvlogs)
and 

i record video through my webcam which gives an awful framerate in win7 But ubuntu gives me amazing video clarity and framerate.
Please help me here.

---

### Post by lidex on 2011-09-27
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.

---

