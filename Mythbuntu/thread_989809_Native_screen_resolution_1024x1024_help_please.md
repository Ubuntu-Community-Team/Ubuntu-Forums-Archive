---
title: "Native screen resolution 1024x1024 help please"
date: 2008-11-22
forum: Mythbuntu
---

### Post by ebike on 2008-11-22
Hi All,

I have a Plasma screen with the above native resolution that I would like to make use of to it's full extent with Mythbuntu.

I have managed to set up a mode line that is accepted by the Plasma, but the aspect is all wrong and the fonts are not very readable. 

Does anyone know if I can set up my display size correctly in the latest Xorg with it's minimal xorg.conf file. (I obviously have non square pixels, which are a pain, which means a non symetrical DPI number ).

I would like to eventually run HD onto this panel and I would like to have the minimal amount of scaling happening .... i.e none in the TV, only in Myth.

Thanks,

---

### Post by ebike on 2008-11-22
... also, when I generated a modeline with "gtf", (i.e gtf 1024 1024 60 ) although it works with the display the screen is shifted to the right and down a bit. Can anyone tell me how to tweak the modeline values to center the image.

I have tried xvidtune but it doesn't seem to work, keeps reporting back that my monitor doesn't support the adjustment made.

Thanks.

---

### Post by ebike on 2008-11-24
Can nobody help me??

The latest I have tried is this:

Using the website -> [http://koala.ilog.fr/cgi-bin/nph-colas-modelines](http://koala.ilog.fr/cgi-bin/nph-colas-modelines)

I have come up with a resolution modeline that represents the aspect ration of my screen (16/11, measured the screen in millimeters ..)

That means the highest resolution for my max dotclock is 1272x874 at 85hz.
This actually presents quite a nice picture at a good aspect ratio (circles are round) and the fonts are shown great.

I guess this is the best I can do with this Plasma. it's just a shame that I am getting two lots of scaling happening, one in Mythtv and also in the TV.

---

### Post by Caps18 on 2008-11-24
That still sounds like a weird resolution.  What is the maximum resolution that you are supposed to get?  I've heard of 1920x1080 and 1368x768.  

I had a problem that my computer would set the resolution at 1280x820 instead of 1920x1080.  I couldn't fix it in Mythbuntu after it had loaded.  I determined the cause of it was from adding a splitter and Mythbuntu automatically detected the resolution from that instead of the TV, even though the splitter can handle 1920x1080.

---

