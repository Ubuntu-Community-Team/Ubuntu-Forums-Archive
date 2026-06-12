---
title: "Gateway Laptop Intel 8280 chipset no sound"
date: 2006-01-07
forum: Multimedia &amp; Video
---

### Post by racin on 2006-01-07
Hi Guys,
Well the wireless is fixed so now on to the sound issue. I have followed the sound problem wiki and I still don't have any sound. Both playback and recording have been set to alsa. PC speaker is activated and sound is turned all the way up. What should I check next? This is on a gateway laptop with on board sound, pentium 4 with the intel 8280 chipset.
Thanks for any help in advance!

---

### Post by stratotak on 2006-01-07
im assuming that the fact you read wiki  sound ..you have correct modules for sound loading..tha you have choosen alsa as sound preferences under prefernce??when you click to test dose it work??if all that seems to check out then i would move on to the mixer part..possibly something is muted or turned down low..like pcm sound..i use gnome-aslasmixer to adjust my sound card settings..have you tried that??

---

### Post by racin on 2006-01-07
Yes preferences are correct. They are both set to alsa. In mixer  there is a IEC958 P that will not close. I'm thinking this is where the problem lies but I don't know how to force it closed. Thanks for the help.

---

### Post by racin on 2006-01-07
When I test the alsa preference settings I don't hear any sound.

---

### Post by racin on 2006-01-08
Sweet!! It's fixed! Although the actions to fix it are very bizzarre. I went through the sound problem tutorials and did just about everything in them. Still no sound. Then I read stratotak's reply above and thought I would give it one more look! Thanks for your time stratotak! So in alsamixer prefs I turned on external amp for whatever reason I don't know but I did that anyhow. I then backed out to the mixer control settings and using keyboard m turned off the external amp and when I did the computer made noise! It scared me I was like huh??? What the?? And then I figured it out! Holy Cow I got sound! Yahoo!:razz:

---

### Post by pakux on 2006-01-08
YYYYYYYEEEEEEEEESSSSSSSSSS !!!!!!!!   :cool: 

wow, it took a lot but finally you show me the way... thanks a lot, i've tried everything but the "external amp" tip was the winner (by the way, did anybody figure out why is this active by default?)

again, thank you all very much.

---

### Post by racin on 2006-01-09
Wow! That is crazy wierd that the same procedure worked for you! I thought the external amp thing was a fluke! Oh well glad I was able to help! Enjoy your new found sound!:eek:

---

