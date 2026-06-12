---
title: "Speed Link Medusa 5.1 USB headset Driver problems"
date: 2006-07-02
forum: Multimedia &amp; Video
---

### Post by Gorlist on 2006-07-02
Hi, recently moved from Windows over to Ubuntu and though generally its gone very well im having issues with my Speed Link Medusa 5.1 USB headset.

I do have sound, and limited mic input but the drivers seem at best confused at best.

The microphone even turned to full with Gain has allot of background noise (Their is no Mic Boost option either, only Gain) and very poor input level - and for some reason the level is being controlled by the Speaker volume buttons on the headset hand device?

Im also finding I have to activate Speaker 2 to have any control on the headset volume through Ubuntu.

Played around with some of the settings, and a person on the IRC had ago at figuring it out but unfortunately couldn't resolve the problem.

I really do need this working... :(

Anyideas? 

Regards!

---

### Post by xrchris on 2006-07-02
I have this exact same headset but have yet to get them to work at all - where did you find the drivers etc?

---

### Post by Gorlist on 2006-07-02
[QUOTE=xrchris]I have this exact same headset but have yet to get them to work at all - where did you find the drivers etc?[/QUOTE]

Ubuntu automatically selected some drivers to use I assume? I get sound but not much else :( Just hope something can be done as its a very good headset.

---

### Post by Gorlist on 2006-07-05
Anyideas?

---

### Post by Advanced on 2007-02-24
hey guys! I had the exact same problem! im running edgy eft..

I found that (if the "USB Audio" is auto detected) yet you still can get anything through them, you need to try using the OSS Output plugin on Beep Media player, that should set you off with some music to listen to, sounds good too :) hope this helps! 

im still experimenting so i will add more when i know more

[edit] From what i can see, the inbuilt drivers in edgy work fine apart from the fact that your volume control is "Speaker 1" instead of "Speaker".. 

I think this is effecting other programs like firefox.. i THINK firefox is trying to output to "speaker" instead of "Speaker 1"

lawd knows.. ah well, i can listen to my music for now :)

---

### Post by Gorlist on 2007-02-24
What I have done is downloaded the ASLA?? Config panel so it allowed me to setup/disable some the channels through a GUI whilst testing. The mic is working fine now, though only two speakers :)

---

### Post by maiageorge on 2007-03-20
> **Gorlist said:**
> What I have done is downloaded the ASLA?? Config panel so it allowed me to setup/disable some the channels through a GUI whilst testing. The mic is working fine now, though only two speakers :)

That sounds great, but does anyone know how it all works? I installed a couple of those alsa congif panels and have no clue how tu use them! Does anyone?

---

### Post by Gorlist on 2007-03-20
Trial and error to some degree :| I set my mic on record and then played with the channels whilst speaking to see if I was getting  input, and the same for speaker output.

Later on if I remember will post a screen shot of the GUI..

It seems strange no one has atleast done a small config for 5.1 USB headphones... 

Regards!

---

### Post by maiageorge on 2007-03-21
So... I found out that the sound chip of the medusa speakers thing is this one: CM-106-Chip

So now my request is: Help! Can anyone help me with this information?

---

### Post by Gorlist on 2008-06-30
Has anyone had any further luck with 5.1 USB headphones? threads getting somewhat old but the problem still remains. And/Or no generic driver available?

---

