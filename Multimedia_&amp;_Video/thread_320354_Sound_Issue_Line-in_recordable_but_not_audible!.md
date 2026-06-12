---
title: "Sound Issue: Line-in recordable but not audible!"
date: 2006-12-17
forum: Multimedia &amp; Video
---

### Post by Impermint on 2006-12-17
I'm confounded by what seems to be a simple problem; the audio input coming through my sound card line in jack from my radio tuner is not playing throught the speakers.

I can see that the line-in input is working because audacity can meter it and can record it but I can not hear the sound until I play the recording back.

If I check "software playthrough" in audacity prefrences then when I click record I can imediatly hear the line-in input but it is distorted and "echoy"

To those in the know: Please suggest a fix that will allow me to turn on my radio reciever,tape deck or any audio input and be able to hear it through the computer.

I have a Audigy 4 on an AMD64, I'm using dapper 6.06, ALSA seems to be in control of the sound and audacity was installed with automatix 2.

---

### Post by deadgobby on 2006-12-17
Have you tried Gnome ALSA Mixer and played with the settings? I use Audacity myself and had to play with the sound for a bit to hear the input. You distortion may be that you have mic input on instead of line in. The gain is to high from the device you are recording from. Like IE a 4 track. What is your sound card?

Gobby

---

### Post by Impermint on 2006-12-18
Problem solved  :) ; under device there is the option of my soundcard (Audigy 4) or a "SigmaTel STAC 9750,51 OSS Mixer".  I had tried playing with all the sliders and switch options for the Audigy 4, which was selected, with no difference but after changing the device to the SigmaTel and playing with those options when I switched back to the Audigy 4 the line-in started working.  Know idea why that worked but no worries, it works now! 

Thanks for your advice Deadgobby, I had all ready tried playing with the settings but not changing the device setting.

Does anyone know what the problem could have been, or what the SigmaTel* is* or does anyway?

---

### Post by Ongaku86 on 2008-02-01
SigmaTel is the junkiest integrated audio chipset EVER made....you cannot even get updated drivers off their website. They only make chips for pre-built computers like Dell. So, you just get ancient drivers from Dell´s website. 

I got an example on how bad it is...my friend bought a new XPS Dell system for his girlfriend. It was a crud computer IMO but it plays newer games well. He was playing Oblivion once on it with a 7950GT and the integrated audio LAGGED the game...anytime the music would switch over to the battle music, the game lagged so bad...like from 60FPS down to about 10FPS. We thought it might have been the graphics card being funny but it was the SigmaTel integrated audio...

....it does the same thing to me...it lags Zelda Ocarina of Time ffs! And it doesn´t even work in Ubuntu on my computer. I get two sound devices once is Intel 82801DB-ICH4 (Alsa mixer), which works beautifully (but still lags because my laptop is so old) and the other is my SigmaTel...and it doesn´t work at all...never bothered to try and fix it, I just warn people how crap this audio is...

---

